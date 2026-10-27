# 30분짜리 pstack 실습

> **주의: 이 문서는 AI 도구에 의해 만들어졌습니다. 저 Spike (Edward) Jee가 일부 섹션들은 검토하고 교정하였지만 전혀 proofreading되지 않은 부분도 많습니다.**

이 30분짜리 코드랩(code lab)에서는 pstack을 활용하는 방법을 익힐 수 있습니다. 여기에서는 작은 예제 프로그램인 “릴리스 선택 도구”를 디버깅하고 개선하고 검토하는 과정을 통해, pstack을 사용하는 기본적인 워크플로(workflow)들을 익힙니다.

우리는 예제 프로그램의 동작과 개발 이력을 살펴보고, 테스트로 오류를 재현하여 수정한 뒤, beta 채널을 선택하는 기능을 추가할 것입니다. 이어서 여러 에이전트에게 코드 검토와 실행 검증을 맡기고 그 결과를 확인할 것입니다.

pstack은, Claude Code나 Codex와 같은 소프트웨어 개발용 AI 에이전트를 위한 플러그인입니다. Cursor AI의 소프트웨어 엔지니어 Lauren Tan이 만들었습니다. pstack은 소프트웨어 엔지니어들에게 유용한 작업들을 수행하는 방법들을 정리한 스킬(skill)들을 제공합니다. pstack의 `/poteto-mode`는 사용자의 요청에 맞는 진행 절차(playbook)를 선택하고 필요한 스킬들을 연결합니다.

이 문서는 2026년 10월 27일에 공식 `cursor/plugins` 저장소에 있는 pstack 0.15.34를 기준으로 작성되었습니다.

## 1. 실습 소요 시간

전체 실습의 예상 소요 시간은 약 30분입니다. Cursor 및 기본적인 개발 도구들이 이미 설치되었다고 가정한 예상 시간들입니다. 다만 모델의 응답 시간에 따라 더 오래 걸릴 수 있습니다.

| 절 | 경과 시간 | 실습 내용 | 주요 기능 |
| --- | --- | --- | --- |
| 3절 | 0~2분 | 예제 코드와 Git 이력 생성 | 실습 환경 구성 |
| 4절 | 2~5분 | pstack 설치와 초기 설정 | `/setup-pstack` |
| 5절 | 5~8분 | 코드와 변경 이력 조사 | `/poteto-mode`, `how`, `why` |
| 6절 | 8~14분 | 오류 재현과 수정 | 테스트 주도 개발(TDD) |
| 7절 | 14~20분 | 설계안 비교와 기능 추가 | `/architect`, `/arena` |
| 8절 | 20~23분 | 여러 모델을 이용한 코드 검토 | `/interrogate` |
| 9절 | 23~27분 | 검증 항목을 나누어 병렬 실행 | `/swarm` |
| 10절 | 27~30분 | 문서 정리와 판단 기록 확인 | `/unslop`, `/show-me-your-work` |

우리는 실제 소프트웨어 개발 시 수행하는 주요 작업들을 직접 실습해 볼 것입니다. 하지만 PR 감시, 장시간 자율 실행, 성능 분석, 형식 검증 등은 11절에서 간단히 소개하기만 할 것입니다. 전체 58개 스킬의 실행이나 실제 PR의 생성부터 병합까지는 실습 범위에 포함하지 않습니다. ‘문제 해결’ 절은 진행 중 문제가 생겼을 때 참고할 수 있는 안내입니다.

## 2. 먼저 준비할 것들

다음 환경을 준비합니다.

- **Cursor**: 설치와 로그인을 마치고 Agent 기능을 사용할 수 있어야 합니다. 병렬 실행 실습에는 로컬 하위 에이전트(subagent)를 지원하는 환경이 필요합니다.
- **기본 개발 도구**: Git 2.28 이상, Python 3.10 이상, Bash를 사용합니다.
- **운영체제**: macOS, Linux, Windows의 WSL 환경에서 진행할 수 있습니다. Windows에서는 WSL에 연결된 Cursor 창을 사용합니다.
- **모델 접근 권한**: 서로 다른 계열의 모델 두 종류를 사용할 수 있으면 모델 간 검토 결과를 비교할 수 있습니다. 한 종류만 사용할 수 있는 경우에도 독립된 에이전트의 병렬 실행은 체험할 수 있으나, 서로 다른 모델을 이용한 검토와는 구분해야 합니다.

예제는 Python 표준 라이브러리만 사용하므로 별도 Python 패키지를 설치할 필요가 없습니다. GitHub 계정을 연결하거나 원격 저장소를 만들 필요도 없습니다. 여러 에이전트를 호출하므로 단일 에이전트로 작업할 때보다 모델 사용량이 늘어납니다.

이 문서에서 `bash`로 표시한 코드 블록은 터미널에 입력합니다. `text`로 표시한 슬래시 명령과 프롬프트는 Cursor의 Agent 채팅에 입력합니다. 스킬을 실행할 때는 `/` 메뉴에서 해당 이름을 선택한 뒤 나머지 프롬프트를 붙여 넣습니다.

pstack의 초기 설정을 마친 뒤에는 새 Agent 채팅을 엽니다. 이후 실습은 그 채팅에서 순서대로 진행합니다.

## 3. 예제 코드 만들어 넣기 (0~2분)

빈 작업 디렉터리에서 터미널을 열고 다음 명령 전체를 실행합니다. 명령을 실행하면 `pstack-lab` 디렉터리에 프로그램, 테스트, 동작 명세가 생성되고 실습용 Git 이력이 추가됩니다. 같은 이름의 디렉터리가 이미 있으면 기존 파일을 덮어쓰지 않고 중단합니다.

