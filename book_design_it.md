# 책 '개발자에서 아키텍트로'를 내가 번역한다면

나는

- 소프트웨어 설계에 너무 많은 시간을 쓰는 걸 좋아하지 않고

- 설계 문서의 포맷은 미니멀한 걸 좋아하고

- 조직에 소프트웨어 아키텍트라는 포지션이나 역할이 따로 있는 것을 별로 좋아하지 않고

- 사람들 모여서 무슨 카드같은 거 가지고 요란뻑적지근하게 무슨 액티비티같은 거 하는 것도, 한다면야 굳이 말리진 않지만 내가 일부러 하는 경우는 많지 않다.



그런데 이 책 '개발자에서 아키텍트로'(원서 제목은 "Design it! From Programmer to Software Architect")는 꽤 유용할 것 같다고 느꼈다. 왜냐하면

- 여러 가지 템플릿, 액티비티, 간단한 프로세스 등이 많이 소개되어있어서, 필요할 때 적당한 걸 찾아 쓰기 좋다. 이 책은 툴박스 역할을 해 줄 것 같다.

- 지나치게 현학적이지 않고 실용적인 편인 것 같다.

- 비교적 최근의 소프트웨어 아키텍처 관련 이야기들을 잘 모아 놓은 것 같다.

- 비교적 읽기 쉬운 편이다.



그런데 문제는... 번역이 이해하기 어렵게 되어 있는 부분이 많다는 것이다. 물론 번역하신 분이 이걸 완벽하게 하시느라 무한히 시간을 쓰실 수는 없으셨을테니, 이해한다. 번역이 워낙 힘든 일이기도 하고. 원저자의 영어 문장 중에도 (공돌이들이 쓴 책들이 종종 그렇듯) 애매하거나 이해하기 어려운 것들이 있었고.

 

그래도, 나중에 다시 읽을 때 도움이 되도록, 그리고 이 책을 보시게 될 다른 분들께도 도움이 되도록, 이해가 어려운 부분을 고쳐보았다.



아래에서 사용한 페이지 번호들은 알라딘 전자책 기준으로 되어 있다.



◆ p35 "시스템은 분리하고 책임은 위임하기"

-> 원문은 "Partition the System and Assign Responsibilities". 다시 번역하면 "시스템을 여러 부분으로 나누고 책임을 할당하기"



◆ p35 "시스템을 나누는 작업은 의미 있는 게 아닙니다."

-> 원문은 "Partitioning a system is important not just because it lets you develop a strategy for achieving quality attributes."

다시 번역하면 "시스템을 쪼개는 것은, 품질 속성들을 달성하기 위한 전략을 수립하는 것을 용이하게 해 줄 뿐 아니라, 다른 중요한 좋은 것들을 가져다 줍니다."



◆ p36 "이상과 현실 사이에 균형을" -> "이상과 현실 사이에서 균형을" 이 나을 것 같음



◆ p37 "품질/속성" -> 빗금이 없어야 함



◆ p39 "종이와 펜으로만 ... 선택해 설계할 수 있습니다."

-> 원문은 "It’s easy to design an architecture on paper with no bearing on reality. To avoid this trap, you’ll build architectures using three types of elements and relations."

다시 번역하면 "종이 위에 그냥 설계를 하다 보면 현실적이지 못한 설계가 되기 쉽습니다. 이러한 일을 방지하기 위해, 세 가지 타입의 요소들 및 관계들을 사용해서 설계를 합니다."



◆ p39 "동일한 타입 안에서 요소와 관계를 결합합니다."

-> "동일한 타입에 속하는 요소들과 관계들을 적절히 결합합니다"



◆ p42 "독창적으로" -> "다른 소프트웨어들과 구별되게"



◆ p44 "'소프트웨어 아키텍트'는 단순한 역할 중 하나가 아니라"

-> "'소프트웨어 아키텍트는' 하나의 역할일 뿐만 아니라"



◆ p49 "촉각의 원칙"

-> 원문은 "tangibility rule". 이 책에서 tangible이란 말을 "누구나 쉽게 액세스하고 이해할 수 있도록 어떠한 구체적인 형태로 표현되어 있음" 정도의 뜻으로 쓰는 것 같으므로, 차라리 "표현의 원칙" 이나 "구체성의 원칙" 등으로 번역하는 게 어떨까 한다.



