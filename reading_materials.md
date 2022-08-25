[Edward Jee](https://kr.linkedin.com/in/edward-jee-480225a?trk=pulse-article_main-author-card)'s favorite reading materials

# Table of Contents

1. [Documentation](#documentation)
1. [Machine learning](#machine-learning)
1. [Basic math](#basic-math)
1. [Coding style](#coding-style)
1. [Software design and programming](#software-design-and-programming)
1. [Algorithms](#algorithms)
1. [Computer architecture](#computer-architecture)
1. [Gotbolt - Compiler Explorer](#godbolt---compiler-explorer)
1. [Performance optimization](#performance-optimization)
1. [Programming tips and techniques](#programming-tips-and-techniques)
1. [Web application development](#web-application-development)
1. [Distributed systems and data engineering](#distributed-systems-and-data-engineering)
1. [C++](#c)
1. [Java](#java)
1. [Open source projects](#open-source-projects)
1. [Tools](#tools)
1. [Productivity](#productivity)
1. [Engineering management](#engineering-management)
1. [Product management](#product-management)
    1. [How to write a PRD](#how-to-write-a-prd)
1. [OKR](#okr)
1. [Hiring](#hiring)
1. [Decision making](#decision-making)
1. [Miscellaneous articles](#miscellaneous-articles)

# Documentation

* [Design Docs at Google](https://www.industrialempathy.com/posts/design-docs-at-google/) ([cached](attachments/Design%20Docs%20at%20Google.pdf))
* [A Quora answer about how Google documents and reviews engineering designs](https://www.quora.com/How-do-teams-in-big-companies-like-Facebook-do-feature-designs-and-design-reviews/answer/J%C3%A9r%C3%B4me-Cukier) ([cached](attachments/J%C3%A9r%C3%B4me%20Cukier%27s%20answer%20to%20How%20do%20teams%20in%20big%20companies%20like%20Facebook%20do%20feature%20designs%20and%20design%20reviews_%20-%20Quora.pdf))
* [How do I write engineering design docs in Google: an example](https://luanjunyi.medium.com/how-do-i-write-engineering-design-docs-in-google-an-example-f19febe0297c) ([cached](attachments/How%20do%20I%20write%20engineering%20design%20docs%20in%20Google%20_%20Medium.pdf))
* "[Design docs](https://abseil.io/resources/swe-book/html/ch10.html#design_docs)" section (p.195) in chapter 10 of [Software Engineering at Google](https://abseil.io/resources/swe-book)

[\[top\]](#table-of-contents)

# Machine learning

* [Making Friends with Machine Learning](https://towardsdatascience.com/making-friends-with-machine-learning-5e28d5205a29) - Cassie Kozyrkov
* [Pattern Recognition and Machine Learning](http://research.microsoft.com/en-us/um/people/cmbishop/#prml-book) - Christopher M. Bishop (Summaries in a Korean blog: [link](http://norman3.github.io/prml/) / 한글 번역판: [link](https://jpub.tistory.com/835))
* [Hidden Technical Debt in Machine Learning Systems](https://papers.nips.cc/paper/2015/hash/86df7dcfd896fcaf2674f757a2463eba-Abstract.html) (Summary in Korean: [link](https://norman3.github.io/papers/docs/hidden_technical_debt))
* Deep learning
    * [쉽게 풀어쓴 딥러닝의 거의 모든 것](http://t-robotics.blogspot.com/2015/05/deep-learning.html)
    * Andrew Ng's lecture on deep learning (한글 자막 및 한글 가이드 있음): [step 1](https://www.boostcourse.org/ai215), [step 2](https://www.boostcourse.org/ai216), [step 3](https://www.boostcourse.org/ai217), [step 4](https://www.boostcourse.org/ai218)
        * Direct links (no sign-in): [step 1](https://www.boostcourse.org/ai215/joinLectures/86246), [step 2](https://www.boostcourse.org/ai216/joinLectures/132203), [step 3](https://www.boostcourse.org/ai217/joinLectures/132223), [step 4](https://www.boostcourse.org/ai218/joinLectures/138357)
    * [골빈해커의 3분 딥러닝 텐서플로맛](https://www.hanbit.co.kr/store/books/look.php?p_code=B7257101308)
* Computer vision
    * [컴퓨터비전](http://www.kocw.net/home/cview.do?cid=1b1f5b73413060b5) (KOCW)
    * [딥러닝과 컴퓨터비전](http://www.kocw.net/home/cview.do?cid=ed866750e14cedd6) (KOCW)
    * [자습해도 모르겠던 딥러닝, 머리속에 인스톨 시켜드립니다](https://www.slideshare.net/yongho/ss-79607172) (특히 vision 및 image processing 관련 예제가 나옴)
    * [ResNet](https://lv99.tistory.com/25) (한글 설명)
    * [Object Detection on Android using TensorFlow Lite (TF Lite)](https://www.augmentedstartups.com/blog/object-detection-on-android-using-tensorflow-lite-tf-lite)
* Reinforcement learning
    * [Reinforcement learning explained](https://www.oreilly.com/radar/reinforcement-learning-explained/)
    * [Reinforcement Learning Made Simple](https://towardsdatascience.com/reinforcement-learning-made-simple-part-1-intro-to-basic-concepts-and-terminology-1d2a87aa060)
    * Sebastian Castro's introductory articles
        * [An Intuitive Guide to Reinforcement Learning](https://roboticseabass.com/2020/08/02/an-intuitive-guide-to-reinforcement-learning/) ([cached](attachments/RL1%20An%20Intuitive%20Guide%20to%20Reinforcement%20Learning%20-%20Robotic%20Sea%20Bass.pdf))
        * [Introduction to Deep Reinforcement Learning](https://roboticseabass.com/2020/08/15/introduction-to-deep-reinforcement-learning/) ([cached](attachments/RL2%20Introduction%20to%20Deep%20Reinforcement%20Learning%20-%20Robotic%20Sea%20Bass.pdf))
        * [Reinforcement Learning: Looking Ahead and Getting Started](https://roboticseabass.com/2020/08/22/reinforcement-learning-looking-ahead-and-getting-started/) ([cached](attachments/RL3%20Reinforcement%20Learning_%20Looking%20Ahead%20and%20Getting%20Started%20-%20Robotic%20Sea%20Bass.pdf))
* [Papers With Code](https://paperswithcode.com/)

[\[top\]](#table-of-contents)

# Basic math

* [Statistics 110, Harvard](https://www.boostcourse.org/ai152) (한글 자막 및 한글 가이드 있음) - [Direct link (no sign-in)](https://www.boostcourse.org/ai152/joinLectures/195039)
* [인공지능을 위한 선형대수](https://www.boostcourse.org/ai251) - [Direct link (no sign-in)](https://www.boostcourse.org/ai251/joinLectures/195088)
* Materials about Kalman Filter
    * [An Elementary Introduction to Kalman Filtering](https://arxiv.org/pdf/1710.04055.pdf) ([cached](attachments/AnElementaryIntroductionToKalmanFilteringpdf.pdf))
    * [How a Kalman filter works, in pictures](https://www.bzarg.com/p/how-a-kalman-filter-works-in-pictures/) ([cached](attachments/How%20a%20Kalman%20filter%20works%2C%20in%20pictures%20_%20Bzarg.pdf))
    * [Kalman and Bayesian Filters in Python](https://github.com/rlabbe/Kalman-and-Bayesian-Filters-in-Python)
* [A Korean blog article about Hidden Markov Model](https://untitledtblog.tistory.com/97) ([alternative link](https://untitledtblog.tistory.com/140), [cache](attachments/%5B%EB%A8%B8%EC%8B%A0%20%EB%9F%AC%EB%8B%9D%5D%20-%20%EC%9D%80%EB%8B%89%20%EB%A7%88%EB%A5%B4%EC%BD%94%ED%94%84%20%EB%AA%A8%EB%8D%B8%20(Hidden%20Markov%20Model%2C%20HMM).pdf))

[\[top\]](#table-of-contents)

# Coding style

* [The Art of Readable Code](https://learning.oreilly.com/library/view/the-art-of/9781449318482/) - 번역판: [읽기 좋은 코드가 좋은 코드다](http://aladin.kr/p/KFsHD)
* [Google Style Guides](https://google.github.io/styleguide/)
* [Chromium coding style](https://chromium.googlesource.com/chromium/src/+/main/styleguide/styleguide.md)
* [Code Complete (2nd ed)](https://www.amazon.com/gp/product/0735619670/) (번역판: [link](http://aladin.kr/p/Ro9nt))

[\[top\]](#table-of-contents)

# Software design and programming

* [Refactoring](https://martinfowler.com/books/refactoring.html) - [Online catalog](https://refactoring.com/catalog/)
* [Design Patterns](https://en.wikipedia.org/wiki/Design_Patterns)
* [The Architecture of Open Source Applications](http://aosabook.org/) (Joel Spolsky's blog article about it: [link](https://stackoverflow.blog/2011/06/22/se-podcast-09/))
* [Software Engineering's Greatest Hits](https://youtu.be/HrVtA-ue-x0) - Greg Wilson

[\[top\]](#table-of-contents)

# Algorithms

* [Computer Science Distilled](https://code.energy/computer-science-distilled) (번역판: [한 권으로 그리는 컴퓨터 과학 로드맵](http://aladin.kr/p/61rhB))
* [쉽게 배우는 알고리즘](http://aladin.kr/p/JP43N) - 문병로 저
* [Introduction to Algorithms](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)
    * [Thomas Cormen's Quora page](https://www.quora.com/profile/Thomas-Cormen-1)
* [P vs NP](https://ratsgo.github.io/data%20structure&algorithm/2017/11/30/NP/) - '[컴퓨터과학이 여는 세계](http://kwangkeunyi.snu.ac.kr/#books)'(이광근 저)에서 발췌 ([cached](attachments/P%2C%20NP%20%EB%AC%B8%EC%A0%9C%20%281%29%20%C2%B7%20ratsgo%27s%20blog.pdf))
* Algorithms ([free online materials](https://algs4.cs.princeton.edu/)) - Robert Sedgewick, Kevin Wayne

[\[top\]](#table-of-contents)

# Computer architecture

* [The Secret Life of Programs](https://nostarch.com/foundationsofcomp) (번역판: [한 권으로 읽는 컴퓨터 구조와 프로그래밍](http://aladin.kr/p/IPd2v))
* [Computer Systems: A Programmer’s Perspective](http://csapp.cs.cmu.edu/) (CS:APP)
* Modern CPU architecture
    * Nice videos from Intel, explaning basic concepts of CPU architecture
        * [https://youtu.be/vgPFzblBh7w](https://youtu.be/vgPFzblBh7w)
        * [https://youtu.be/o_WXTRS2qTY](https://youtu.be/o_WXTRS2qTY)
    * 로우 레벨 프로그래밍을 하거나 매우 performance critical한 코드를 작성할 때에는, 이런 것들도 고려해야 할 때가 있습니다.
        * 예를 들어 멀티쓰레드 프로그래밍을 할 때에는 out of order execution을 고려하여 barrier를 만들어 줘야 할 수도 있습니다.
            * [https://en.wikipedia.org/wiki/Memory_barrier](https://en.wikipedia.org/wiki/Memory_barrier)
        * C/C++ 프로그래머는 심지어 CPU의 branch prediction이 유리하게 일어나도록 컴파일러에게 코드를 특정 방법으로 arrange하라고 hint를 줄 수도 있습니다 (다만 많은 경우 이런 건 안 하는 게 낫습니다).
            * [https://stackoverflow.com/q/30130930](https://stackoverflow.com/q/30130930)
* Cache and memory
    * [What Every Programmer should Know about Memory](https://www.akkadia.org/drepper/cpumemory.pdf)
        * [Brief slides](https://www.akkadia.org/drepper/cpucache-slides.pdf)
        * [What have changed](https://stackoverflow.com/a/47714514)
    * [Scott Meyers: Cpu Caches and Why You Care](https://youtu.be/WDIkqP4JbkE)

[\[top\]](#table-of-contents)

# Godbolt - Compiler Explorer

* [What Everyone Should Know About How Amazing Compilers Are](https://cpponsea.uk/2019/sessions/keynote-what-everyone-should-know-about-how-amazing-compilers-are.html)
* [What Has My Compiler Done for Me Lately? Unbolting the Compiler's Lid](https://youtu.be/bSkpMdDe4g4) (Slides: [link](https://github.com/CppCon/CppCon2017/tree/master/Keynotes/What%20Has%20My%20Compiler%20Done%20for%20Me%20Lately%20-%20Unbolting%20the%20Compiler%27s%20Lid))

[\[top\]](#table-of-contents)

# Performance optimization

* [Optimization manuals](https://agner.org/optimize/#manuals) - by [Agner Fog](https://agner.org/)
* [Brendan Gregg](https://www.brendangregg.com/overview.html)
* [Latency numbers every programmer should know](https://gist.github.com/jboner/2841832)

[\[top\]](#table-of-contents)

# Programming tips and techniques

* Bit manipulation: [http://graphics.stanford.edu/~seander/bithacks.html](http://graphics.stanford.edu/~seander/bithacks.html)
* Hacker's Delight

[\[top\]](#table-of-contents)

# Web application development

* [The Twelve-Factor App](https://12factor.net/) (한국어판: [link](https://12factor.net/ko/))
* [React.js, 스프링 부트, AWS로 배우는 웹 개발 101](http://acornpub.co.kr/book/reactjs-springboot) - [김다정](https://cselabnotes.com/kr/sample-page/)
* [클라우드 인프라 구축 및 활용](http://www.kocw.net/home/cview.do?cid=5d286835fd5cde8c) (KOCW) - An introductory AWS course

[\[top\]](#table-of-contents)

# Distributed systems and data engineering

* [Designing Data-Intensive Applications](https://dataintensive.net/)
    * [Korean version](http://aladin.kr/p/t1Nzd) / [a review](https://towardsdatascience.com/designing-data-intensive-applications-book-review-cc34ba1f90a7) / [concise video summary](https://www.youtube.com/watch?v=PdtlXdse7pw&list=PL4KdJM8LzAMecwInbBK5GJ3Anz-ts75RQ) / [SDML bookclub notes and videos](https://github.com/SanDiegoMachineLearning/bookclub/blob/master/designing-data-intensive-apps.md) / [Slides in Korean](https://github.com/data-system-wiki/designing-data-intensive-applications) / [author interview](https://www.youtube.com/watch?v=grGqCuTcu50) / [SDE Skills videos](https://www.youtube.com/watch?v=fxNn_CpzdB0&list=PLBtMh4xfa9FGWU4E4oP9uqHuSl9ht7wXD&index=38)
    * 분산 시스템과 현대적 데이터 엔지니어링의 이론적 토대를 배울 수 있는 책
    * FAANG의 system design 면접 준비에 좋다고 추천되는 책

[\[top\]](#table-of-contents)

# C++

* [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html)
    * Old snapshots, just for comparsion (Do **not** use these!): [Korean](http://jongwook.kim/google-styleguide/trunk/cppguide.xml)(around Sep. 2013), [English](attachments/Google%20C%2B%2B%20Style%20Guide.pdf)(around Nov. 2011), [Korean](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=sorkelf&logNo=40133065744)(around mid 2011)
* [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)
* [Google's Tips of the Week](https://abseil.io/tips/)
* [C++ Insights](https://cppinsights.io/)
* ['Effective' series](https://www.aristeia.com/books.html), the most recommended books (한글 요약들 백업: [link](attachments/cppbooksummaries.zip))
    * Effective C++ ([한글 요약](http://ajwmain.iptime.org/programming/book_summary/%5B00%5Deffective_cpp/effective_cpp.html))
    * More Effective C++ ([한글 요약](http://ajwmain.iptime.org/programming/book_summary/%5B01%5Dmore_effective_cpp/more_effective_cpp.html))
    * Effective STL ([한글 요약](http://ajwmain.iptime.org/programming/book_summary/%5B02%5Deffective_stl/effective_stl.html))
    * Effective Modern C++ ([한글 요약](http://ajwmain.iptime.org/programming/book_summary/%5B03%5Deffective_modern_cpp/effective_modern_cpp.html)) ([짧은 요약](https://velog.io/@wsong0101/%EC%9D%B4%ED%8E%99%ED%8B%B0%EB%B8%8C-%EB%AA%A8%EB%8D%98-C-%EC%A0%95%EB%A6%AC))
* [API Design for C++](https://www.sciencedirect.com/book/9780123850034/api-design-for-c-and-and) (번역판: [C++ API 디자인](http://aladin.kr/p/IGia0))
* [씹어먹는 C++](https://modoocode.com/135)
* Modern C++
    * [C++ 시작하기 - 최신 C++](https://docs.microsoft.com/ko-kr/cpp/cpp/welcome-back-to-cpp-modern-cpp?view=msvc-170) (Microsoft)
    * [Overview of the New C++ (C++11/14)](https://www.artima.com/samples/cpp11-14NotesSample.pdf) - Scott Meyers
    * [Modern C++ 무조건 써야 해?](https://deview.kr/2018/schedule/233) ([동영상](https://tv.naver.com/v/4578722), [발표자료](https://www.slideshare.net/deview/143-modern-c))
    * [Effective Modern C++](https://www.oreilly.com/library/view/effective-modern-c/9781491908419/?cmp=af-code-books-video-product_cj_0636920033707_7708709) ([한글 요약](http://ajwmain.iptime.org/programming/book_summary/%5B03%5Deffective_modern_cpp/effective_modern_cpp.html)) ([짧은 요약](https://velog.io/@wsong0101/%EC%9D%B4%ED%8E%99%ED%8B%B0%EB%B8%8C-%EB%AA%A8%EB%8D%98-C-%EC%A0%95%EB%A6%AC))
    * [씹어먹는 C++](https://modoocode.com/135) (chapter 12 - chapter 17)
    * [What is move semantics?](https://stackoverflow.com/q/3106110) (Stack Overflow) - 기계번역: [link](https://melkia.dev/ko/questions/3106110)
    * [What are rvalues, lvalues, xvalues, glvalues, and prvalues?](https://stackoverflow.com/q/3601602) (Stack Overflow)
* [C++ 언어 설명서](https://docs.microsoft.com/ko-kr/cpp/cpp/?view=msvc-170) (Microsoft)
* [더 안전하게 C++ 코드를 작성하는 법](https://www.cv-learn.com/20220115-safer-c/)
* [When a Microsecond Is an Eternity: High Performance Trading Systems in C++](https://youtu.be/NH1Tta7purM)
    * [한글 요약](https://velog.io/@wsong0101/%EB%86%92%EC%9D%80-%EC%84%B1%EB%8A%A5%EC%9D%98-C-%ED%8A%B8%EB%A0%88%EC%9D%B4%EB%94%A9-%EC%8B%9C%EC%8A%A4%ED%85%9C) (주의: 이 한글 블로그 글에 있는 비디오 링크는 잘못되었음. 윗 줄의 링크가 맞음) ([cached](attachments/%EB%86%92%EC%9D%80%20%EC%84%B1%EB%8A%A5%EC%9D%98%20C%2B%2B%20%ED%8A%B8%EB%A0%88%EC%9D%B4%EB%94%A9%20%EC%8B%9C%EC%8A%A4%ED%85%9C.pdf))

[\[top\]](#table-of-contents)

# Java

* [Effective Java](https://www.oreilly.com/library/view/effective-java/9780134686097/) ([한글 ebook](http://aladin.kr/p/BfloN) / [한글 요약 블로그](https://icarus8050.tistory.com/category/Java/Effective%20Java) / [더 자세히 설명된 블로그](https://hirlawldo.tistory.com/category/%EA%B0%9C%EB%B0%9C/Effective%20Java) / [또 다른 블로그](https://developer-cheol.tistory.com/tag/%EC%9D%B4%ED%8E%99%ED%8B%B0%EB%B8%8C%EC%9E%90%EB%B0%94))
* [Modern Java in Action](https://www.manning.com/books/modern-java-in-action) ([한글 요약 블로그](https://ckddn9496.tistory.com/category/Java/%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%20%EC%9D%B8%20%EC%95%A1%EC%85%98))
* Spring 요약: [pjok1122/Spring-Summary](https://github.com/pjok1122/Spring-Summary)
* [Java Concurrency](http://tutorials.jenkov.com/java-concurrency/index.html) - Jakob Jenkov ([일부 한글 번역](https://parkcheolu.tistory.com/category/Java/Concurrency))

[\[top\]](#table-of-contents)

# Open source projects

* [Google's code search for their open source projects](https://cs.opensource.google/)
* [Linux kernel](https://elixir.bootlin.com/)
* [Chromium](https://www.chromium.org/Home) / [Chromium OS](https://www.chromium.org/chromium-os) (code search: [link](https://source.chromium.org/))
* [Android](https://www.android.com/) (code search: [link](https://cs.android.com/))
* [Kubernetes](https://opensource.google/projects/kubernetes)

[\[top\]](#table-of-contents)

# Tools

* CMake
    * [씹어먹는 C++](https://modoocode.com/332)

[\[top\]](#table-of-contents)

# Continuous integration examples

* [Android](https://source.android.com/setup/build/dashboard)
* [Chromium](https://www.chromium.org/developers/testing/chromium-build-infrastructure/tour-of-the-chromium-buildbot/) (* see also: [Deterministic builds](https://chromium.googlesource.com/chromium/src.git/+/HEAD/docs/deterministic_builds.md))
* [Chromium OS](https://www.chromium.org/chromium-os/build/tour-of-the-chromiumos-buildbot/)
* [Kubernetes](https://github.com/kubernetes/test-infra)

# Productivity

* [Effective Engineer](http://www.effectiveengineer.com/) (한글번역: [이펙티브 엔지니어](https://books.google.co.kr/books/about/%EC%9D%B4%ED%8E%99%ED%8B%B0%EB%B8%8C_%EC%97%94%EC%A7%80%EB%8B%88%EC%96%B4.html?id=Hap5EAAAQBAJ&redir_esc=y), Summary: [English](https://gist.github.com/rondy/af1dee1d28c02e9a225ae55da2674a6f), [Korean](https://dev200ok.blogspot.com/2020/04/dev_13.html))
* [Meetings That Don’t Suck](https://www.bringthedonuts.com/essays/meetings-that-dont-suck.html) - Ken Norton
    * 한 가지 추가하고 싶은 것: 모든 회의는 결과물이 있어야 한다고 생각한다. 결과물은 대개 의사결정, 액션 아이템, 또는 (단순 회의록이 아닌)문서이다.
* [Maker's schedule, manager's schedule](http://www.paulgraham.com/makersschedule.html) - Paul Graham (한글 번역: [개발자의 시간 관리 vs 관리자의 시간 관리](https://justinchronicles.net/ko/2014/02/07/makers-schedule-managers-schedule/), [관련글 1](https://platum.kr/archives/75646), [관련글 2](https://brunch.co.kr/@davejin/17), [관련글 3](https://topofcomp.tistory.com/498))
* [Accelerate: The Science of Lean Software and DevOps: Building and Scaling High Performing Technology Organizations](https://www.amazon.com/Accelerate-Software-Performing-Technology-Organizations/dp/1942788339) ([번역판](http://aladin.kr/p/ONrE0), [한글요약1](https://jh4hj.tistory.com/entry/Accelerate-%EB%94%94%EC%A7%80%ED%84%B8-%ED%8A%B8%EB%9E%9C%EC%8A%A4%ED%8F%AC%EB%A9%94%EC%9D%B4%EC%85%98-%EC%97%94%EC%A7%84), [한글요약2](https://gowoonsori.com/etc/accelerate/))
* [The Good Day Project](https://github.blog/2021-05-25-octoverse-spotlight-good-day-project/)
* [The SPACE of Developer Productivity](https://queue.acm.org/detail.cfm?id=3454124)

# Excellency

* [The 4 things it takes to be an expert](https://youtu.be/5eW6Eagr9XA)
    * 어떤 영역에서 실력을 키워 전문가가 되는 법
        * 피드백을 받으면서 반복적으로 수행하기
        * 뭔가 노력하는 만큼 결과가 좋아지는, valid environment
        * 즉각적으로 받는 피드백
        * Comfort zone을 벗어나기 (본인을 살짝 push하는 환경 및 동기부여요인을 만들어 놓고, 쉽게 할 수 있는 것보다는 간신히 할 수 있는 난이도의 일을 한다)
* [공부 잘하는 학생, 대한민국 상위 0.1% 학생의 비밀](https://youtu.be/ptiCX_I0fZc)
* [Great at Work](http://mortenhansen.com/great-at-work/) ([한글요약](https://parksehee.blog/2021/01/22/great-at-work/))
* [The Talent Code](https://danielcoyle.com/the-talent-code/) ([번역판](http://aladin.kr/p/eyddh))

[\[top\]](#table-of-contents)

# Engineering management

* [The Making of a Manager](https://www.juliezhuo.com/book/manager.html) (한글번역: [팀장의 탄생](https://www.gilbut.co.kr/book/view?bookcode=BN002858), Summary in English: [link](https://fellow.app/blog/management/julie-zhuo-the-making-of-a-manager/)) 
* [The Manager's Path](https://www.oreilly.com/library/view/the-managers-path/9781491973882/) (한글번역: [개발 7년차, 매니저 1년차](http://aladin.kr/p/4WyAq))
    * [한빛출판네트워크 편집자 Choice](https://www.hanbit.co.kr/channel/choice/editor_choice_view.html?cms_code=CMS9150073010)
* [어서 와, 리더는 처음이지?](https://brunch.co.kr/brunchbook/youngleaders)
* [Scaling engineering organizations](https://stripe.com/atlas/guides/scaling-eng) - Raylene Yung (Stripe)
* [Software Engineering at Google](https://arxiv.org/abs/1702.01715) (짧고 읽기 쉬운 논문) (한글번역: [링크](https://blog.naver.com/junechol/221495080367), [cached](attachments/junechol-Software%20Engineering%20at%20Google.pdf)) ([한글요약](https://docs.likejazz.com/software-engineering-at-google/))
* [Software Engineering at Google](https://abseil.io/resources/swe-book) (두껍지만 읽기 쉬운 책) (5장 번역: [링크](https://blog.naver.com/junechol/222592134145), [cached](attachments/junechol-chap5.pdf) / 6장 번역: [링크](https://blog.naver.com/junechol/222602505041), [cached](attachments/junechol-chap6.pdf))
* 실리콘 밸리의 엔지니어링 매니저(리더)들은 대체 무엇을 하는가? ([1편](https://sendbird.com/ko/blog/eng-leader-role-1), [2편](https://sendbird.com/ko/blog/eng-leader-role-2))
* [Google's Project Aristotle](https://rework.withgoogle.com/guides/understanding-team-effectiveness/) - What makes a team effective?
    * The New York Times Magazine's article about this: [link](https://www.nytimes.com/2016/02/28/magazine/what-google-learned-from-its-quest-to-build-the-perfect-team.html) / [cached (no sign-in)](attachments/What%20Google%20Learned%20From%20Its%20Quest%20to%20Build%20the%20Perfect%20Team%20-%20The%20New%20York%20Times.pdf)
        * The article is long. You can start from "But what was confusing was that not all the good teams appeared to behave in the same ways."
* Google's Project Oxygen - Behaviours of best managers
    * [A blog post](https://rework.withgoogle.com/blog/the-evolution-of-project-oxygen/)
    * [Guides](https://rework.withgoogle.com/subjects/managers/) (한국어로 된 해석: [1회](https://infuture.kr/1642), [2회](https://infuture.kr/1643) / cached: [1회](attachments/%EC%9D%B8%ED%93%A8%EC%B2%98%EC%BB%A8%EC%84%A4%ED%8C%85%20%26%20%EC%9C%A0%EC%A0%95%EC%8B%9D%20__%20%EA%B5%AC%EA%B8%80%EC%9D%98%20%EB%A6%AC%EB%8D%94%EC%8B%AD_%201.%20%ED%9B%8C%EB%A5%AD%ED%95%9C%20%EA%B4%80%EB%A6%AC%EC%9E%90%EB%8A%94%20%EB%88%84%EA%B5%AC%EC%9D%B8%EA%B0%80_.pdf), [2회](attachments/%EC%9D%B8%ED%93%A8%EC%B2%98%EC%BB%A8%EC%84%A4%ED%8C%85%20%26%20%EC%9C%A0%EC%A0%95%EC%8B%9D%20__%20%EA%B5%AC%EA%B8%80%EC%9D%98%20%EB%A6%AC%EB%8D%94%EC%8B%AD_%202.%20%ED%8C%80%EC%9B%90%EA%B3%BC%20%ED%95%A8%EA%BB%98%20%EB%B9%84%EC%A0%84%EC%9D%84%20%EC%88%98%EB%A6%BD%ED%95%98%EA%B3%A0%20%EA%B3%B5%EC%9C%A0%ED%95%98%EB%9D%BC.pdf))
    * [관리자를 위한 피드백](https://edward-jee.github.io/attachments/%EA%B4%80%EB%A6%AC%EC%9E%90%EB%A5%BC%20%EC%9C%84%ED%95%9C%20%ED%94%BC%EB%93%9C%EB%B0%B1.pdf) (Google이 공개한 [Manager Feedback Survey](https://rework.withgoogle.com/guides/managers-give-feedback-to-managers/steps/try-googles-manager-feedback-survey/) form을 번역하고 일부 수정한 것)
* [Blameless Post Mortems](https://www.bringthedonuts.com/newsletter/blameless-post-mortems.html) - Ken Norton
* Google engineering director 출신 이준영 님 인터뷰 - [1부](https://www.youtube.com/watch?v=VT48Yctgybs), [2부](https://www.youtube.com/watch?v=oSZtDpWxlIA)
* [Google TLM 출신 이동휘 님 인터뷰](https://magazine.hankyung.com/job-joy/article/202202166841d)
* [The surprising skills that help you succeed in your product management career as you get more senior](https://jackiebo.medium.com/the-surprising-skills-that-help-you-succeed-in-your-product-management-career-as-you-get-more-3a1fcff40f8e)
    * Advice on career development, helpful for everybody IMO (not only for PMs)
* [미끄럼틀 설치한다고 저절로 혁신?… 스타트업 그냥 따라하다간 미끄러진다](https://web.archive.org/web/20190905011559/http://weeklybiz.chosun.com/site/data/html_dir/2019/03/14/2019031402078.html) ([cached](attachments/%5BWEEKLY%20BIZ%5D%20%EB%AF%B8%EB%81%84%EB%9F%BC%ED%8B%80%20%EC%84%A4%EC%B9%98%ED%95%9C%EB%8B%A4%EA%B3%A0%20%EC%A0%80%EC%A0%88%EB%A1%9C%20%ED%98%81%EC%8B%A0_%E2%80%A6%20%EC%8A%A4%ED%83%80%ED%8A%B8%EC%97%85%20%EA%B7%B8%EB%83%A5%20%EB%94%B0%EB%9D%BC%ED%95%98%EB%8B%A4%EA%B0%84%20%EB%AF%B8%EB%81%84%EB%9F%AC%EC%A7%84%EB%8B%A4.pdf))
    * 의견: 예전의 아마존처럼 직원을 상대평가하여 하위 몇 프로를 해고하는 방식에는 동의하지 않습니다. 회사가 믿을 수 있고 안전하다는 느낌을 주면서도 능률적일 수 있다고 믿습니다.
* [성공한 팀장들은 지독하게 솔직… 다만 직구 아닌 변화구로 말한다](https://web.archive.org/web/20200203171507/http://weeklybiz.chosun.com/site/data/html_dir/2019/09/26/2019092602017.html) ([cached](attachments/%5BWEEKLY%20BIZ%5D%20%EC%84%B1%EA%B3%B5%ED%95%9C%20%ED%8C%80%EC%9E%A5%EB%93%A4%EC%9D%80%20%EC%A7%80%EB%8F%85%ED%95%98%EA%B2%8C%20%EC%86%94%EC%A7%81%E2%80%A6%20%EB%8B%A4%EB%A7%8C%20%EC%A7%81%EA%B5%AC%20%EC%95%84%EB%8B%8C%20%EB%B3%80%ED%99%94%EA%B5%AC%EB%A1%9C%20%EB%A7%90%ED%95%9C%EB%8B%A4.pdf))
    * 의견: 솔직한 피드백을 하되 기분 좋게 전달하는 방법이 있으리라 믿습니다. 듣는 사람에게 반발, 저항, 방어하는 마음이 생기지 않도록, 개선할 점을 편안하고 유쾌하게 커뮤니케이션하는 기술이 필요하다고 생각합니다.
* [StaffEng](https://staffeng.com/)
* [High Output Management](https://www.amazon.com/High-Output-Management-Andrew-Grove/dp/0679762884) ([번역판](http://aladin.kr/p/NKMCu), [WP article](https://www.washingtonpost.com/news/on-leadership/wp/2015/11/18/how-a-business-book-from-the-80s-became-a-cult-classic-in-silicon-valley/) and [cache](attachments/How%20a%20business%20book%20from%20the%20%E2%80%9980s%20became%20a%20cult%20classic%20in%20Silicon%20Valley%20-%20The%20Washington%20Post.pdf), [Ben Horowitz's essay](https://a16z.com/2015/11/13/high-output-management/), [summary by Ian Tien](https://medium.com/@iantien/top-takeaways-from-andy-grove-s-high-output-management-2e0ecfb1ea63))
* [Interview tips for moving up to leadership](https://www.bzarg.com/p/interview-tips-for-moving-up-to-leadership/) ([cached](attachments/Interview%20tips%20for%20moving%20up%20to%20leadership%20_%20Bzarg.pdf))

[\[top\]](#table-of-contents)

# Product Management

* [Building a great product management organization](https://stripe.com/atlas/guides/building-a-great-pm-org) (Stripe Atlas guide) - Elad Gil
* [How 51 leading tech teams define the Product Manager role](https://producthabits.com/product-manager-job-description/) (한글 번역: [실리콘밸리 51개 기업들이 말하는 프로덕트 매니저의 역할 9가지](http://blog.wishket.com/%EC%8B%A4%EB%A6%AC%EC%BD%98%EB%B0%B8%EB%A6%AC-51%EA%B0%9C-%EA%B8%B0%EC%97%85%EB%93%A4%EC%9D%B4-%EB%A7%90%ED%95%98%EB%8A%94-%ED%94%84%EB%A1%9C%EB%8D%95%ED%8A%B8-%EB%A7%A4%EB%8B%88%EC%A0%80%EC%9D%98/))
* [채용 공고 뜯어보며 PM 직무 이해하기](https://brunch.co.kr/@moon9410/43)
* [사업 폭넓게 정의하고 실패 땐 빨리 인정, 피버팅 대명사 ‘슬랙’도 그렇게 탄생했다](https://dbr.donga.com/article/view/1203/article_no/9898/ac/a_view) ([cached](attachments/%EC%82%AC%EC%97%85%20%ED%8F%AD%EB%84%93%EA%B2%8C%20%EC%A0%95%EC%9D%98%ED%95%98%EA%B3%A0%20%EC%8B%A4%ED%8C%A8%20%EB%95%90%20%EB%B9%A8%EB%A6%AC%20%EC%9D%B8%EC%A0%95%2C%20%ED%94%BC%EB%B2%84%ED%8C%85%20%EB%8C%80%EB%AA%85%EC%82%AC%20%E2%80%98%EC%8A%AC%EB%9E%99%E2%80%99%EB%8F%84%20%EA%B7%B8%EB%A0%87%EA%B2%8C%20%ED%83%84%EC%83%9D%ED%96%88%EB%8B%A4%20_%20%EA%B2%BD%EC%98%81%EC%A0%84%EB%9E%B5%20_%20DBR.pdf)) - Dong-A Business Review
* [On Writing Product Roadmaps](https://goberoi.com/on-writing-product-roadmaps-a4d72f96326c) - Gaurav Oberoi
* Jackie Bavaro
    * [Cracking the PM Career](https://www.crackingthepmcareer.com/) - with Gayle McDowell
    * [Cracking the PM Interview](https://www.crackingthepminterview.com/) (번역판: [PM인터뷰의 모든 것](https://jpub.tistory.com/471) / [2장 PDF](attachments/PM%EC%9D%B8%ED%84%B0%EB%B7%B0%EC%9D%98%EB%AA%A8%EB%93%A0%EA%B2%83_sample.pdf))
    * [https://jackiebo.medium.com/](https://jackiebo.medium.com/)
* Marty Cagan
    * [Inspired](https://svpg.com/inspired-how-to-create-products-customers-love/) (번역판: [link](https://jpub.tistory.com/885), 한글 요약: [link](https://parksehee.blog/2022/06/03/inspired/))
    * [https://svpg.com/](https://svpg.com/)
        * [The Most Important Thing](https://www.svpg.com/the-most-important-thing/)
            * 피쳐 팀이 아니라 프로덕트 팀이 되기 위해 가장 중요한 것은, 엔지니어들에게 권한을 주는 것이다.
            * 즉, 엔지니어들에게 해결해야 할 문제와 전략적 맥락(strategic context)을 주고, 엔지니어들이 기술을 활용하여 가장 좋은 해결책을 찾도록 하는 것이다.
            * 혁신의 원천은 엔지니어이다.
* Ken Norton
    * [How to Hire a Product Manager](https://www.bringthedonuts.com/essays/productmanager.html) (A famous classic that explains what a PM is) (10 yr anniversary: [link](https://www.bringthedonuts.com/essays/happy-10th-birthday-to-hthapm.html)) (한글 번역 1: [link](https://m.blog.naver.com/careerinspo/221976711074)) (한글 번역 2: [link](https://webuildproduct.com/%EC%96%B4%EB%96%A4-%ED%94%84%EB%A1%9C%EB%8D%95%ED%8A%B8-%EB%A7%A4%EB%8B%88%EC%A0%80%EB%A5%BC-%EC%B1%84%EC%9A%A9%ED%95%B4%EC%95%BC-%ED%95%A0%EA%B9%8C-45396988f6a0))
    * [What Makes A Strong Product Culture?](https://newsletter.bringthedonuts.com/p/what-makes-a-strong-product-culture)
    * [10x Not 10%](https://www.bringthedonuts.com/essays/10x-not-10-percent.html)
    * [How do you make sure your new PM is successful?](https://www.bringthedonuts.com/newsletter/how-do-you-make-sure-a-new-pm-is-successful.html)
    * [What to Do in Your First 30 Days in a New Role](https://www.bringthedonuts.com/essays/what-to-do-in-your-first-30-days-as-product-manager.html) (한글 번역: [첫 30일 동안 PM이 해야 할 12가지](https://brunch.co.kr/@hj-kang/4)) (실행 후기: [link](https://medium.com/@alishadle_80244/i-tested-ken-nortons-article-what-to-do-in-your-first-30-days-and-this-is-what-i-learned-b99286627474))
    * [What I wished I’d known back when I started](https://newsletter.bringthedonuts.com/p/reflecting-on-a-career-in-product)
    * [The Tools Don't Matter](https://newsletter.bringthedonuts.com/p/the-tools-dont-matter)
* Lenny Rachitsky
    * [My favorite product management templates](https://www.lennysnewsletter.com/p/my-favorite-templates-issue-37)
    * [The Best of Lenny's Newsletter](https://www.lennysnewsletter.com/p/the-best-of-lennys-newsletter)
    * [PM이 가져야 할 매우 효과적인 습관](https://jihye.oopy.io/pm/habit)
    * [Getting buy-in](https://www.lennysnewsletter.com/p/getting-buy-in) (한글 요약: [내 의견이 받아들여지게 하는 방법](https://m.blog.naver.com/careerinspo/222399124016)) ([cached](attachments/%5B%EB%89%B4%EC%8A%A4%EB%A0%88%ED%84%B0%5D%20%EB%82%B4%20%EC%9D%98%EA%B2%AC%EC%9D%B4%20%EB%B0%9B%EC%95%84%EB%93%A4%EC%97%AC%EC%A7%80%EA%B2%8C%20%ED%95%98%EB%8A%94%20%EB%B0%A9%EB%B2%95%20_%20%EB%84%A4%EC%9D%B4%EB%B2%84%20%EB%B8%94%EB%A1%9C%EA%B7%B8.pdf))
* Sachin Rekhi
    * [Top 100 Resources for Product Managers](https://www.sachinrekhi.com/top-resources-for-product-managers)
    * [3 Types of Product Managers: Builders, Tuners, Innovators](https://www.sachinrekhi.com/3-types-of-product-managers-builders-tuners-innovators)
    * [Finding Product Culture Fit](https://www.sachinrekhi.com/finding-product-culture-fit)
* Marc Andreessen
    * [https://pmarchive.com/](https://pmarchive.com/)
    * [The Pmarca Blog Archives (pdf)](https://a16z.com/wp-content/uploads/2021/08/The-pmarca-Blog-Archives.pdf)
    * [https://a16z.com/](https://a16z.com/)
* Melissa Perri
    * [Escaping the Build Trap](https://melissaperri.com/book) (번역판: [link](http://aladin.kr/p/AyivU)) (한글 평: [link](https://bizbuddha.tistory.com/962))
    * [https://melissaperri.com/](https://melissaperri.com/)
* [Good Product Manager/Bad Product Manager](https://a16z.com/2012/06/15/good-product-managerbad-product-manager/) - Ben Horowitz (한글 번역: [link](https://m.blog.naver.com/careerinspo/221955654535))
* [Let's talk about Product Management](https://news.greylock.com/let-s-talk-about-product-management-d7bc5606e0c4) - Josh Elman (한글 번역: [link](https://m.blog.naver.com/careerinspo/221963974171))
* [Product managers for the digital world](https://www.mckinsey.com/industries/technology-media-and-telecommunications/our-insights/product-managers-for-the-digital-world) (참고: [PM유형테스트](https://brunch.co.kr/@windydog/423))
* [Rework](https://basecamp.com/books/rework) (번역판: [리워크](http://aladin.kr/p/IbO0y))
* [When should you a hire a Product Manager?](https://medium.com/once-upon-a-team/when-should-you-a-hire-a-product-manager-91e393862150) (한글 번역: [언제 프로덕트 매니저를 채용해야 할까?](https://webuildproduct.com/%EC%96%B8%EC%A0%9C-%ED%94%84%EB%A1%9C%EB%8D%95%ED%8A%B8-%EB%A7%A4%EB%8B%88%EC%A0%80%EB%A5%BC-%EC%B1%84%EC%9A%A9%ED%95%B4%EC%95%BC-%ED%95%A0%EA%B9%8C-ca5fdf076206))
* Miscellaneous posts
    * [현재 <개발자>인데 "프로덕트매니저"가 되고 싶다구요?](https://brunch.co.kr/@ywkim36/17)
    * [좋은 PM에게 '영혼의 닭고기 수프'와 같은 10권의 책](https://brunch.co.kr/@ywkim36/45)
    * [What is a project manager? The lead role for project success](https://www.cio.com/article/230682/what-is-a-project-manager-the-lead-role-for-project-success.html)
    * [Project management for non-project managers](https://www.atlassian.com/project-management)
    * [PM은 리더가 아니다?··· 프로젝트 관리자들의 8가지 착각](https://www.ciokorea.com/news/146190)
    * [프로젝트 관리에 관한 그릇된 통념 12가지](https://www.ciokorea.com/news/192744)
    * [Product Management for the Enterprise](https://medium.com/@BlairReeves/product-management-for-the-enterprise-f1118798376f)
    * [도그냥TV](https://www.youtube.com/channel/UCreMBpOzMfpoKTluWmPiesg)

## How to write a PRD

* [How to Write a Product Requirements Document (PRD)](https://blog.tryexponent.com/how-to-write-a-prd/) (한글 번역: [구글 프로덕트 매니저가 알려주는 기획서 작성 꿀팁](https://brunch.co.kr/@lulina724/26))
* [How to Write a Good PRD](https://svpg.com/assets/Files/goodprd.pdf) - Martin Cagan
* [Need more than a PRD? Functional specs to the rescue](https://productmanagementtips.com/2007/11/12/functionalspecs/) - Gopal Shenoy
* [On Writing Product Spec](https://goberoi.com/on-writing-product-specs-5ca697b992fd) - Gaurav Oberoi (한글 번역: [프로덕트 스펙 문서 작성법](https://brunch.co.kr/@hj-kang/2))
* [How to Write a Product Requirements Document - With Examples](https://www.perforce.com/blog/alm/how-write-product-requirements-document-prd) (at Perforce blog)
* [Product Hunt](https://docs.google.com/document/d/1yrU5F6Gxhkfma91wf_IbZfexw8_fahbGQLW3EvwdfQI/) example
* Joel Spolsky's Painless Functional Specifications: [part 1](https://www.joelonsoftware.com/2000/10/02/painless-functional-specifications-part-1-why-bother/), [part 2](https://www.joelonsoftware.com/2000/10/03/painless-functional-specifications-part-2-whats-a-spec/), [part 3](https://www.joelonsoftware.com/2000/10/04/painless-functional-specifications-part-3-but-how/), [part 4](https://www.joelonsoftware.com/2000/10/15/painless-functional-specifications-part-4-tips/)
* [My favorite product management templates](https://www.lennysnewsletter.com/p/my-favorite-templates-issue-37) - Lenny Rachitsky

[\[top\]](#table-of-contents)

# OKR

* [John Doerr's speech about OKRs](https://www.ted.com/talks/john_doerr_why_the_secret_to_success_is_setting_the_right_goals) (더 나은 한국어 해석: [link](okr_speech_translation.md))
* [Google's guide at re:Work](https://rework.withgoogle.com/guides/set-goals-with-okrs) (한국어로 된 해석: [1회](https://infuture.kr/1630), [2회](https://infuture.kr/1631), [3회](https://infuture.kr/1632), [4회](https://infuture.kr/1633) / cached: [1회](attachments/%EC%9D%B8%ED%93%A8%EC%B2%98%EC%BB%A8%EC%84%A4%ED%8C%85%20%26%20%EC%9C%A0%EC%A0%95%EC%8B%9D%20__%20%EA%B5%AC%EA%B8%80%EC%9D%98%20%EB%AA%A9%ED%91%9C%EC%84%A4%EC%A0%95_%201.%20%ED%95%B5%EC%8B%AC%EB%82%B4%EC%9A%A9%20%EA%B0%9C%EA%B4%84.pdf), [2회](attachments/%EC%9D%B8%ED%93%A8%EC%B2%98%EC%BB%A8%EC%84%A4%ED%8C%85%20%26%20%EC%9C%A0%EC%A0%95%EC%8B%9D%20__%20%EA%B5%AC%EA%B8%80%EC%9D%98%20%EB%AA%A9%ED%91%9C%EC%84%A4%EC%A0%95_%202.%20OKRs%EB%8A%94%20%EC%84%B1%EA%B3%BC%EA%B4%80%EB%A6%AC%EB%8F%84%EA%B5%AC%EA%B0%80%20%EC%95%84%EB%8B%88%EB%9D%BC%20%EC%9D%98%EC%82%AC%EC%86%8C%ED%86%B5%EB%8F%84%EA%B5%AC.pdf), [3회](attachments/%EC%9D%B8%ED%93%A8%EC%B2%98%EC%BB%A8%EC%84%A4%ED%8C%85%20%26%20%EC%9C%A0%EC%A0%95%EC%8B%9D%20__%20%EA%B5%AC%EA%B8%80%EC%9D%98%20%EB%AA%A9%ED%91%9C%EC%84%A4%EC%A0%95_%203.%20OKRs%20%EC%88%98%EB%A6%BD%EC%9D%98%20%ED%8C%81%EA%B3%BC%20%ED%94%BC%ED%95%B4%EC%95%BC%20%ED%95%A0%20%EC%98%A4%EB%A5%98.pdf), [4회](attachments/%EC%9D%B8%ED%93%A8%EC%B2%98%EC%BB%A8%EC%84%A4%ED%8C%85%20%26%20%EC%9C%A0%EC%A0%95%EC%8B%9D%20__%20%EA%B5%AC%EA%B8%80%EC%9D%98%20%EB%AA%A9%ED%91%9C%EC%84%A4%EC%A0%95_%204.%20%ED%8C%80%20OKRs%20%EC%88%98%EB%A6%BD%EA%B3%BC%20%EB%93%B1%EA%B8%89%20%EA%B2%B0%EC%A0%95.pdf))
* [한국 기업이 구글식 성과평가? 무조건 따라하지 말아라](https://www.joongang.co.kr/article/23795521)
    * 회사가 목표(Objective)를 설정하면 부서와 직원들이 자신들의 목표를 직접 설정한다. 국내 기업들이 많이 쓰는 핵심성과지표(KPI)처럼 하달식으로 정하지 않는 것이 핵심이다. 황 대표는 "KPI로 전년 대비 3%, 5% 더 달성 하네 마네 해서는 구글·애플·아마존과 같은 혁신 성장을 시도조차 할 수 없을 것"이라고 꼬집었다.
    * OKR을 성공적으로 도입해 안착하려면 다음 3가지가 필요하다고 강조했다.
        * 목표를 달성하지 못해도 괜찮다고 말하는 실패 용인 문화
        * 목표 달성시 급여가 얼마 오른다더라 하는 식의 불필요한 디테일에 집착하지 않는 문화
        * 주기적인 1대1 미팅 등으로 직원에게 올바른 동기 부여를 하는 문화
* [Are you doing OKRs right?](https://medium.com/range/are-you-doing-okrs-right-5ca1fa1e53d2) - Braden Kowitz
* [The Tools Don't Matter](https://newsletter.bringthedonuts.com/p/the-tools-dont-matter) - Ken Norton

[\[top\]](#table-of-contents)

# Hiring

* [Here's Google's Secret to Hiring the Best People](https://www.wired.com/2015/04/hire-like-google/) - from _[Work Rules!](https://www.workrules.net/)_ by Laszlo Bock ([cached](attachments/Here%27s%20Google%27s%20Secret%20to%20Hiring%20the%20Best%20People%20_%20WIRED.pdf))
* [The Guerrilla Guide to Interviewing](https://www.joelonsoftware.com/2006/10/25/the-guerrilla-guide-to-interviewing-version-30/) - Joel on Software (번역판: '[조엘 온 소프트웨어](http://www.acornpub.co.kr/book/joel-on-software)')
* [Google's guide at re:Work](https://rework.withgoogle.com/subjects/hiring/) (한국어로 된 해석: [1회](https://infuture.kr/1634), [2회](https://infuture.kr/1635), [3회](https://infuture.kr/1636), [4회](https://infuture.kr/1637), [5회](https://infuture.kr/1638), [6회](https://infuture.kr/1639), [7회](https://infuture.kr/1640), [8회](https://infuture.kr/1641) / cached: [1회](attachments/%EC%9D%B8%ED%93%A8%EC%B2%98%EC%BB%A8%EC%84%A4%ED%8C%85%20%26%20%EC%9C%A0%EC%A0%95%EC%8B%9D%20__%20%EA%B5%AC%EA%B8%80%EC%9D%98%20%EC%B1%84%EC%9A%A9_%201.%20%EC%A7%80%EC%9B%90%EC%9E%90%EC%9D%98%20%EA%B2%BD%ED%97%98%EC%97%90%20%EC%A3%BC%EC%9D%98%EB%A5%BC%20%EA%B8%B0%EC%9A%B8%EC%97%AC%EB%9D%BC.pdf), [2회](attachments/%EC%9D%B8%ED%93%A8%EC%B2%98%EC%BB%A8%EC%84%A4%ED%8C%85%20%26%20%EC%9C%A0%EC%A0%95%EC%8B%9D%20__%20%EA%B5%AC%EA%B8%80%EC%9D%98%20%EC%B1%84%EC%9A%A9_%202.%20%EC%A7%80%EC%9B%90%EC%9E%90%EB%A5%BC%20%EA%B3%A0%EA%B0%9D%EC%B2%98%EB%9F%BC%20%EB%8C%80%ED%95%98%EB%9D%BC.pdf), [3회](attachments/%EC%9D%B8%ED%93%A8%EC%B2%98%EC%BB%A8%EC%84%A4%ED%8C%85%20%26%20%EC%9C%A0%EC%A0%95%EC%8B%9D%20__%20%EA%B5%AC%EA%B8%80%EC%9D%98%20%EC%B1%84%EC%9A%A9_%203.%20%EC%B1%84%EC%9A%A9%EC%9C%84%EC%9B%90%ED%9A%8C%EB%A5%BC%20%ED%99%9C%EC%84%B1%ED%99%94%ED%95%98%EB%9D%BC.pdf), [4회](attachments/%EC%9D%B8%ED%93%A8%EC%B2%98%EC%BB%A8%EC%84%A4%ED%8C%85%20%26%20%EC%9C%A0%EC%A0%95%EC%8B%9D%20__%20%EA%B5%AC%EA%B8%80%EC%9D%98%20%EC%B1%84%EC%9A%A9_%204.%20%EB%A9%B4%EC%A0%91%EA%B4%80%EC%9D%98%20%EC%9E%90%EC%9C%A0%EB%A1%9C%EC%9A%B4%20%EC%A7%88%EB%AC%B8%EC%9D%84%20%EA%B8%88%ED%95%98%EB%9D%BC.pdf), [5회](attachments/%EC%9D%B8%ED%93%A8%EC%B2%98%EC%BB%A8%EC%84%A4%ED%8C%85%20%26%20%EC%9C%A0%EC%A0%95%EC%8B%9D%20__%20%EA%B5%AC%EA%B8%80%EC%9D%98%20%EC%B1%84%EC%9A%A9_%205.%20%EC%98%AC%EB%B0%94%EB%A5%B8%20%EC%A7%88%EB%AC%B8%EC%9D%84%20%EC%98%AC%EB%B0%94%EB%A5%B4%EA%B2%8C%20%ED%95%98%EB%9D%BC.pdf), [6회](attachments/%EC%9D%B8%ED%93%A8%EC%B2%98%EC%BB%A8%EC%84%A4%ED%8C%85%20%26%20%EC%9C%A0%EC%A0%95%EC%8B%9D%20__%20%EA%B5%AC%EA%B8%80%EC%9D%98%20%EC%B1%84%EC%9A%A9_%206.%20%EC%B1%84%EC%9A%A9%20%EA%B3%B5%EA%B3%A0%EB%8A%94%20%ED%9A%8C%EC%82%AC%EC%9D%98%20%EC%B2%AB%EC%9D%B8%EC%83%81%EC%9D%B4%EB%8B%A4.pdf), [7회](attachments/%EC%9D%B8%ED%93%A8%EC%B2%98%EC%BB%A8%EC%84%A4%ED%8C%85%20%26%20%EC%9C%A0%EC%A0%95%EC%8B%9D%20__%20%EA%B5%AC%EA%B8%80%EC%9D%98%20%EC%B1%84%EC%9A%A9_%207.%20%EC%9D%B4%EB%A0%A5%EC%84%9C%EB%A5%BC%20%EA%B3%B5%EC%A0%95%ED%95%98%EA%B2%8C%20%EA%B2%80%ED%86%A0%ED%95%98%EB%9D%BC.pdf), [8회](attachments/%EC%9D%B8%ED%93%A8%EC%B2%98%EC%BB%A8%EC%84%A4%ED%8C%85%20%26%20%EC%9C%A0%EC%A0%95%EC%8B%9D%20__%20%EA%B5%AC%EA%B8%80%EC%9D%98%20%EC%B1%84%EC%9A%A9_%208.%20%EB%A9%B4%EC%A0%91%EA%B4%80%EB%93%A4%EC%9D%84%20%EC%B2%A0%EC%A0%80%ED%9E%88%20%ED%9B%88%EB%A0%A8%EC%8B%9C%EC%BC%9C%EB%9D%BC.pdf))
* [Cracking the Coding Interview](https://www.crackingthecodinginterview.com/) (번역판: [코딩 인터뷰 완전 분석](https://blog.insightbook.co.kr/2017/08/07/%EC%BD%94%EB%94%A9-%EC%9D%B8%ED%84%B0%EB%B7%B0-%EC%99%84%EC%A0%84-%EB%B6%84%EC%84%9D-189%EA%B0%80%EC%A7%80-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%EB%AC%B8%EC%A0%9C%EC%99%80-%ED%95%B4%EB%B2%95/))

[\[top\]](#table-of-contents)

# Decision making

* [의사 결정의 심리적 편향을 없애라](https://dbr.donga.com/article/view/1306/article_no/2297/ac/magazine) ([cached](attachments/%EC%9D%98%EC%82%AC%EA%B2%B0%EC%A0%95%EC%9D%98%20%EC%8B%AC%EB%A6%AC%EC%A0%81%20%ED%8E%B8%ED%96%A5%EC%9D%84%20%EC%97%86%EC%95%A0%EB%9D%BC%20_%20%EB%A6%AC%EB%8D%94%EC%8B%AD%20_%20DBR.pdf)) - 틀 효과(framing effect), [확증 편향](https://ko.wikipedia.org/wiki/%ED%99%95%EC%A6%9D_%ED%8E%B8%ED%96%A5)(confirmation bias), 과신(overconfidence), [사후 판단 편향](https://brunch.co.kr/@summer9461/38)(hindsight bias)
* [매몰 비용의 오류](https://www.hbrkorea.com/article/view/atype/di/category_id/1_1/article_no/464/page/1)(sunk cost fallacy)
* [결합 오류](https://ko.wikipedia.org/wiki/%ED%9C%B4%EB%A6%AC%EC%8A%A4%ED%8B%B1_%EC%9D%B4%EB%A1%A0#%EA%B2%B0%ED%95%A9_%EC%98%A4%EB%A5%98)(conjunction fallacy)
* [결과 편향](https://infuture.kr/1335)(outcome bias) * 사후 판단 편향과 다름
* [모호성 회피](https://www.behavioraleconomics.com/resources/mini-encyclopedia-of-be/ambiguity-uncertainty-aversion/#:~:text=Ambiguity%20aversion%2C%20or%20uncertainty%20aversion,known%20risks%20over%20unknown%20risks.)(ambiguity aversion)
* [슬기로운 부장생활 1](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=240839541)

[\[top\]](#table-of-contents)

# Miscellaneous articles

* [How do Google engineers work?](google_engineering.md)
    * [An ex-Googler's guide to dev tools](https://news.ycombinator.com/item?id=25217291)
    * [xg2xg](https://github.com/jhuangtw/xg2xg)
    * Monorepo
        * https://trunkbaseddevelopment.com/monorepos/
        * [A Hacker News thread](https://news.ycombinator.com/item?id=25218175)
    * [Trunk-based development](https://cloud.google.com/architecture/devops/devops-tech-trunk-based-development)
* [Empathy is the most important leadership skill according to research](https://www.forbes.com/sites/tracybrower/2021/09/19/empathy-is-the-most-important-leadership-skill-according-to-research/) (Forbes) ([cached](attachments/Empathy%20Is%20The%20Most%20Important%20Leadership%20Skill%20According%20To%20Research.pdf))
* [The law of leaky abstractions](https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/) - Joel Spolsky (Wikipedia page: [link](https://en.wikipedia.org/wiki/Leaky_abstraction))
* [Teach yourself programming in ten years](https://norvig.com/21-days.html) - Peter Norvig
* [Politics and the English Language](https://www.orwell.ru/library/essays/politics/english/e_polit) - George Orwell (한글번역: [1](https://blog.daum.net/hjb009/8445446), [2](https://blog.daum.net/hjb009/8445446))
    * 다음은 '조지 오웰 산문선'에서 발췌하였음.
    1. 글에서 자주 본 은유, 직유, 기타 비유적 표현을 절대 사용하지 않는다.
    2. 짧은 단어로 충분할 때는 긴 단어를 절대 사용하지 않는다.
    3. 어떤 단어를 뺄 수 있을 때는 항상 뺀다.
    4. 능동태를 쓸 수 있을 때는 수동태를 절대 쓰지 않는다.
    5. 같은 뜻의 일상 영어가 생각나면 외래어 문구, 과학 용어, 전문 용어를 절대 쓰지 않는다.
    6. 아주 상스러운 말을 하느니 차라리 위의 원칙을 어긴다.
* [발표의 정석](attachments/%EB%B0%9C%ED%91%9C%EC%9D%98%20%EC%A0%95%EC%84%9D.pdf) - 하용호
* [The Evolution of CPU Processing Power](https://www.youtube.com/playlist?list=PLC7a8fNahjQ8IkiD5f7blIYrro9oeIfJU) - YouTube
* [The universal design pattern](http://steve-yegge.blogspot.com/2008/10/universal-design-pattern.html) - Steve Yegge (Reddit thread: [link](https://www.reddit.com/r/programming/comments/786qn/the_universal_design_pattern_steve_yegge/))
* [Good agile, bad agile](http://steve-yegge.blogspot.com/2006/09/good-agile-bad-agile_27.html) - Steve Yegge (Hacker News thread: [link](https://news.ycombinator.com/item?id=3616193))
* [A Beginner's Guide to Scaling to 11M+ Users on Amazon's AWS](https://news.ycombinator.com/item?id=10885727) (Related [video 1](https://youtu.be/4Lt8eOuS9zU) / [video 2](https://youtu.be/Ma3xWDXTxRg))
* [Designing Uber](http://highscalability.com/blog/2022/1/25/designing-uber.html)
* [Designing Netflix](http://highscalability.com/blog/2021/12/13/designing-netflix.html)
* [5 Lessons Learned From Writing Over 300,000 Lines of Infrastructure Code](https://blog.gruntwork.io/5-lessons-learned-from-writing-over-300-000-lines-of-infrastructure-code-36ba7fadeac1)
* [Elementary Algorithms](https://github.com/liuxinyu95/AlgoXY) - Xinyu LIU ([cached](attachments/algoxy-en.pdf))
* [Isomorphism - Mathematics of Programming](https://github.com/liuxinyu95/unplugged) - Xinyu LIU ([cached](attachments/unplugged-en.pdf))
* [Do Not Use MSA - 마이크로서비스 아키텍처가 꼭 필요한가요?](https://www.samsungsds.com/kr/insights/msa.html) ([cached](attachments/Do%20Not%20Use%20MSA%20-%20마이크로서비스%20아키텍처가%20꼭%20필요한가요_.pdf) / [alt.link](https://s-core.co.kr/insight/view/do-not-use-msa-%eb%a7%88%ec%9d%b4%ed%81%ac%eb%a1%9c%ec%84%9c%eb%b9%84%ec%8a%a4-%ec%95%84%ed%82%a4%ed%85%8d%ec%b2%98%ea%b0%80-%ea%bc%ad-%ed%95%84%ec%9a%94%ed%95%9c%ea%b0%80%ec%9a%94/))
* [Andrew Ng: Forget about building an AI-first business. Start with a mission.](https://www.technologyreview.com/2021/03/26/1021258/ai-pioneer-andrew-ng-machine-learning-business/) ([cached](attachments/Learning%20about%20AI%20with%20Google%20Brain%20and%20Landing%20AI%20founder%20Andrew%20Ng%20_%20MIT%20Technology%20Review.pdf))
* [Andrew Ng Launches A Campaign For Data-Centric AI](https://www.forbes.com/sites/gilpress/2021/06/16/andrew-ng-launches-a-campaign-for-data-centric-ai/) ([cached](attachments/Andrew%20Ng%20Launches%20A%20Campaign%20For%20Data-Centric%20AI.pdf))
* [Failure of IBM Watson](ibm_watson_failure.md) (articles in English and Korean)
* [Woowa Brothers' engineering culture](https://dbr.donga.com/article/view/1201/article_no/10410/ac/magazine) ([cached](attachments/%E2%80%9C%EC%A7%81%EA%B5%B0%EB%B3%84%20%ED%9A%A1%EC%A0%81%20%EC%A1%B0%EC%A7%81%EC%9C%BC%EB%A1%9C%20%E2%80%98%EC%82%AC%EC%9D%BC%EB%A1%9C%20%EB%AC%B8%EC%A0%9C%E2%80%99%20%ED%95%B4%EA%B2%B0%2C%20%EC%9E%A5%EC%95%A0%20%EB%B0%9C%EC%83%9D%20%EB%95%90%20%EA%B0%9C%EC%9D%B8%20%ED%83%93%20%EC%95%84%EB%8B%8C%20%EC%8B%9C%EC%8A%A4%ED%85%9C%20%EA%B0%9C%EC%84%A0%20%EC%A3%BC%EB%A0%A5%E2%80%9D%20_%20%EC%9D%B8%EC%82%AC_%EC%A1%B0%EC%A7%81%20_%20DBR.pdf))
* [Introduction to AUTOMATIC DIFFERENTIATION](https://alexey.radul.name/ideas/2013/introduction-to-automatic-differentiation/) ([cached](attachments/Introduction%20to%20Automatic%20Differentiation.pdf))
* [The Pivot to Web3 Is Going to Get People Hurt](https://www.vice.com/en/article/jgmyzk/the-pivot-to-web3-is-going-to-get-people-hurt) ([한글요약](https://parksehee.blog/2022/06/06/web3-hysteria/))

[\[top\]](#table-of-contents)