```bash
bash <<'BASH' && cd pstack-lab
#!/usr/bin/env bash
set -euo pipefail
python3 - <<'PY'
from pathlib import Path
import subprocess

root = Path('pstack-lab')
root.mkdir()  # Refuse to overwrite an existing lab.
files = {
    'release_picker.py': '''import argparse

RELEASES = [
    {"version": "1.9.0", "channel": "stable"},
    {"version": "2.0.0", "channel": "beta"},
]

def choose_release(releases, current):
    candidates = [r for r in releases
                  if r["channel"] == "stable" and r["version"] > current]
    return max(candidates, key=lambda r: r["version"], default=None)

def main():
    parser = argparse.ArgumentParser()
    parser.add_argument("--current", default="1.8.0")
    args = parser.parse_args()
    release = choose_release(RELEASES, args.current)
    print(release["version"] if release else "NO_UPDATE")

if __name__ == "__main__":
    main()
''',
    'test_release_picker.py': '''import unittest
from release_picker import choose_release

class PickerTests(unittest.TestCase):
    def test_empty(self):
        self.assertIsNone(choose_release([], "1.0.0"))

    def test_equal_version_is_not_an_update(self):
        releases = [{"version": "1.0.0", "channel": "stable"}]
        self.assertIsNone(choose_release(releases, "1.0.0"))

    def test_stable_only(self):
        releases = [{"version": "1.2.0", "channel": "stable"},
                    {"version": "2.0.0", "channel": "beta"}]
        self.assertEqual(choose_release(releases, "1.0.0")["version"], "1.2.0")
''',
    'SPEC.md': '''# Release selector contract
- Versions are valid major.minor.patch triples of nonnegative integers.
- Components have no leading zeroes except the number 0 itself.
- Compare components numerically, from left to right.
- Select the highest stable release strictly newer than current.
- Return the original release dictionary, or None if no update exists.
- Do not mutate the input. Input order must not affect the selected version.
- CLI prints the version or NO_UPDATE, followed by a newline.
- Invalid input, full SemVer, networking and installation are out of scope.
''',
    'README.md': '''# Release picker
This cutting-edge selector seamlessly orchestrates next-generation updates.
It empowers users to unlock a revolutionary release-selection journey.
''',
    '.gitignore': '__pycache__/\n*.pyc\ndecisions.tsv\n.audit/\n',
}
for name, content in files.items():
    (root / name).write_text(content, encoding='utf-8')

def git(*args):
    subprocess.run(['git', *args], cwd=root, check=True)

git('init', '-b', 'main')
git('config', 'user.name', 'Codelab')
git('config', 'user.email', 'codelab@example.invalid')
git('config', 'commit.gpgsign', 'false')
git('add', '.')
git('commit', '-m', 'feat: ship stable first; beta is reserved for internal testing')
p = root / 'release_picker.py'
p.write_text(p.read_text().replace(
    '    {"version": "1.9.0", "channel": "stable"},',
    '    {"version": "1.9.0", "channel": "stable"},\n'
    '    {"version": "1.10.0", "channel": "stable"},'), encoding='utf-8')
git('add', 'release_picker.py')
git('commit', '-m', 'data: publish stable 1.10.0')
git('tag', 'lab-start')
print('\nCreated:', root.resolve())
PY
cd pstack-lab
python3 -m unittest -v
python3 release_picker.py
BASH
```

생성이 끝나면 기존 테스트 3개가 모두 통과하고, 프로그램은 `1.9.0`을 출력합니다. 그러나 릴리스 목록에는 stable 채널의 `1.10.0`도 있으므로 올바른 선택은 `1.10.0`입니다. 현재 테스트가 이 오류를 검출하지 못하는 상태에서 실습을 시작합니다.

`release_picker.py`는 릴리스를 선택하는 프로그램이고, `test_release_picker.py`는 테스트입니다. `SPEC.md`에는 다음 동작 규칙이 정리되어 있습니다.

- 버전은 `1.10.0`처럼 음이 아닌 정수 세 개로 구성됩니다. 각 숫자는 `0` 자체를 제외하면 앞에 `0`을 붙이지 않습니다. 버전의 크기는 각 숫자를 왼쪽부터 차례로 비교하여 결정합니다.
- 기본 동작은 현재 버전보다 높은 stable 릴리스 가운데 가장 높은 버전을 선택하는 것입니다. 함수는 선택한 릴리스의 원래 딕셔너리를 반환하며, 해당 릴리스가 없으면 `None`을 반환합니다.
- 입력 목록을 변경해서는 안 되며, 목록의 순서가 달라도 선택되는 버전은 같아야 합니다.
- 명령행 인터페이스(CLI)는 선택한 버전을 출력합니다. 업데이트할 버전이 없으면 `NO_UPDATE`를 출력합니다.

전체 SemVer 규칙, 잘못된 입력의 처리, 네트워크 통신, 실제 업데이트 설치는 이 실습에서 다루지 않습니다.

## 4. pstack을 설치하고 초기 설정하기 (2~5분)

생성된 `pstack-lab` 디렉터리를 Cursor에서 엽니다. Agent 채팅에 다음 명령을 하나씩 입력하여 플러그인을 설치하고 초기 설정을 시작합니다.

```text
/add-plugin pstack
```

```text
/setup-pstack
```

설정 과정에서 질문이 나오면 다음 기준으로 선택합니다.

| 설정 항목 | 선택 기준 |
| --- | --- |
| 추론 예산 | `small — medium reasoning`을 선택합니다. |
| `architect runners`, `arena runners`, `interrogate reviewers` | 각 목록에 사용 가능한 모델을 두 개씩 지정합니다. 가능하면 서로 다른 계열의 모델을 선택합니다. |
| 나머지 역할 | 사용 가능한 빠른 모델이나 `inherit-parent`를 선택합니다. `inherit-parent`는 현재 채팅의 모델을 그대로 사용한다는 뜻입니다. |
| 검증 스킬 또는 형식 검증 스킬 생성 제안 | 이번 실습에서는 건너뜁니다. 예제에 이미 실행 가능한 CLI와 테스트가 준비되어 있습니다. |