◆ p49 (그리고 p51) "손에 잡히는 디자인이 대화를 이끌어낸다"

-> "설계를 누구나 쉽게 액세스하고 이해할 수 있도록 어떠한 구체적인 형태로 표현해 두어, 커뮤니케이션을 촉발한다."



◆ p51 "코드는 읽기 어렵고, ... 토론하기 어렵습니다."

-> "코드는 읽기 어렵고, 코드만 가지고는 ... 토론하기 어렵습니다."



◆ p52 "시스템 흐름의 일부를 직접 동작해보세요."

-> "시스템 제어 흐름의 일부를 직접 동작으로 보여 주세요."



◆ p52 "디자인 마인드셋"

-> 여기서부터 원저자는 mindset이란 말을 계속 쓰고 있다. 디자인을 위한 네 가지 마인드셋으로 understand 마인드셋, explore 마인드셋, make 마인드셋, evaluate 마인드셋이 있다 한다. 그런데 내 개인적 의견은, 저자가 괜히 마인드셋이란 개념을 굳이 써서 그게 여기서 무슨 뜻으로 쓰이는지 고민하게 만드는 것 같다. 마인드셋은 원래 사고 방식 아닌가. 뭔가 살짝 이상하다. 나라면 차라리 '모드'라고 할 것 같다.



◆ p52 에서부터 "훈련"이라는 말이 계속 나오는데, 이는 원문의 "practice"를 잘못 번역한 것으로 보인다. 여기서는 이 말이 "구체적 실천 방안" 정도의 뜻으로 쓰인 것 같다. 마치 "best practice"에서처럼.



◆ p63 "결박된 합리성"

-> 원문은 "bounded rationality". 다음과 같이 쓰였다. "Herbert Simon coined the term bounded rationality to describe the theoretical barrier created by limits in time, money, skills, and knowledge that make rational design challenging for complex problems such as software architecture."

번역으로는 "제한된 합리성" 정도가 어떨까?



◆ p63의 "만족스럽게", p64의 "만족감", "만족스러운"

-> 이런 어휘를 쓰니 마치 사람에게 만족감을 준다는 듯한 뉘앙스가 느껴진다. 본문의 satisfying을 번역한 것인데, 여기선 "주어진 조건들을 충족시키는"의 뉘앙스가 풍기도록 해야 더 어울리지 않을까? "요건을 만족시키는" 정도로 번역하면 어떨까?



◆ p66 "설계를 얼마나 우선해야 하는가"

-> "설계에 얼마나 시간을 투자해야 하는가" 가 더 낫지 않을까?



◆ p71 "위험이 발생할 시간 없애기"

-> 원문은 "Push out the time frame of the risk". 이것은 "위험이 발생할 수 있는 시기를 늦추기"란 뜻 아닌가?



◆ p72 "아래처럼 위험 구문으로 조건과 결과를 표로 만들어봤습니다."

-> 원문은 "Compare our <Condition>; might <Consequence> risk with these other, less effective risk statements:"

이것은 정말 잘못 번역되었다. 원문에서는 이 문장보다 이전에 보여준 <Condition>; might <Consequence> 형식의 리스크 표현 방식을 이 문장 다음에 나오는 다른 형식의 리스크 표현 방식들과 비교하며 전자의 우수성을 강조하였다. 번역판에선 그것이 드러나지 않는다. 따라서 번역판에서 이 문장은 "우리가 만든 <조건> - <결과> 형태의 위험 문구에 비하면, 아래 표에 있는 위험 문구들은 별로 효과적이지 않음을 알 수 있습니다." 처럼 번역돼야 한다.



◆ p72의 표에 있는 "위험 구문" -> "안 좋은 위험 문구"



◆ p72의 표에 있는 "왜 위험한가" -> "왜 안 좋은가"



◆ p72 "별문제 없어 보이는군요." -> 이 문장이 있으면 독자가 위의 표에 나오는 것들이 별 문제 없는 뜻이라 오해를 할 수 있음(번역하신 분은 저자가 뷰리토 리스크가 별로 중요한 리스크가 아니라고 말한다고 오해를 하시고 이 문장을 쓰신 것 같음). 그러므로 이 문장은 제거해야 함.



◆ p85 "다음은 일반적인 비즈니스 목표를 정리한 표입니다."

