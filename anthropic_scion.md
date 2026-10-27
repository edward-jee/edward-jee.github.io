# Anthropic의 소스 코드 관리 도구 "Scion"

Git을 아는 엔지니어를 위한 Scion 소개

2026년 10월 28일  |  읽는 데 걸리는 시간 10분 이내

> **주의: 이 문서는 AI 도구에 의해 만들어졌습니다. 저 Spike (Edward) Jee가 일부 섹션들은 검토하고 교정하였지만 전혀 proofreading되지 않은 부분도 많습니다.**

Anthropic은 여러 프로젝트의 소스 코드를 **단 하나의 저장소(repository)**에 모아 관리합니다. 이런 구성을 **monorepo(모노레포)**라고 합니다. 이 회사는 코드 저장소 관리를 위하여 Git을 사용했는데, 최근 자체 개발한 **Scion**이라는 도구로 Git을 대체하였습니다. [1](https://www.anthropic.com/research/redesigning-source-control)

Git은 **"분산"(distributed) 버전 관리 시스템**입니다. Git에서는 완전한 클론(clone)을 만들면 소스 파일뿐 아니라 변경 이력도 개발자의 컴퓨터로 복제됩니다. 이렇게 만들어진 로컬 저장소는 **서버에 연결하지 않고도 이력을 조회하고 새 commit을 만들 수 있는 독립적인 저장소**입니다. 각 저장소는 필요할 때 다른 저장소와 변경 이력을 주고받습니다. [4](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)[9](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)

Scion은 **서버 중심의 소스 코드 관리 시스템**입니다. 클라이언트가 항상 서버에 연결될 수 있다고 가정하고, 변경 이력 조회나 commit 생성, merge 등의 작업을 서버에서 수행합니다. 클라이언트는 실행할 작업에 필요한 데이터만 받아 사용합니다. [1](https://www.anthropic.com/research/redesigning-source-control)

Git 이전에 쓰이던 CVS와 SVN도 서버 중심의 버전 관리 시스템이었습니다. SVN에서도 서버에 변경 이력을 조회하거나 필요한 디렉터리만 받을 수 있습니다. [7](https://svnbook.red-bean.com/en/1.7/svn.basic.version-control-basics.html)[8](https://svnbook.red-bean.com/en/1.7/svn.advanced.sparsedirs.html) 이들과 비교되는 Scion의 특징은, Scion은 **거대한 저장소가 수많은 자동 작업들에 의해 동시에 액세스되는 환경**에 맞게 설계되었다는 것입니다. 저장소 데이터를 여러 서버에 나누어 저장하고, 한 번 받은 파일은 임시 저장해 두었다가 다른 작업을 할 때에 다시 사용합니다. [1](https://www.anthropic.com/research/redesigning-source-control)

Google이 사내에서 쓰기 위해 만든 **Piper**도, Scion처럼 **저장 공간과 요청 처리 능력을 여러 서버로 확장**할 수 있도록 설계되었습니다. 전통적인 SVN 구성과 비교하면, Piper는 저장소가 커지고 요청이 늘어날 때 서버 한 대의 용량과 성능에 덜 제약받는다는 장점이 있습니다. Piper와 함께 쓰이는 도구인 **CitC**는 개발자가 파일을 보고 편집할 작업공간을 제공합니다. 이에 비해 Scion에서는 **작업공간 없이 API로 조회와 변경을 처리하는 방식**이 특히 강조됩니다. [1](https://www.anthropic.com/research/redesigning-source-control)[2](https://abseil.io/resources/swe-book/html/ch16.html)[3](https://research.google/pubs/why-google-stores-billions-of-lines-of-code-in-a-single-repository/)

## 1. Anthropic이 Git을 Scion으로 대체한 이유

개발자가 한 작업공간에서 코드를 수정하고 과거 변경을 분석할 때에는 Git의 로컬 저장소가 유용합니다. 필요한 이력을 이미 가지고 있으므로 서버 응답을 기다리지 않아도 되고, 네트워크가 끊겨도 작업을 계속할 수 있습니다. [4](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)

그러나 자동화된 도구들이 코드 저장소를 액세스할 때에는 이러한 방식이 꼭 유리하지는 않습니다. 예를 들어 코드가 바뀔 때마다 빌드와 테스트를 실행하는 **CI(Continuous Integration, 지속적 통합)**를 생각해 보겠습니다. 짧은 검사를 실행할 때마다 로컬 저장소를 새로 준비한다면, 데이터를 받는 데에도 시간과 자원이 들어갑니다.

가령 검사 한 번마다 데이터를 10 MB씩 받는다고 가정해 보겠습니다. 같은 검사를 100만 번 실행하면 전송량이 약 10 TB가 됩니다. **작업 하나의 준비 비용이 작아도, 같은 작업을 반복하는 횟수가 많으면 전체 비용은 커집니다.**

Anthropic이 공개한 수치들로부터, 이러한 문제가 얼마나 큰지 짐작할 수 있습니다. 2026년 9월에는 하루 **30,000건 이상**의 코드 변경이 병합(merge)되었으며, CI에서 코드를 체크아웃하는 횟수는 하루 약 **2,500만 회**였습니다. [1](https://www.anthropic.com/research/redesigning-source-control)

## 2. Scion으로 작업하면 무엇이 달라지는가

### 2.1. 변경을 서버에 기록합니다

Git에서는 먼저 로컬 저장소에 commit을 만듭니다. 다른 저장소와 공유하려면 push로 이 기록을 보냅니다. Scion에서는 서버에 변경 기록을 만들도록 요청하며, 기록이 처음부터 서버에 있으므로 **따로 push할 필요가 없습니다**. [1](https://www.anthropic.com/research/redesigning-source-control)[4](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)

Scion은 변경 한 묶음을 **changeset**이라고 부릅니다. changeset을 서버에 기록해도 그 변경이 main에 자동으로 반영되지는 않습니다. **리뷰 등 필요한 절차를 거친 뒤 main에 병합해야** 팀이 사용하는 기준 코드에 반영됩니다. [1](https://www.anthropic.com/research/redesigning-source-control)

changeset에는 첫 번째 부모 기록과 비교해 바뀐 파일 목록이 들어갑니다. 여기서 부모는 현재 변경이 이어지는 이전 기록을 뜻합니다. 각 파일의 내용은 그 내용으로부터 계산한 식별값인 **해시(hash)**로 참조합니다. Scion은 이 기록을 바탕으로 파일별 변경 이력이나 누가 어느 줄을 고쳤는지 빠르게 조회할 수 있는 자료를 따로 만듭니다. [1](https://www.anthropic.com/research/redesigning-source-control)

Git의 commit은 당시 파일 트리의 상태인 **스냅샷(snapshot)**을 가리킵니다. 바뀌지 않은 파일의 객체는 재사용하므로, commit할 때마다 모든 파일을 새로 복사하지는 않습니다. Git과 Scion은 변경 이력을 표현하는 구조가 다르지만, 두 시스템 모두 특정 버전의 전체 파일 상태를 복원할 수 있습니다. [1](https://www.anthropic.com/research/redesigning-source-control)[4](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)

### 2.2. 파일을 받지 않고도 필요한 결과를 얻습니다

자동화된 도구가 두 버전 사이에서 어떤 파일이 바뀌었는지만 확인한다고 해 보겠습니다. 이 도구는 파일 내용을 모두 받아 로컬에 펼쳐 놓을 필요가 없습니다. Scion의 **API로 서버에 차이를 물어보고 결과만 받으면 됩니다**. 필요한 조회를 위해 로컬 저장소를 만들고 유지하는 비용이 사라지는 것입니다. [1](https://www.anthropic.com/research/redesigning-source-control)

컴파일러처럼 실제 파일 내용이 필요한 도구도 있습니다. Scion은 이런 경우에도 다음 두 방식으로 다운로드할 데이터의 범위를 줄입니다. [1](https://www.anthropic.com/research/redesigning-source-control)

- **Sparse checkout**에서는 작업에 필요한 디렉터리를 미리 고릅니다. 예를 들어 문서 검사라면 문서 디렉터리만 받도록 설정할 수 있습니다.

- **가상 체크아웃(virtualized checkout)**에서는 프로그램이 파일을 실제로 읽을 때 내용을 가져옵니다. 저장소에 파일이 있어도 작업에서 읽지 않으면 그 내용을 다운로드하지 않습니다.

### 2.3. 한 번 받은 데이터를 다른 작업에서도 재사용합니다

Scion은 받은 파일 내용을 **캐시(cache)**에 보관합니다. 같은 컴퓨터에서 실행되는 작업들은 이 캐시를 함께 사용하므로, 앞선 작업이 받은 파일을 다음 작업이 다시 다운로드할 필요가 줄어듭니다. 같은 지역의 여러 서버가 이용하는 캐시도 두어, 원본 데이터를 보관하는 서버에 요청이 몰리는 부담을 줄입니다. [1](https://www.anthropic.com/research/redesigning-source-control)

## 3. Git, Piper, Scion의 비교

### 3.1. 저장소의 구조와 작업 방식

세 시스템을 비교할 때에는 **개발자의 로컬 저장소가 어떤 역할을 하는지**부터 살펴보면 좋습니다. Git의 완전한 클론은 독립적으로 버전을 관리할 수 있는 저장소입니다. Piper와 Scion에서는 서버가 버전 관리를 맡고, 클라이언트는 작업에 필요한 데이터에 접근합니다. [1](https://www.anthropic.com/research/redesigning-source-control)[2](https://abseil.io/resources/swe-book/html/ch16.html)[4](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)

Piper는 단 하나의 공식 코드 저장소를 여러 서버에 나누어 운영합니다. 여기서 **중앙집중식**이라는 말은 모두가 같은 공식 저장소를 사용한다는 뜻입니다. 저장소 전체를 한 대의 서버에 넣어 운영한다는 뜻은 아닙니다. **Git의 분산 구조는 각 클론의 독립성을, Piper의 서버 분산은 서비스의 용량과 처리 능력을 키우는 방식을 가리킵니다.** [2](https://abseil.io/resources/swe-book/html/ch16.html)[9](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)

Google의 **CitC(Clients in the Cloud)**는 개발자가 Piper의 파일을 보고 편집할 수 있게 해 주는 도구입니다. 수정하지 않은 파일은 공유된 저장소에서 읽고, **수정한 파일만 개발자 자신의 작업공간에 저장**합니다. 따라서 개발자마다 전체 저장소를 복제해 둘 필요가 없습니다. **Piper는 버전 관리를 맡고, CitC는 편집 작업공간을 제공**합니다. [3](https://research.google/pubs/why-google-stores-billions-of-lines-of-code-in-a-single-repository/)

| **비교 항목** | **Git** | **Piper와 CitC** | **Scion** |
| --- | --- | --- | --- |
| **저장소 구조** | 완전한 클론들 각각이 독립 저장소 | 중앙 저장소를 여러 서버로 나누어 운영 | 중앙 저장소를 여러 서버로 나누어 운영 |
| **작업 파일** | 로컬 작업 디렉터리 | 수정한 파일만 개발자의 작업공간에 저장 | 디렉터리를 골라 받거나, 읽는 파일만 다운로드 |
| **변경 기록** | 로컬 commit을 만들고 push로 공유 | 작업공간에서 만든 변경을 리뷰한 뒤 중앙 저장소에 commit | changeset을 서버에 기록하고, 리뷰 후 main에 병합 |
| **브랜치 정책** | 팀이 브랜치 정책을 선택 | trunk 중심 개발과 release 브랜치 | main 중심 개발과 release 브랜치 |
| **코드 리뷰** | 팀이 리뷰 도구를 선택 | Critique 리뷰 도구 | Antique 리뷰 도구 |
| **접근 통제** | 호스팅 서비스에 따라 다름 | 파일 단위 접근 통제 | 저장소 및 디렉터리 단위 권한 |

위에서는 Git이 일반적인 방식으로 쓰인다고 가정했습니다. Piper와 CitC에 관한 설명은 2016년 논문과 2020년 서적을, Scion에 관한 설명은 2026년 공개 자료를 참고했습니다. 따라서 위 표는 **서로 다른 시점에 공개된 설계**를 비교한 것입니다. [1](https://www.anthropic.com/research/redesigning-source-control)[2](https://abseil.io/resources/swe-book/html/ch16.html)[3](https://research.google/pubs/why-google-stores-billions-of-lines-of-code-in-a-single-repository/)[4](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)

### 3.2. Piper도 오래전부터 대규모 자동화 작업을 지원해 왔습니다

Piper와 Scion의 차이를 이해하려면 자동화 작업의 유무보다 **어떤 작업을 얼마나 자주 실행하는지**를 살펴보아야 합니다. 2016년 Piper 논문에 따르면 당시 일반적인 근무일에 사람이 만든 commit은 약 16,000건, 자동화 시스템이 만든 commit은 약 24,000건이었습니다. Piper 역시 대규모 자동화 작업을 처리해 온 시스템입니다. [3](https://research.google/pubs/why-google-stores-billions-of-lines-of-code-in-a-single-repository/)

Google의 공개 문서에서는 개발자들이 작은 변경을 trunk에 자주 병합하는 **trunk 중심 개발**을 설명합니다. 여기서 trunk는 일반적인 Git 개발 환경의 main에 해당하는 기준 브랜치입니다. 배포한 버전을 따로 관리할 때에는 release 브랜치를 사용하며, 코드 변경을 반영하기 전에는 리뷰와 담당자의 승인을 받습니다. [2](https://abseil.io/resources/swe-book/html/ch16.html)

반면 Scion은, 항상 온라인 상태인 자동화 도구가 조회 및 반복적인 체크아웃 등을 할 때에 드는 비용에 주목합니다. [1](https://www.anthropic.com/research/redesigning-source-control) 두 시스템을 비교하려면 commit 건수와 함께 **작업의 실행 시간, 필요한 조회, 데이터의 재사용 정도**를 살펴보아야 합니다.

## 4. Scion의 성능 수치는 어떻게 읽어야 하는가

Anthropic은 Scion으로 전환한 뒤 CPU와 메모리 요구량이 **기존 Git 미러 인프라의 약 1/200**로 줄었으며, CI의 CPU 가용 용량은 **25% 증가**했다고 보고했습니다. 이 수치의 비교 대상은 Anthropic이 이전에 운영하던 Git 미러 인프라입니다. [1](https://www.anthropic.com/research/redesigning-source-control)

다른 팀이 같은 효과를 얻을지는 그 팀의 작업 방식에 따라 달라집니다. Scion과 Git 또는 Piper의 성능을 직접 비교하려면 같은 작업을 실행하고, 캐시에 데이터가 이미 있는지 등의 조건도 맞추어야 합니다. 그 상태에서 작업 준비에 걸리는 시간과 자원 사용량, 서비스의 신뢰성을 측정해야 타당한 비교가 됩니다.

## 5. 코드 변경을 병합한 뒤에도 테스트해야 하는 이유

모든 코드 변경을 main에 병합하기 전에 하나씩 순서대로 검사한다고 해 보겠습니다. 뒤의 변경은 앞선 변경의 검사가 끝날 때까지 기다려야 하므로, 변경이 빠르게 쌓이면 병합 대기열이 길어질 수 있습니다. Anthropic은 저장소 전체의 병합을 잠금으로 통제하는 방식을 유지하기 어려웠다고 설명하며, **병합 후와 배포 전의 테스트**를 강조했습니다. [1](https://www.anthropic.com/research/redesigning-source-control)

같은 기준 코드에서 출발한 변경 A와 B를 생각해 보겠습니다. A는 아직 쓰이지 않는 함수를 삭제하고, B는 그 함수를 호출하는 코드를 추가합니다. 두 변경을 기준 코드에 각각 적용해 테스트하면 모두 통과할 수 있지만, 둘을 병합하면 삭제한 함수를 호출하는 문제가 생깁니다.

버전 관리 시스템이 두 변경을 정확히 기록하더라도 합쳐진 프로그램의 동작까지 보장하지는 않습니다. 따라서 **병합 결과를 테스트하고, 검증한 버전만 배포하는 절차**가 필요합니다.

## 6. Git을 쓰면서도 시도해 볼만한 것들

Scion의 설계로부터 배울 수 있는 교훈들을 자신의 팀에 적용해 보려면, 먼저 개발 과정의 어느 단계에서 시간을 많이 쓰는지 측정해야 합니다. **코드를 받는 시간, 컴파일과 테스트에 걸리는 시간, 리뷰를 기다리는 시간**을 나누어 재면 개선할 대상을 찾을 수 있습니다.

그중 코드를 준비하는 비용이 크다면 Git의 다음 기능부터 검토할 수 있습니다. 각 기능이 줄이는 데이터의 범위는 서로 다릅니다. [5](https://git-scm.com/docs/partial-clone)[6](https://git-scm.com/docs/git-sparse-checkout)

- **Partial clone**은 처음부터 모든 객체를 받지 않고, 빠진 객체는 필요할 때 가져오는 방식입니다.

- **Shallow clone**은 최근 일부 commit만 받는 것처럼 가져올 변경 이력의 범위를 제한하는 방식입니다.

- **Sparse checkout**은 작업 디렉터리에 펼쳐 놓을 경로를 고르는 방식입니다. 이 설정만으로 변경 이력의 다운로드까지 줄어들지는 않습니다.

Anthropic도 Git의 이러한 기능들과 미러를 사용했습니다. 그러다가 Scion을 개발했습니다. Scion은 Anthropic의 사내 도구들과 함께 쓰도록 만들어졌습니다. 따라서 다른 팀이 Scion으로 전환하려면, 리뷰 도구와 코드 검색, CI가 새 저장소와 어떻게 연동될지도 함께 검토해야 합니다. 일반적인 팀에서는 기존 도구를 사용하면서 **준비 작업을 반복하는 횟수와 데이터를 전송하는 양을 줄이는 것**부터 시작해 볼 수 있습니다. [1](https://www.anthropic.com/research/redesigning-source-control)

## 참고자료

- [1] [Anthropic의 Scion 설계 설명](https://www.anthropic.com/research/redesigning-source-control)  2026년 10월 발표

- [2] [Software Engineering at Google  Chapter 16](https://abseil.io/resources/swe-book/html/ch16.html)  버전 관리와 브랜치 운영

- [3] [Google의 모노레포와 Piper 논문](https://research.google/pubs/why-google-stores-billions-of-lines-of-code-in-a-single-repository/)  Potvin과 Levenberg, 2016년

- [4] [Pro Git  What is Git](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)  로컬 연산과 스냅샷

- [5] [Git  Partial clone](https://git-scm.com/docs/partial-clone)  객체 다운로드와 이력 제한

- [6] [Git  Sparse checkout](https://git-scm.com/docs/git-sparse-checkout)  작업 디렉터리에 펼칠 경로 선택

- [7] [Version Control with Subversion  Version Control Basics](https://svnbook.red-bean.com/en/1.7/svn.basic.version-control-basics.html)  서버와 작업 복사본

- [8] [Version Control with Subversion  Sparse Directories](https://svnbook.red-bean.com/en/1.7/svn.advanced.sparsedirs.html)  SVN의 부분 체크아웃

- [9] [Pro Git  About Version Control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)  중앙집중식과 분산 구조