모델 이름은 설정 과정에서 실제로 사용할 수 있다고 확인된 것만 지정합니다. `/setup-pstack`의 설정은 사용자 수준에 저장되며 새 채팅부터 적용됩니다. 설정을 마치면 새 Agent 채팅을 열어 다음 절을 진행합니다. [공식 모델 설정](https://github.com/cursor/plugins/blob/main/pstack/skills/setup-pstack/SKILL.md)

## 5. 코드와 변경 이력 살펴보기 (5~8분)

먼저 프로그램의 현재 동작과 개발 배경을 조사합니다. 다음 프롬프트를 입력합니다. 프롬프트에 포함된 공통 조건은 이후 실습에도 적용됩니다.

```text
/poteto-mode new task. 이 릴리스 선택 프로그램을 읽기 전용으로 조사해 주십시오.
CLI 입력에서 choose_release 함수와 출력으로 이어지는 흐름을 파일명과 행 번호로 설명하고,
stable 채널만 기본으로 허용한 이유를 Git 이력에서 찾아 주십시오.
확인된 사실과 추측을 구분하고, 현재의 잘못된 동작을 직접 실행하여 확인해 주십시오.
이 단계에서는 파일을 수정하지 마십시오.

실습 전체에 다음 조건을 적용해 주십시오.
- Python 표준 라이브러리만 사용합니다.
- 외부 자료나 MCP 서비스를 조회하지 않고 이 저장소와 Git 이력만 조사합니다.
- 로컬 커밋은 허용하지만 원격 저장소 생성, push, PR 생성, merge는 수행하지 않습니다.
- 최종 구현은 현재 열려 있는 작업 트리에 반영합니다.
- 조사와 설계에는 로컬 하위 에이전트를 사용하고, 각 설계안은 별도 임시 디렉터리에 작성합니다.
- 설치되지 않은 보조 스킬은 생략한 이유를 밝히고, 사용 가능한 Python 명령으로 검증합니다.
- 답변은 한국어로 간결하게 작성하되, 실제 실행한 명령과 결과를 제시합니다.
```

결과에서 다음 내용을 확인합니다.

1. 조사 절차에 해당하는 작업 목록이 작성되었는지 확인합니다.
2. `how`와 `why`를 통해 코드의 동작과 개발 배경에 관한 근거가 제시되었는지 확인합니다.
3. stable 채널을 우선 지원한다는 설명이 첫 번째 커밋 메시지로 뒷받침되는지 확인합니다. 이 Git 이력은 실습을 위해 만든 가상 프로젝트의 이력입니다.

`how`는 현재 코드가 어떻게 동작하는지 조사하고, `why`는 그러한 구조나 동작을 선택한 배경을 조사합니다. 이 실습에서는 배경을 조사할 자료를 Git 이력으로 한정합니다. 조사 결과를 확인한 뒤 오류 수정 단계로 넘어갑니다. [공식 why](https://github.com/cursor/plugins/blob/main/pstack/skills/why/SKILL.md)

## 6. 실패하는 테스트로 버그 고쳐 보기 (8~14분)

이제 잘못된 버전 선택을 테스트로 재현하고 수정합니다. 테스트 주도 개발(TDD)에서는 올바른 동작을 요구하는 테스트를 먼저 작성하고, 기존 코드에서 그 테스트가 실패하는지 확인한 뒤 구현을 고칩니다. 다음 프롬프트를 입력합니다.

```text
/poteto-mode new task. 기본 CLI가 stable 1.10.0 대신 1.9.0을 선택합니다.
SPEC.md의 동작 규칙에 맞게 테스트 주도 개발(TDD)로 수정해 주십시오.
먼저 오류를 재현하는 회귀 테스트를 추가하고, 기존 코드에서 실패하는지 확인한 뒤 수정해 주십시오.
현재 버전이 1.8.0 또는 1.9.0이면 1.10.0을 선택해야 하며,
현재 버전이 1.10.0이면 업데이트할 버전이 없어야 합니다.
외부 패키지를 추가하지 말고 기존 API를 유지해 주십시오.
실패하는 테스트의 추가와 구현 수정은 순서를 확인할 수 있도록 별도 로컬 커밋으로 남겨 주십시오.
수정 후 원래 CLI를 다시 실행하고, 수정 전후의 테스트 명령과 실제 출력을 보여 주십시오.
```

오류의 원인은 문자열 비교입니다. 문자열의 사전식 순서에서는 `1.9.0`이 `1.10.0`보다 뒤에 위치합니다. 버전을 올바르게 비교하려면 각 문자열을 정수 세 개로 해석하여 비교해야 합니다. 가장 높은 버전을 선택하는 부분과 현재 버전보다 높은지 판단하는 부분에 동일한 비교 기준을 적용해야 합니다.

추가한 테스트가 **버전 선택 오류 때문에 실패했는지** 확인합니다. 모듈을 가져오는 과정이나 파일 경로의 오류 때문에 실패했다면 원하는 오류를 재현한 것으로 볼 수 없습니다. 구현을 수정한 뒤에는 다음 명령으로 결과를 확인합니다.

```bash
python3 -m unittest -v
python3 release_picker.py
python3 release_picker.py --current 1.10.0
```

전체 테스트는 통과해야 합니다. 이어지는 두 CLI 명령의 출력은 각각 `1.10.0`과 `NO_UPDATE`여야 합니다. [공식 TDD](https://github.com/cursor/plugins/blob/main/pstack/skills/tdd/SKILL.md)

## 7. 설계안들을 비교하고 기능 추가하기 (14~20분)

다음으로 beta 채널의 릴리스를 선택하는 기능을 추가합니다. 구현을 시작하기 전에 서로 다른 설계안을 비교하고, 선택한 설계에 따라 기능을 완성합니다.

```text
/architect beta 채널 선택 기능을 설계하고 구현해 주십시오.
기본 실행에서는 stable 채널을 유지하고, --channel beta를 지정하면 beta 채널만 대상으로 선택합니다.
기존 choose_release(releases, current) 호출은 계속 동작해야 합니다.
현재 버전보다 높은 릴리스만 선택하고 입력 목록을 변경하지 않는 규칙도 유지해 주십시오.
두 하위 에이전트가 같은 과제를 독립적으로 설계하되, 각 설계안은 별도 임시 디렉터리에 작성하게 해 주십시오.
설계 개요는 짧게 작성하고, 구조가 서로 다른 설계안 두 개와 별도 심사 결과를 제시해 주십시오.
예를 들어 기존 함수를 확장하는 방식과 작은 선택기 객체를 도입하는 방식을 비교할 수 있습니다.
채택 이유를 설명한 뒤 구현까지 진행해 주십시오. 외부 패키지는 추가하지 마십시오.
회귀 테스트, CLI 실행, SPEC.md 갱신을 완료하고 로컬 커밋을 남겨 주십시오.
다음 단계에서는 커밋된 코드를 검증할 수 있어야 합니다.
```

`architect`는 구현 전에 호출 방법, 타입, 함수의 경계를 설계합니다. 내부적으로 `arena`를 사용하여 같은 과제에 대한 여러 설계안을 독립적으로 작성하고, 심사와 통합을 거쳐 최종 설계를 선택합니다. 이 단계에서는 설계에 이어 구현까지 수행하도록 요청합니다. [공식 architect](https://github.com/cursor/plugins/blob/main/pstack/skills/architect/SKILL.md) · [공식 arena](https://github.com/cursor/plugins/blob/main/pstack/skills/arena/SKILL.md)

실제로 두 하위 에이전트가 설계안을 작성했는지, 별도의 심사 결과가 있는지 확인합니다. 주 에이전트가 혼자 두 가지 방안을 제시한 것만으로는 독립된 설계 비교를 수행했다고 볼 수 없습니다. 비교의 목적은 적절한 구조를 선택하는 것이므로, 최종 구현은 단순한 형태여도 무방합니다.

구현을 마치면 다음 명령을 실행합니다.

```bash
python3 release_picker.py
python3 release_picker.py --channel beta
```

출력은 각각 `1.10.0`과 `2.0.0`이어야 합니다.

## 8. 여러 모델로 코드 검토하기 (20~23분)

구현 결과를 여러 모델이 독립적으로 검토하도록 요청합니다. 검토 범위는 실습 시작 시점인 `lab-start`부터 현재 커밋까지의 전체 변경 사항입니다.

```text
/interrogate git diff lab-start..HEAD의 전체 변경 사항을 검토해 주십시오.
목표는 버전을 숫자로 비교하고, stable 기본값을 유지하면서 beta 채널을 지원하는 것입니다.
SPEC.md를 기준으로 구현과 테스트를 독립적으로 검토하고,
각 검토자의 실제 모델명과 의견이 일치하거나 다른 부분을 제시해 주십시오.
실습 범위를 벗어나는 입력 형식이나 향후의 대규모 확장을 요구하지 마십시오.
코드를 자동으로 수정하지 말고, 지적 사항을 Act On, Consider, Noted, Dismissed로 분류해 주십시오.
```

`interrogate`는 설정된 모델별로 검토를 수행하고, 지적 사항을 종합하여 조치의 필요성을 판단합니다. 검토 결과는 다음과 같이 구분합니다.

| 분류 | 의미 |
| --- | --- |
| `Act On` | 실제 결함이나 중요한 문제이므로 수정해야 하는 사항 |
| `Consider` | 타당한 지적이지만 수정 비용과 효과를 함께 검토해야 하는 사항 |
| `Noted` | 참고할 만하나 현재 조치가 필요하지 않은 사항 |
| `Dismissed` | 잘못된 지적이거나 현재 맥락에 맞지 않아 채택하지 않은 사항 |

검토 결과가 코드에 자동으로 반영되지는 않습니다. 여러 모델의 의견이 일치하더라도 실제 코드와 실행 결과를 근거로 판단해야 합니다. 수정할 문제가 없다는 검토 결과도 유효합니다. [공식 interrogate](https://github.com/cursor/plugins/blob/main/pstack/skills/interrogate/SKILL.md)

`Act On`에 실제 결함이 포함되어 있으면 다음 프롬프트로 먼저 수정하고 재검증합니다. 추가 수정이 필요하면 전체 실습 시간이 늘어날 수 있습니다.

```text
/poteto-mode 방금 검토에서 Act On으로 분류한 실제 결함만 수정해 주십시오.
회귀 테스트와 CLI 실행으로 결과를 확인하고 로컬 커밋을 남겨 주십시오.
```

## 9. 검증 항목들을 나누어 병렬로 실행하기 (23~27분)

이번에는 두 하위 에이전트에게 서로 다른 검증 항목을 맡깁니다. 두 에이전트가 같은 코드 버전을 검사하도록 검증 대상 커밋의 해시(SHA)를 먼저 확정합니다.

```text
/swarm 이 저장소는 원격에 없으므로 로컬 하위 에이전트 두 개로 검증해 주십시오.
먼저 git rev-parse HEAD로 검증 대상 커밋의 SHA를 확정하고, 동일한 값을 두 작업자에게 전달해 주십시오.
A는 버전의 숫자 비교가 올바른지, 같은 버전이나 낮은 버전을 업데이트 대상으로 선택하지 않는지 검증합니다.
B는 stable과 beta 채널이 분리되는지, 입력 순서와 무관하게 같은 버전을 선택하는지,
입력 목록을 변경하지 않는지 검증합니다.
각 작업자는 기존 테스트를 읽는 데 그치지 않고 실제 Python 코드를 실행해야 합니다.
프로젝트 파일은 수정하지 말고, 필요한 임시 파일은 각자 별도 디렉터리에 작성해 주십시오.
각 결과에는 SHA, 실행 방법, 실제 출력을 포함하고 PASS, ISSUES, BLOCKED 가운데 하나로 판정해 주십시오.
주 에이전트는 검증하지 못한 항목도 포함하여 표 하나로 결과를 종합해 주십시오.
병렬 실행을 지원하지 않는 환경이면 BLOCKED로 보고해 주십시오.
```

`arena`는 같은 과제에 대한 여러 후보를 비교하여 하나의 결과물을 만듭니다. 이번 `swarm` 실습에서는 서로 다른 검증 항목을 작업자에게 나누어 맡긴 뒤 결과를 종합합니다. `swarm`은 동일한 과제를 여러 작업자에게 맡겨 결과를 비교하는 방식도 지원합니다. 기본 실행 환경은 cloud이지만, 이 실습에서는 원격에 없는 파일에 접근해야 하므로 local을 명시합니다. [공식 swarm](https://github.com/cursor/plugins/blob/main/pstack/skills/swarm/SKILL.md)

결과를 확인할 때는 두 작업자가 동일한 SHA를 검사했는지, 각 검증 항목에 실제 실행 결과가 있는지 살펴봅니다. `BLOCKED`는 검증을 수행하지 못했다는 뜻이며, 작업자가 결과를 제출하지 않은 경우에도 검증을 통과한 것으로 처리해서는 안 됩니다.

## 10. 문서를 다듬고 판단 기록 확인하기 (27~30분)

먼저 프로그램의 실제 동작에 맞게 사용 설명을 정리합니다. 예제의 `README.md`에는 이 과정을 연습할 수 있도록 과장된 표현이 포함되어 있습니다.

```text
/unslop README.md를 프로그램의 실제 동작에 맞는 한국어 사용 설명으로 고쳐 주십시오.
기본 실행 명령, beta 채널 실행 명령, 버전 형식의 제한을 포함하여 다섯 문장 이내로 작성해 주십시오.
구현과 테스트는 변경하지 마십시오.
```

이어서 지금까지 내린 주요 판단과 그 근거를 기록합니다.

```text
/show-me-your-work 이 대화에서 실제로 내린 결정을 decisions.tsv에 정리해 주십시오.
버그의 원인, 채택한 설계, 검증 결과를 확인할 수 있는 근거 경로와 함께 기록해 주십시오.
과거의 결정을 지금 정리한 행은 사후에 작성했음을 표시하고, 확인할 수 없는 과거 시각을 임의로 적지 마십시오.
실행하지 않은 검사를 수행했다고 기록하지 마십시오.
대화 기록과 판단 기록을 대조하고, 다른 계열 모델의 검토를 거쳐 Attention 항목을 제시해 주십시오.
다른 모델이나 대화 기록에 접근할 수 없으면 그 제한을 명시해 주십시오.
코드는 수정하지 마십시오.
```

`show-me-your-work`은 판단, 이유, 근거, 결과를 탭으로 구분한 표 형식인 TSV로 기록하고 실행 기록과 대조합니다. 이 실습에서는 마지막에 주요 결정을 정리합니다. 장시간 작업을 맡길 때는 처음부터 이 스킬을 호출하여 결정이 이루어질 때마다 기록을 누적하는 것이 좋습니다. [공식 판단 기록](https://github.com/cursor/plugins/blob/main/pstack/skills/show-me-your-work/SKILL.md)

마지막으로 다음 명령을 직접 실행하여 결과를 확인합니다.

```bash
python3 -m unittest -v
python3 release_picker.py
python3 release_picker.py --current 1.9.0
python3 release_picker.py --current 1.10.0
python3 release_picker.py --channel beta
python3 release_picker.py --channel beta --current 2.0.0
git diff --check
```

| CLI의 실행 인자 | 기대 출력 |
| --- | --- |
| 인자 없음 | `1.10.0` |
| `--current 1.9.0` | `1.10.0` |
| `--current 1.10.0` | `NO_UPDATE` |
| `--channel beta` | `2.0.0` |
| `--channel beta --current 2.0.0` | `NO_UPDATE` |

다음이 모두 확인되면 실습을 마칩니다.

- 전체 테스트가 통과하고, 위 다섯 가지 CLI 실행 결과가 기대 출력과 일치합니다.
- 독립된 설계안, 코드 검토, 병렬 검증을 실제로 수행했음을 확인할 수 있는 기록이 있습니다.
- `decisions.tsv`의 각 판단에 제시된 근거를 확인할 수 있습니다.

추가된 테스트의 개수와 최종 코드의 구조는 에이전트가 선택한 구현 방식에 따라 달라질 수 있습니다.

## 11. 다른 기능 살펴보기

pstack에는 이번 실습에서 사용한 기능 외에도 엔지니어를 위한 다양한 기능이 있습니다. 아래 표에는 각 기능을 사용하는 상황과 수행하는 작업, 얻을 수 있는 결과를 정리했습니다.

`/`로 시작하는 이름은 직접 입력하는 명령입니다. Perf, Babysit처럼 작업 절차의 이름만 적힌 항목은 `/poteto-mode`에 목표를 설명하면 요청에 맞게 선택되는 절차입니다.

PR(pull request)은 변경한 코드를 검토하고 병합하기 위한 요청입니다. CI(continuous integration)는 코드가 변경되면 테스트와 빌드 등의 검사를 자동으로 실행하는 절차입니다. PR 관련 기능을 사용하려면 원격 저장소와 접근 권한이 필요하며, 형식 검증 기능에는 별도의 검증 도구가 필요할 수 있습니다.

| 기능 | 사용하는 상황 | 수행하는 작업과 결과 |
| --- | --- | --- |
| [/in-your-own-words](https://github.com/cursor/plugins/blob/main/pstack/skills/in-your-own-words/SKILL.md) | 에이전트가 요청을 정확히 이해했는지 확인하고 싶을 때 | 사용자의 목표와 해결하려는 문제를 에이전트가 자신의 말로 다시 설명합니다. 코드를 변경하기 전에 잘못 이해한 부분을 확인할 수 있습니다. |
| [/sharpen](https://github.com/cursor/plugins/blob/main/pstack/skills/sharpen/SKILL.md) | 작업을 요청하기 전에 요청문을 더 명확하게 만들고 싶을 때 | 목표를 달성하는 데 필요한 자료, 작업 방법, 검증 방법을 보완하여 요청문을 다시 작성합니다. 이 단계에서는 원래 요청한 작업을 실행하지 않습니다. |
| [/teach](https://github.com/cursor/plugins/blob/main/pstack/skills/teach/SKILL.md) | 변경된 코드나 익숙하지 않은 시스템을 이해하고 싶을 때 | 코드가 어떻게 동작하는지와 왜 그렇게 설계되었는지를 조사합니다. 이해에 필요한 개념부터 순서대로 설명하고, 필요하면 그림을 함께 제시합니다. |
| [/recall](https://github.com/cursor/plugins/blob/main/pstack/skills/recall/SKILL.md) | 이전에 하던 일을 다시 시작하면서 진행 상황을 파악하고 싶을 때 | 이전 대화, 관련 작업 기록, 현재 코드와 PR 상태를 조사합니다. 이미 결정한 사항, 남아 있는 문제, 다음에 할 일을 정리하여 작업을 이어갈 수 있게 합니다. |
| [/ketchup](https://github.com/cursor/plugins/blob/main/pstack/skills/ketchup/SKILL.md) | 에이전트에게 작업을 맡긴 뒤 현재 대화의 진행 상황을 확인하고 싶을 때 | 이 대화에서 마지막으로 확인한 이후 무엇이 진행되었는지 설명합니다. 사용자가 결정하거나 답해야 할 항목도 함께 정리합니다. |
| [/blast-radius](https://github.com/cursor/plugins/blob/main/pstack/skills/blast-radius/SKILL.md) | 작은 코드 변경이 다른 기능에 문제를 일으키지 않는지 확인하고 싶을 때 | 변경한 코드가 사용되는 곳과 영향을 받는 동작을 추적합니다. 기존 사용 방식이 유지되는지 실제 코드를 실행하여 확인하고 그 근거를 제시합니다. |
| [성능 병목 조사 절차 `Perf`](https://github.com/cursor/plugins/blob/main/pstack/skills/poteto-mode/playbooks/perf-issue.md) | 프로그램의 특정 동작이 느린 원인을 찾아 개선하고 싶을 때 | 현재 성능을 먼저 측정하고, 실행 중 어디에서 시간이 소요되는지 조사하여 원인을 찾습니다. 코드를 수정한 뒤 같은 조건에서 다시 측정하여 개선 여부를 확인합니다. |
| [반복적인 성능 개선 절차 `Hillclimb`](https://github.com/cursor/plugins/blob/main/pstack/skills/poteto-mode/playbooks/hillclimb.md) | 처리 시간이나 메모리 사용량 같은 수치를 목표 수준까지 계속 개선하고 싶을 때 | 개선할 지표와 목표를 정하고, 가설 수립·코드 변경·전후 측정을 반복합니다. 효과가 확인된 변경을 커밋으로 남기면서 다음 개선을 진행합니다. |
| [/benchmark-checklist](https://github.com/cursor/plugins/blob/main/pstack/skills/benchmark-checklist/SKILL.md) | 성능이 좋아졌다는 측정 결과를 믿어도 되는지 확인하고 싶을 때 | 비교 조건, 반복 측정, 오류 발생 여부 등을 점검합니다. 준비 상태나 측정 방식의 차이 때문이 아니라 실제 작업이 빨라진 것인지 판단하고, 근거가 부족하면 판정을 유보합니다. |
| [/create-verification-skill](https://github.com/cursor/plugins/blob/main/pstack/skills/create-verification-skill/SKILL.md) | 프로그램이 제대로 동작하는지 확인하는 절차를 반복해서 사용하고 싶을 때 | 프로그램을 실행하는 방법, 기능별 확인 방법, 기대 결과와 증거를 남기는 방법을 조사하여 프로젝트용 검증 스킬을 만듭니다. 이후 에이전트가 같은 절차로 실제 동작을 확인할 수 있습니다. |
| [/maintain-verification-skill](https://github.com/cursor/plugins/blob/main/pstack/skills/maintain-verification-skill/SKILL.md) | 프로그램이 바뀌어 기존 검증 절차가 맞지 않게 되었을 때 | 기존 검증 스킬의 설명을 현재 코드와 비교하고 실제 동작을 확인합니다. 달라진 기능이나 실행 방법을 반영하여 검증 절차를 갱신합니다. |
| [/create-formal-verification-skill](https://github.com/cursor/plugins/blob/main/pstack/skills/create-formal-verification-skill/SKILL.md) | 동시 실행이나 재시도에서 드물게 발생하는 오류를 검증하고 싶을 때 | 예를 들어 ‘하나의 작업이 동시에 두 번 실행되지 않는다’처럼 지켜야 할 규칙과 검증 범위를 정합니다. 적합한 검증 도구로 규칙이 깨지는 경우가 있는지 확인하고, 같은 검증을 다시 실행할 수 있는 스킬을 만듭니다. |
| [/statechart](https://github.com/cursor/plugins/blob/main/pstack/skills/statechart/SKILL.md) | 작업이 ‘대기→실행→완료’처럼 어떤 상태를 거쳐 진행되는지 살펴보고 싶을 때 | 시스템의 상태와 상태가 바뀌는 규칙을 모델로 작성하여 검사합니다. 상태 사이의 이동을 그림으로 보여 주고, 규칙을 어기는 상태와 그 상태에 이르는 경로를 표시합니다. |
| [PR 생성 절차 `Opening a PR`](https://github.com/cursor/plugins/blob/main/pstack/skills/poteto-mode/playbooks/opening-a-pr.md) | 구현과 검증을 마친 변경을 다른 사람에게 검토받고 싶을 때 | 변경 내용을 순서가 분명한 커밋으로 정리하고 PR의 제목과 설명을 작성하여 검토 요청을 생성합니다. 무엇을 바꾸었고 어떻게 검증했는지 검토자가 확인할 수 있게 합니다. |
| [PR 관리 절차 `Babysit`](https://github.com/cursor/plugins/blob/main/pstack/skills/poteto-mode/playbooks/babysit.md) | 진행 중인 PR을 병합할 수 있는 상태로 유지하고 싶을 때 | PR의 상태를 계속 확인하면서 코드 충돌, 검토 의견, 자동 검사 실패에 대응합니다. 아직 해결되지 않은 항목과 병합 준비 상태를 확인할 수 있습니다. |
| [병합 절차 `Shipping`](https://github.com/cursor/plugins/blob/main/pstack/skills/poteto-mode/playbooks/shipping.md) | 검토와 검증을 마친 변경을 주 브랜치에 반영하고 싶을 때 | 변경 내용과 검증 결과를 다시 확인한 뒤 병합을 진행합니다. 여러 PR이 앞선 변경에 의존하는 경우에는 필요한 순서에 따라 병합합니다. |
| [장시간 작업 절차 `Autonomous run`](https://github.com/cursor/plugins/blob/main/pstack/skills/poteto-mode/playbooks/autonomous-run.md) | 큰 작업을 완료 조건에 도달할 때까지 계속 진행하도록 맡기고 싶을 때 | 목표와 완료 조건, 허용 범위를 바탕으로 조사·구현·검증을 이어갑니다. 주요 판단과 실행 결과를 기록하여 사용자가 나중에 작업 과정을 확인할 수 있게 합니다. |
| [프로젝트 조정 절차 `Orchestrate`](https://github.com/cursor/plugins/blob/main/pstack/skills/poteto-mode/playbooks/orchestrate.md) | 여러 날에 걸쳐 여러 에이전트와 PR이 필요한 작업을 관리하고 싶을 때 | 하나의 조정 에이전트가 작업을 나누고, 선행 작업과 후속 작업의 관계를 추적합니다. 각 에이전트와 PR의 진행 상황을 모아 전체 작업을 조정합니다. |
| [독립된 PR들의 자동 진행 절차 `Autopilot-full`](https://github.com/cursor/plugins/blob/main/pstack/skills/poteto-mode/playbooks/autopilot-full.md) | 서로 독립적인 여러 작업을 각각 PR로 만들어 완료하고 싶을 때 | 각 PR에 담당 에이전트를 배정하여 구현부터 검증과 병합까지 맡깁니다. 조정 에이전트는 병합 전에 별도의 검증을 수행하도록 관리합니다. |
| [연속된 PR들의 준비 절차 `Autopilot-stack`](https://github.com/cursor/plugins/blob/main/pstack/skills/poteto-mode/playbooks/autopilot-stack.md) | 앞선 변경 위에 후속 변경을 차례로 쌓아 검토받고 싶을 때 | 여러 변경을 의존 관계에 맞춰 순서가 있는 PR들로 구성하고 검증합니다. 사용자가 검토하고 병합할 수 있는 상태로 준비합니다. |
| [/show-me-your-work](https://github.com/cursor/plugins/blob/main/pstack/skills/show-me-your-work/SKILL.md) | 자리를 비운 동안 에이전트가 어떤 판단을 내렸는지 확인하고 싶을 때 | 선택한 방법, 선택 이유, 실행 근거와 결과를 표 형태의 기록으로 남깁니다. 기록을 실제 대화 및 실행 내용과 대조하여 검토할 부분을 알려 줍니다. |
| [Cursor의 반복 실행 명령 `/loop`](https://github.com/cursor/plugins/blob/main/pstack/docs/guide/07-overnight.md) | 일정 간격으로 에이전트가 작업을 다시 확인하고 이어가게 하고 싶을 때 | 정해진 간격으로 에이전트를 다시 실행하여 작업을 이어가거나 진행 상태를 확인하게 합니다. pstack의 작업 절차와 함께 사용할 수 있는 Cursor 자체 기능입니다. |
| [/reflect](https://github.com/cursor/plugins/blob/main/pstack/skills/reflect/SKILL.md) | 한 작업을 마친 뒤 다음 작업에서 같은 시행착오를 줄이고 싶을 때 | 이번 대화에서 얻은 교훈을 검토하고, 기존 스킬에 반영할 개선안을 제시합니다. 사용자가 승인한 개선안을 스킬에 적용하여 다음 작업에 활용합니다. |
| [/correct](https://github.com/cursor/plugins/blob/main/pstack/skills/correct/SKILL.md) | 에이전트가 같은 종류의 실수를 반복할 때 | 커밋과 검토 기록 등을 조사하여 반복되는 실수의 유형을 찾습니다. 설계, 타입, 자동 검사, 테스트를 개선하여 잘못된 변경을 막고, 새 검사가 과거의 실수를 검출하는지 확인합니다. |
| [/automate-me](https://github.com/cursor/plugins/blob/main/pstack/skills/automate-me/SKILL.md) | 자신의 작업 방식에 맞는 에이전트 지침을 만들고 싶을 때 | 이전 대화와 사용자의 답변에서 작업 방식과 선호를 파악하여 개인용 모드 스킬을 만듭니다. 이후 그 모드를 호출하여 같은 지침에 따라 작업하게 할 수 있습니다. |
| [/unslop](https://github.com/cursor/plugins/blob/main/pstack/skills/unslop/SKILL.md) | 글의 과장된 표현이나 기계적인 상투어를 정리하고 싶을 때 | 의미를 유지하면서 불필요한 수식과 상투적인 표현을 줄입니다. 설명하려는 대상과 실제 동작이 드러나는 문장으로 글을 다듬습니다. |
| [/technical-writing](https://github.com/cursor/plugins/blob/main/pstack/skills/technical-writing/SKILL.md) | README, 설계 문서, PR 설명 등을 작성하거나 정리하고 싶을 때 | 독자와 문서의 목적에 맞게 정보의 순서, 용어, 실행 절차, 예시를 정리합니다. 독자가 필요한 내용을 이해하고 실제로 따라 할 수 있는 기술 문서를 작성하도록 돕습니다. |
| [/no-comments](https://github.com/cursor/plugins/blob/main/pstack/skills/no-comments/SKILL.md) | 코드의 주석과 주석이 설명하는 임시방편을 검토하고 싶을 때 | 별도의 검토 에이전트가 주석을 검토하고, 채택된 지적에 따라 주석과 관련 코드를 정리합니다. 지켜야 할 조건을 타입 검사나 테스트 등으로 표현하는 방법도 검토합니다. |
| [/bro](https://github.com/cursor/plugins/blob/main/pstack/skills/bro/SKILL.md) | 바로 앞의 답변에 전문용어가 많아 이해하기 어려울 때 | 직전 답변의 뜻을 유지하면서 전문용어와 복잡한 표현을 쉬운 말로 바꾸어 다시 설명합니다. |
| [/poteto-help](https://github.com/cursor/plugins/blob/main/pstack/skills/poteto-help/SKILL.md) | 어떤 스킬이나 작업 절차를 써야 할지 모를 때 | 하려는 일을 설명하면 적절한 기능과 사용 방법을 안내합니다. 바로 입력해 볼 수 있는 프롬프트도 제안합니다. |

`reflect`는 작업을 요약하는 데 그치지 않고 스킬의 개선으로 이어지는 기능입니다. 제안된 변경 내용을 검토한 뒤 적용합니다. 버전 비교 오류처럼 테스트나 코드 구조로 재발을 방지할 수 있는 문제는 지침 문구만 추가하기보다 실행 가능한 검사나 구조의 개선으로 다루는 것이 적절합니다.

일반적인 작업에서는 `/poteto-mode`에 목표, 완료 조건, 필요한 실행 결과를 전달하면 됩니다. 이번 실습에서는 기능별 역할과 차이를 익히기 위해 여러 스킬을 직접 호출했습니다. [공식 기능 목록](https://github.com/cursor/plugins/blob/main/pstack/README.md) · [공식 검증과 배포 안내](https://github.com/cursor/plugins/blob/main/pstack/docs/guide/06-verify-and-ship.md)

## 12. 문제 해결

| 증상 | 해결 방법 |
| --- | --- |
| 슬래시 명령이 보이지 않습니다. | 플러그인 설치가 완료되었는지 확인하고 새 Agent 채팅을 엽니다. 해결되지 않으면 Cursor를 다시 열고 `/` 메뉴에서 명령을 검색합니다. |
| 지정한 모델을 사용할 수 없다는 메시지가 나옵니다. | `/setup-pstack`에서 실제로 확인된 모델이나 `inherit-parent`를 선택합니다. 설정 후 새 채팅을 열고 5절의 공통 조건을 다시 전달합니다. |
| `deslop`, `control-cli` 등의 보조 스킬이 설치되어 있지 않습니다. | 이번 실습에서는 해당 보조 스킬을 생략한 이유를 밝히고 Python 명령으로 검증하도록 요청합니다. |
| 로컬 하위 에이전트를 실행할 수 없습니다. | 해당 단계의 결과를 `BLOCKED`로 기록합니다. 병렬 실행을 체험하려면 로컬 하위 에이전트를 지원하는 Cursor 환경이 필요합니다. |
| 실제 실행 결과가 기대 출력과 다릅니다. | `/poteto-mode`에 실행 명령과 실제 출력을 전달하고, `SPEC.md`를 기준으로 오류를 재현하여 수정하고 검증하도록 요청합니다. |
| 실습을 처음부터 다시 진행하려고 합니다. | 기존 디렉터리는 보존하고, 다른 빈 작업 디렉터리에서 3절의 예제 생성 명령을 다시 실행합니다. |

## 13. 참고

**예제의 검증 범위**: 초기 테스트 3개의 통과와 잘못된 출력, 추가 회귀 검사 3개의 실패, 버전 비교 수정 후 테스트 6개의 통과를 실행으로 확인했습니다. 별도의 참조 구현에서는 채널 선택, 입력 순서, 입력 목록의 불변성을 포함한 테스트 9개와 최종 CLI 실행 결과 5개를 확인했습니다. Cursor 내부에서 모델을 호출하는 전체 절차를 이 환경에서 실행한 것은 아니므로, 각 단계의 소요 시간은 예상치입니다.