-> 원문은 "Here’s a summary of common business goal categories:" 이다. 그 다음에 나오는 표에는 구체적인 비즈니스 목표들의 예가 아니라 비즈니스 목표들의 종류(카테고리)들이 나온다. 그러므로 이 문장은 "다음은 자주 보이는 비즈니스 목표들의 유형들을 정리한 표입니다." 정도가 되어야 할 것 같다.

표에 나오는 것들은 일반적이고 추상적인 것들인데, 잠시 후 원저자는 비즈니스 목표가 구체적이고 측정 가능해야 한다고 주장한다. 그러므로 표에 나오는 것들을 그냥 '비즈니스 목표'라 하면 모순이 발생한다.



◆ p87의 mad lib 예제 문장에서 "고 싶어" 및 "기 때문"에는 밑줄을 긋지 않는 게 나을 것 같다. 아니, 더 나아가서 "XXX은(는) YYY를 원한다. 왜냐하면 ZZZ기 때문이다." (XXX, YYY, ZZZ에만 밑줄) 와 같은 형태로 바꾸면 좋겠다.



◆ p93 "품질 속성은 기능 요구사항이 아닌가요?"

-> 원문은 "Are Quality Attributes Non-functional Requirements?" 임. 이것은 "품질 속성은 비기능 요구사항인가요?" 라고 번역되어야 함.



◆ p98 "5.3 기능 요구사항 찾아내기"

-> 소챕터 제목이 잘못되었다. 이 소챕터에선 기능 요구사항을 다 찾아내라는 얘기를 하는 게 아니고, *영향력 있는* 기능 요구사항들을 뽑아내라는 얘기를 하고 있다. 그러므로 소챕터 제목은 "영향력 있는 기능 요구사항 뽑아내기" 또는 "기능 요구사항의 종류를 분간하기" 정도가 되어야 한다.



◆ p98 "기능 중 하나라도 소화하지 못하면"

-> 앞에 "이들"을 삽입해서, 여기의 "기능"이 전술한 아키텍처 킬러 기능들을 말하는 것임을 분명히 해야 함.



◆ p98 "비슷한 문제끼리 묶은 후 일반적인 요구사항을 분류합니다."

-> 원문은 "Identify general classes of requirements that represent the same type of architectural problem."이다. 이것은 "요구 사항들 중 공통된 설계상 문제와 관련된 것들을 하나의 클래스로 묶습니다." 처럼 번역돼야 한다.



◆ p98 "앞서 작성해본 아키텍처로 해결 가능한지 ... 미칠 가능성이 높습니다."

-> 원문은 "For each problem class identified, walk through the notional architecture and show how to achieve each requirement group. If it is not immediately obvious how you would implement the feature based on the known coarse-grained requirements, it might have architectural significance."

다시 번역해 보면 "앞에서 찾아낸 요구사항 클래스들 각각에 대해, 앞서 작성해 본 아키텍처가 그 클래스의 문제를 해결할 수 있는지 확인합니다. 그 큰 덩어리로 묶여 있는 요구사항들을 위한 기능을 어떻게 구현할지 생각해 보세요. 만약 구현 방법이 즉시 명확히 떠오르지 않는다면, 그 기능은 아키텍처 설계에 중요한 영향을 미치는 것일 수 있습니다."



◆ p98 "두 번째 단계는"

-> 앞에 "위의"를 삽입해 주어서, 다른 얘기로 넘어가는 게 아니라 앞에서 말한 단계 2에 대한 설명을 하는 것임을 확실히 해야 함.



◆ p99-100 "이 간단한 계산기의 예에서 ... 이목을 집중시키는 일입니다."

-> 읽기가 매우매우 어려움. 원문은 다음과 같다.

"In our simple calculator example, we can reduce any mathematical operation to the same general problem. To solve the newly requested history feature, we need remote storage. This one feature takes the architecture in a new direction that other functional requirements did not.

Reference any influential functional requirements in your architecture documentation but avoid duplicating the requirements engineering effort. Our goal is to call attention to critical features that influence our decision making."

다시 번역해 보면 다음과 같다.

"이 간단한 계산기 예제에서, 산술 계산 기능은 모두 하나의 일반적인 문제로 귀결시킬 수 있습니다. 그런데 새로이 요청받은 '기록' 기능을 만들려면, 원격 스토리지가 필요합니다. 이 하나의 기능은, 다른 기능 요구사항들과는 달리 아키텍처를 새로운 방향으로 이끌고 갑니다.

아키텍처 문서에서는 영향력 있는 기능 요구사항들을 모두 언급해야 합니다. 하지만 요구사항 엔지니어링을 다시 하지는 않도록 하세요. 우리의 목표는 의사결정에 영향을 미치는 중요한 기능들에 주의를 기울이는 것입니다."



◆ p101 "아키텍처가 항상 최신 기술 동향을 ... 좋은 포장만 씌운 경우가 많습니다."

-> 원문은 "Architecture always seems to follow hot technology trends. As new hardware, software, and design paradigms emerge, some will permanently alter the software engineering landscape. Others might just be marketing veneer on old ideas."

다시 번역하면

"아키텍처는 항상 최신 기술 동항을 따르는 듯 보입니다. 새로운 하드웨어, 소프트웨어, 설계 패러다임이 등장하며, 그들 중 어떤 것들은 소프트웨어 엔지니어링의 지형을 영원히 바꿔놓을 것입니다. 하지만 다른 것들은 그저 오래된 아이디어들에 마케팅을 위한 좋은 포장만 씌운 것들일 수 있습니다."



◆ p107 "6.1 대안을 위한 분기, 결정을 위한 융합"

-> 원문은 "Diverge to See Options, Converge to Decide".

이것은 "가능한 옵션들을 찾기 위한 발산, 결정을 하기 위한 수렴"으로 번역하면 어떨까?



◆ p108 "인간의 뇌는 선택을 갈망합니다."

-> 원문은 "Human brains crave options."

"인간의 뇌는 선택지들을 더 찾고 싶어 합니다." 가 어떨지?



◆ p110 "해당 인스턴스에 새 버전을 배포하면 기존 인스턴스와 교체합니다."

-> 원문은 "deploys the new version into those instances, and then switches to use the new instances."이다.

다시 번역하면

"그 인스턴스들에 새 버전을 배포하고, 그러고 나서 이 새 인스턴스들을 사용하도록 스위칭을 합니다."



◆ p110 "불일치"

-> 그냥 '문제'라고 하면 더 나을 듯 하다.



◆ p110 "예를 들어 서비스 A가 ... 서비스 C에 의존합니다."

-> 문장을 어색하게 나눈 것 같고 문장 하나는 빠져 있음. 원문은 "For example, suppose you have a chain of services—Service A depends on Service B, which in turn depends on Service C. Now one of your developers deploys a new version of Service B."

다시 번역하면

"예를 들어, 서비스 A가 서비스 B에 의존하고, 서비스 B는 서비스 C에 의존하는, 서비스들의 체인이 있다고 가정해봅시다. 그런데 개발자가 서비스 B의 새로운 버전을 디플로이하려 합니다."



◆ p110 "인터페이스 이름이나 형태를"

-> 원문은 "the syntax or semantics of the interface".

이것은 "인터페이스의 형태 또는 사용 방법을"이라고 번역하면 좋을 것 같다.



◆ p110 "서비스 B는 서비스 C가 새 버전이라고"

-> 앞에 "또한"과 같은 말을 삽입하면 좋겠다.



◆ p110 "롤링 업그레이드를 ... 동시에 실행할 수 있습니다."

-> 우선 문단을 바꾸지 말고 앞 문단에 붙이면 좋겠고, 번역은 다음과 같이 바꿔야 할 것 같다.

"한편, 롤링 업그레이드를 사용하면 인터페이스가 다른 두 버전의 서비스 B들이 동시에 실행되고 있을 수 있습니다."



◆ p110 "암묵적으로"

-> "적절히"



◆ p115 "각 요소마다 메시지를 만들고 ... 구독할 수 있습니다."

-> "각 요소들은 이벤트 버스에다가 메시지를 발행합니다. 특정 타입의 메시지에 관심이 있는 컴포넌트는 그 메시지 타입들을 구독할 수 있습니다."



◆ p121에는 "책임감"이라는 말이 여러 번 나오는데, 이것을 모두 그냥 "책임"으로 바꾸면 좋겠다.



◆ p121-122의 소챕터 "6.6 결정은 미룰 수 있을 때까지 미룬다"는, 제목과 본문 상당 부분이 잘못 번역된 것 같다.

우선 제목을 "결정은 가장 책임이 큰 순간까지 미룬다"로 바꿔야 한다.

그리고 원문에는 the most responsible moment라는 개념이 소개돤 블로그 글이 각주로 링크되어 있는데 번역본에는 그게 없다. 이 블로그 글을 대충이라도 보면 이해에 도움이 된다. 글로의 링크는 http://wirfs-brock.com/blog/2011/01/18/agile-architecture-myths-2-architecture-decisions-should-be-made-at-the-last-responsible-moment/ 이다.

또한 "이 책에서는 ... 미치는 때를 의미합니다."는 다시 번역하면 "우리는 책임있는 최후의 순간에 대해 생각하기보다는, '가장 책임이 큰 순간(the most responsible moment)'에 설계에 대한 의사 결정을 하기를 원합니다. 가장 책임이 큰 순간이란, 설계에 대한 어떤 의사 결정이 소프트웨어 시스템에 좋은 영향을 가장 크게 미칠 순간을 말합니다."

그 다음 문단은 잘 이해가 되지 않는다 (마지막 문장은 문제 없으니 제외하고). 일단 내가 이해한 바에 따라 다시 번역해보면

"이상적으로는, 책임있는 최후의 순간이 곧 의사결정을 위한 가장 책임이 큰 순간이어야 할 것입니다. 하지만 실제로는, 가장 책임이 큰 순간 뒤에 다른 일들을 할 시간이 좀 남습니다. 우리가 컨트롤할 수 없는 외부 디펜던시, 합의 이루기, 교육, 그리고 설계 검증 등의 일 말입니다."



◆ p122 "의사결정을 하기 좋은 ... 의사결정하는 방법입니다."

-> 원문은 "Even if we can identify the most responsible moment to decide, that doesn’t mean we’ll always have enough information to make a good decision. Luckily we have a cheat to help us avoid catastrophes when this situation arises. We can move things likely to change out of the architecture."

다시 번역하면 "의사결정을 위한 가장 책임이 큰 순간을 찾아낼 수 있더라도, 좋은 의사결정을 내리기에 충분한 정보를 가지고 있지는 못할 수도 있습니다. 그런 경우에도 파국을 피하는 묘수가 있습니다. 나중에 바뀔 수도 있는 것들은, 아키텍처 밖으로 옮겨 버리는 것입니다."

여기까지 생각하고 보니, '책임있는 최후의 순간'은 '최후 책임 시점', '가장 책임이 큰 순간'은 '최대 책임 시점'으로 모두 바꾸면 좋겠다.



◆ p122 "6.6.1 아키텍처에 영향을 주지 않게 의사결정하기"

-> "설계를 위한 의사결정을 아키텍처 밖으로 밀어내기"

그 아래의 두 문장을 다시 번역하면

"나중에 쉽게 바꿀 수 있는 것에 대한 의사결정이라면, 아키텍처 측면에서 걱정거리가 아닐 것입니다. 그러므로, 아키텍처를 설계할 때에는 가능하면, 나중에 바뀔 법한 의사결정은 상세 설계를 하는 사람들(downstream designer)에게 맡길 수 있도록 설계해 보세요."



◆ p125 "추가 가능한pluggable 아키텍처, 환경변수 설정, 자기 기술적self-describing 데이터, 동적 탐색 등"

-> "구성 요소를 끼워넣을 수 있는(pluggable) 아키텍처, 외부에서 각종 설정을 하는 기능, 자기 기술적(self-describing) 데이터, 동적 디스커버리 등,"



◆ p145 "아키텍처를 설계하고 고치는 일은 ... 바로 알아챌 수 있습니다."

-> 대충 무슨 뜻인지 짐작은 할 수 있는데, 읽기가 어려움. 원문은 다음과 같다.

"We know that architecture flaws are cheaper and faster to fix while we’re still designing architecture than when we’re writing code, running acceptance tests, or (gasp!) reviewing customer complaints after release. Gregor knows that an architecture problem is much faster to fix while it’s on a whiteboard than captured in thousands of lines of code.

Writing code is a fantastic way to learn about the system and how to design it."

다시 번역해 보면

"우리 모두 알고 있듯이, 아키텍처상의 결함은 우리가 아직 아키텍처를 설계하고 있을 때 고쳐야 값싸고 빠르게 고칠 수 있습니다. 코드를 작성할 때나, 억셉턴스 테스트를 할 때나, 심지어 릴리스를 하고 나서 고객들의 불만(더헉!)을 검토하고 있을 때에는, 아키텍처를 수정하는 것이 비싸고 어렵습니다. 아키텍처 문제는 수천 줄의 코드 안에 녹아들었을 때보다 화이트보드에 있을 때 훨씬 빨리 고칠 수 있다는 걸, 그레거는 잘 압니다.

그런데 한편으론, 코드를 작성하는 것은 시스템에 대해 파악하고 그것을 어떻게 설계할지를 배울 수 있는 매우 좋은 방법입니다."

정도가 좋겠다.



◆ p145 "소프트웨어 시스템의 아키텍처 메타모델... 규칙을 의미합니다"

-> 이해하기 어려움. 원문은 "A software system’s architectural meta-model defines the concepts used in a model and the rules for how those concepts are applied." 임. 다시 번역해보면

"소프트웨어 시스템의 아키텍처 메타모델이란, 모델에서 쓰이는 개념들 및 그 개념들을 적용하는 규칙들을 정의한 것입니다."



◆ p147 "이 질문으로 간단한 테스트를 만들 수 있습니다."

-> "이 질문이 곧, 우리가 테스트를 해야 할 것입니다."



◆ p147 "테스트를 거치면서 ... 파악할 수 있습니다."

-> "테스트를 통해, 우리는 이 모델 안에서 질문의 답을 찾게 되거나 또는 우리의 이해와 현실 간에 차이가 있음을 알게 됩니다."



◆ p147 "답을 찾으면 ... 생각할 수 있습니다."

-> "답을 찾았다면 기존의 모델에 대한 믿음이 더 강화될 것이고, 차이가 있었다면 모델을 어떻게 바꿔야 그 차이가 메워질지를 생각해 내야 할 것입니다."



◆ p147 "하지만 우리는 비용을" -> "하지만 우리는 비용도"



◆ p147 "비정상 상태일 때 가장 많은 비용을 내야 하는가 " -> "가용하지 않게 될 때 가장 많은 비용이 드는가"



◆ p155 "요소 간 관계 제어하기"

-> 원문은 "Enforce Relations Among Elements". 다시 번역하면 "요소들 간의 관계가 설계를 위반하지 못하도록 강제하라"

이 소챕터에 나오는 "제어"를 모두 "강제"로 바꿔야 함.



◆ p155 "유지하기 위해 규칙과 주의 사항을 잔뜩 만드는 경우가 있습니다."

-> "유지하는 방법이 규칙과 주의 사항에 의존하는 것 뿐이라는 점이 있습니다."



◆ p155 "코드로 꽉 짜인 설계는"

-> "설계상의 의사결정들이 코드에 의해 강제되면 이들을"



◆ p155 "모듈 구조는 코드로 읽기엔 ... 문서를 작성하곤 합니다"

이해하기 어려운 번역. 원문은 "Module structures are the simplest to see in the code but often the most difficult to enforce. In most modern programming languages, we can enforce an allowed to use relation by limiting access to specific modules. If that fails, it’s usually possible to distribute modules as a library with decent documentation."

다시 번역해 보면 "모듈 구조는 코드 상에서 가장 쉽게 볼 수 있지만, 강제하기는 가장 어려운 구조일 때가 많다. 현대의 프로그래밍 언어들 대다수는 모듈들에 대한 액세스를 제한하는 방식으로 '사용할 수 있음' 관계를 강제할 수 있다. 그게 안 되는 경우라면, 보통 모듈을 잘 작성된 문서와 함께 라이브러리 형태로 배포할 수 있다."



◆ p156 "할당 구조에서 코드로 의도를 표현하기란 매우 어렵슺니다."

-> "할당 구조에 들어 있는 의도를 코드로 표현하는 것은 예전엔 매우 어려운 일이었습니다."



◆ p156 "서비스형 플랫폼 ... 제어할 수 없습니다."

-> 이 부분은 원문이 잘못되지 않았나 의심된다. 원문은 "It is not possible to describe and enforce allocation models in the code thanks to the rise of technologies and paradigms such as platform-as-a-service, container technologies (for example, Docker), infrastructure as code, and distributed version control systems." 처럼 되어 있다. 그런데 문맥상 "possible"이 "impossible"로 바뀌어야 맞지 않나 싶다. 그렇다면 번역본의 이 문장은 "강제하는 것이 불가능하진 않습니다"로 끝나야 할 것이다.



◆ p156 "인프라를 코드로 처리하면"

-> "인프라스트럭처를 코드처럼 다룰 수 있게 되면"



◆ p184 "서로 맞붙이기에 유용한 두 가지 뷰로"

-> "두 가지의 유용한 매핑 뷰로"



◆ p184 "업무 할당 뷰에서는 ... 볼 수 있습니다."

-> 원문은 "In a work assignment view, we show who works on different parts of the system by mapping teams with the elements they’ll build. Deployment views show where runtime elements from a component and connector view will be installed and used."

다시 번역하면 "업무 할당 뷰는 팀들과 그들이 만드는 요소들을 매핑하여 누가 시스템의 어떤 부분을 만드는지를 보여줍니다. 배포 뷰는 '컴포넌트와 커넥터' 뷰의 런타임 요소들이 어디에서 설치되고 쓰일지를 보여줍니다."



◆ p184 "목표는 단지 ... 초점이 있어야 합니다."

-> 원문은 "Our objective is to communicate design decisions by any means necessary."

다시 번역하면 "우리의 목표는 설계상의 의사결정들을 커뮤니케이션하는 것입니다."



◆ p184 "매핑 뷰는 이해관계자 간의 ... 완벽하게 부합합니다."

-> "매핑은 서로 다른 관심사를 가진 이해관계자들을 연결해 줍니다. 업무 할당 뷰는 스케줄이나 충원 계획을 만드는 프로젝트 마니저의 니즈에 완벽하게 부합합니다."



◆ p185 "제품 관리자가 요구한 기능의 ... 공감대가 만들어졌습니다."

-> 원문은 "This tiny smidge of knowledge enables team self-organization and helps developers prioritize work with the product manager’s needs in mind. Now you’re empathizing with stakeholders!"

다시 번역하면 "이런 작은 지식들 덕분에, 팀이 스스로 구조를 만들게 되기도 하고, 개발자들이 제품 관리자의 요구를 고려해서 일의 우선순위를 정하는 게 용이해지기도 합니다. 이제 이해관계자들이 공감을 하게 되었어요!"



◆ p337 "모듈식 분해 다이어그램"

-> "모듈 분해 다이어그램"



(마치며: *연상이 돼서 잠깐 언급하면, 엔지니어링 디자인에 대한 나의 아주 어줍잖고 개인적인 이론은 '디자인은 인터페이스를 정의하는 게 거의 전부'라는 거다.*

*내가 디자인하는 방식은 이렇다. 디자인의 첫 단계에는, 생각할 수 있는 아주 큰 element들만 그린다. 예를 들어, 내가 만들려는 시스템 전체가 하나의 element, 사용자(사람일수도 기계일수도)가 하나의 element, 그 밖의 큼직한 외부 dependency들이 각각 하나씩의 element가 되는 정도로.*

*다음 단계로, 각 element들의 역할과 인터페이스를 정의한다. 보통, 역할을 묘사하는 건 별 거 아니고 인터페이스를 묘사하는 데 시간이 많이 걸린다. 여기서 내가 말하는 인터페이스란, API 같은 것만 말하는 게 아니라, 그 element와 외부와의 인터랙션이 어떻게 일어나야 하는지를 총체적으로 정의하는 것이다. 나는 이 '인터페이스 정의'에 각종 퀄리티 어트리뷰트들과 제약 조건들을 포함시킬 뿐만 아니라 대부분의 기능적 요구사항들도 포함시킨다. 아직 각 element의 내부 구조나 동작 원리는 묘사하지 않는다.*

*이제 다음 단계로, 그려놓은 블록들 중 내가 만들 시스템을 몇 개의 큰 하위 element들로 나눈다. 그리고 또 각 element의 역할과 인터페이스를 설계한다.*

*이와 같은 방식으로, 점점 구체적인 레벨의 element들로 내려가며 그것들의 외부와의 인터페이스를 정의한다. 그런데 별로 깊은 depth까지 들어가진 않는다. 클래스 레벨이나 파일 레벨의 설계는, 복잡한 경우 간혹 설계 문서에 기술하기도 하지만, 보통은 그냥 코드로 한다.*)
