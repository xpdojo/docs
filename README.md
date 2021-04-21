# TDD

- [TDD](#tdd)
  - [참고 자료](#참고-자료)
    - [Book](#book)
    - [Article](#article)
    - [Video](#video)
    - [Language](#language)
      - [Java](#java)
      - [Go](#go)
      - [Javascript](#javascript)
      - [Python](#python)
    - [같이 보기](#같이-보기)
  - [개념](#개념)
    - [TDD 리듬(Rhythm)](#tdd-리듬rhythm)
  - [관련 용어](#관련-용어)
    - [간접 입력 (Indirect Input)](#간접-입력-indirect-input)
    - [간접 출력 (Indirect Output)](#간접-출력-indirect-output)
    - [`SUT`](#sut)
    - [`DOC`](#doc)
    - [Test Fixture (Test Context)](#test-fixture-test-context)
    - [Test Suite](#test-suite)
    - [테스트 유형](#테스트-유형)
      - [Unit Test](#unit-test)
      - [Integration Test](#integration-test)
      - [Functional Test](#functional-test)
      - [End to End Test](#end-to-end-test)
      - [Acceptance Test](#acceptance-test)
      - [Customer Test](#customer-test)
    - [테스트 더블 test double](#테스트-더블-test-double)
      - [Dummy](#dummy)
      - [Fake](#fake)
      - [Stub](#stub)
      - [Spy](#spy)
      - [Mock](#mock)

## 참고 자료

### Book

| 제목                                                                                                  | 저자                       | 링크                                                                              |
| ----------------------------------------------------------------------------------------------------- | -------------------------- | --------------------------------------------------------------------------------- |
| [소프트웨어 장인](books/the-software-craftsman.md)                                                    | 산드로 만쿠소              | [9791186659489](https://www.gilbut.co.kr/book/view?bookcode=BN001288)             |
| 테스트 주도 개발 - [Money 예제](https://github.com/tdd-kata/java/blob/main/money-kent-beck/README.md) | 켄트 벡                    | [9788966261024](https://www.aladin.co.kr/shop/wproduct.aspx?ISBN=9788966261024)   |
| xUnit 테스트 패턴                                                                                     | 제라드 메스자로스          | [Website for Book](http://xunitpatterns.com/index.html)                           |
| [리팩터링 2판](books/refactoring-2.md)                                                                | 마틴 파울러                | [9791162242742](https://www.hanbit.co.kr/store/books/look.php?p_code=B6952616555) |
| 패턴을 활용한 리팩터링                                                                                | 조슈아 케리에브스키        | [9788991268920](https://www.aladin.co.kr/shop/wproduct.aspx?ISBN=9788991268920)   |
| 코드 컴플리트 2                                                                                       | 스티브 맥코넬              | [9791158390600](https://wikibook.co.kr/code-complete-2/)                          |
| 테스트 주도 개발로 배우는 객체 지향 설계와 실천                                                       | 스티브 프리먼, 냇 프라이스 | [9788966260843](http://ebook.insightbook.co.kr/book/19)                           |
| 클린 코드                                                                                             | 로버트 C. 마틴             | [9788966262724](http://ebook.insightbook.co.kr/book/79)                           |
| 클린 코더                                                                                             | 로버트 C. 마틴             | [9788960778818](http://www.acornpub.co.kr/book/clean-coder)                       |
| 클린 소프트웨어                                                                                       | 로버트 C. 마틴             | [9791185890852](https://jpub.tistory.com/682)                                     |

### Article

- [Mocks, Fakes, Stubs and Dummies](http://xunitpatterns.com/Mocks,%20Fakes,%20Stubs%20and%20Dummies.html) - xUnit Patterns
- [The different types of software testing](https://www.atlassian.com/continuous-delivery/software-testing/types-of-software-testing) - Atlassian CI/CD
- [Test 관련 용어 정리](https://johngrib.github.io/wiki/test-terms/) - 이종립 (기계인간 John Grib)
- [정말로 테스트 대역이 필요한가](https://gyuwon.github.io/blog/2020/05/10/do-you-really-need-test-doubles.html) - 이규원
- [TestDouble](https://www.martinfowler.com/bliki/TestDouble.html) - Martin Fowler
- [Mocks Aren't Stubs](https://www.martinfowler.com/articles/mocksArentStubs.html) - Martin Fowler ([번역](https://sites.google.com/a/jabberstory.net/testing/mocksArentStubs))

### Video

| 제목                                       | 저자                                                 | 링크                                                                                                   |
| ------------------------------------------ | ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| TDD 리팩토링                               | 자바지기 박재성                                      | [Youtube](https://youtu.be/bIeqAlmNRrA)                                                                |
| 현실 세상의 TDD                            | 이규원                                               | [fastcampus](https://www.fastcampus.co.kr/dev_red_ygw), [GitHub](https://github.com/gyuwon/TDDHandsOn) |
| 자바와 JUnit을 활용한 실용주의 단위 테스트 | 제프 랭어, 앤디 헌트, 데이브 토마스                  | [9791160508383](https://www.aladin.co.kr/shop/wproduct.aspx?ISBN=9791160508383)                        |
| JUnit in Action (3rd)                      | 피터 타치브, 펠리페 레미, 빈센트 마솔, 게리 그레고리 | [9781617297045](https://www.manning.com/books/junit-in-action-third-edition)                           |

### Language

#### Java

| 제목                                     | 저자                            | 링크                                                                                |
| ---------------------------------------- | ------------------------------- | ----------------------------------------------------------------------------------- |
| 테스트 주도 개발 시작하기                | 최범균                          | [9788980783052](https://www.aladin.co.kr/shop/wproduct.aspx?ISBN=9788980783052)     |
| Test Driven Development with Spring Boot | Sannidhi Jalukar, Madhura Bhave | [Youtube](https://youtu.be/s9vt6UJiHg4)                                             |
| Java TDD 실습                            | 아샬                            | [Youtube](https://www.youtube.com/playlist?list=PLbdtsbZUwdeRirBYnWrMSvKYS4CcmXCeU) |

#### Go

| 제목                | 저자        | 링크                                                              |
| ------------------- | ----------- | ----------------------------------------------------------------- |
| Learn Go with Tests | Chris James | [Git Book](https://github.com/MiryangJung/learn-go-with-tests-ko) |

#### Javascript

| 제목                                              | 저자   | 링크                                    |
| ------------------------------------------------- | ------ | --------------------------------------- |
| 프론트엔드에서 TDD가 가능하다는 것을 보여드립니다 | 최수형 | [Youtube](https://youtu.be/L1dtkLeIz-M) |

#### Python

| 제목                                | 저자             | 링크                                                                            |
| ----------------------------------- | ---------------- | ------------------------------------------------------------------------------- |
| 우아하게 준비하는 테스트와 리팩토링 | 한성민           | [Youtube](https://youtu.be/S5SY2pkmOy0)                                         |
| 클린 코드를 위한 테스트 주도 개발   | 해리 J.W. 퍼시벌 | [9788994774916](https://www.aladin.co.kr/shop/wproduct.aspx?ISBN=9788994774916) |

### 같이 보기

| 제목                           | 저자                           | 링크                                                                                                                |
| ------------------------------ | ------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| 함께 자라기                    | 김창준                         | [9788966262373](http://ebook.insightbook.co.kr/book/65)                                                             |
| 실용주의 프로그래머            | 데이비드 토머스, 앤드류 헌트   | [9788966261031](https://www.aladin.co.kr/shop/wproduct.aspx?ISBN=9788966261031)                                     |
| 실용주의 사고와 학습           | 앤디 헌트                      | [9788992939362](https://wikibook.co.kr/pragmatic-thinking-and-learning/)                                            |
| 프로그래머의 길, 멘토에게 묻다 | 데이브 후버, 애디웨일 오시나이 | [8991268803](https://www.aladin.co.kr/shop/wproduct.aspx?ISBN=8991268803)                                           |
| 클린 아키텍처                  | 로버트 C. 마틴                 | [9788966262472](https://blog.insightbook.co.kr/2019/08/08/%ED%81%B4%EB%A6%B0-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98/) |
| Clean Architecture and Design  | 로버트 C. 마틴                 | [amara (한글 자막)](https://amara.org/ko/videos/0AtjY87egE3m/ko/796487/)                                            |
| 객체 지향의 사실과 오해        | 조영호                         | [9788998139766](https://wikibook.co.kr/object-orientation/)                                                         |
| 오브젝트                       | 조영호                         | [9791158391409](https://wikibook.co.kr/object/)                                                                     |

## 개념

> "TDD의 이름 자체에 '테스트'가 들어 있기는 하지만 사실 **TDD는 설계에 대한 실행 관례다.**" - <소프트웨어 장인>

![tdd-global-lifecycle](image/tdd-global-lifecycle.png)

_출처: [위키피디아](https://en.wikipedia.org/wiki/Test-driven_development)_

### TDD 리듬(Rhythm)

<테스트 주도 개발>, 켄트 벡

1. 재빨리 **작은** 테스트를 하나 추가합니다.
2. 🔴 모든 테스트를 실행하고, 실패하는 것을 확인합니다.
3. 코드에 변화를 줍니다.
4. 🟢 모든 테스트를 실행하고, 성공하는 것을 확인합니다.
   - 가짜로 구현하기: 상수로 반환하게 만들고 진짜 코드를 얻을 때까지 단계적으로 상수를 변수로 바꾸어 갑니다.
   - 명백한 구현 사용하기: 실제 구현을 입력합니다.
   - 삼각측량(triangulation): 두 개 이상의 예제를 통해 코드를 일반화합니다. 어떻게 리팩토링해야 하는지 전혀 감이 안 올 때만 삼각측량을 사용합니다.
5. 🔵 중복을 제거하기 위해 리팩토링합니다.

## 관련 용어

### 간접 입력 (Indirect Input)

입력된 의존성 인터페이스를 통한 입력을 말합니다(의존성 관점에서는 출력).
SUT의 동작이 SUT에서 사용하는 다른 서비스 컴포넌트에서 리턴하는 값에 영향을 받을 때
이런 값들을 SUT의 간접 입력이라 합니다.

### 간접 출력 (Indirect Output)

입력된 의존성 인터페이스를 통한 출력을 말합니다(의존성 관점에서는 입력).
SUT의 동작에 따른 효과를 public 애플리케이션 인터페이스(API)에서는 볼 수 없고
다른 시스템이나 애플리케이션 컴포넌트에서만 볼 수 있을 때 이런 효과를 SUT의 간접 출력이라 합니다.

### `SUT`

[System Under Test](http://xunitpatterns.com/SUT.html).
"테스트하려는 대상"을 의미합니다.
SUT는 항상 테스트를 기준으로 정의됩니다.
단위 테스트를 작성할 때 SUT는 테스트하려는 클래스(CUT), 오브젝트(OUT) 또는 메서드(MUT)가 됩니다.
[고객 테스트](https://explainagile.com/agile/xp-extreme-programming/practices/customer-tests/)를 작성할 때
SUT는 아마도 애플리케이션 전체(AUT)이거나 적어도 주요 서브 시스템일 것입니다.
애플리케이션에서 특정 테스트의 검증 대상이 아닌 부분도 여전히
의존 컴포넌트(`DOC`)로서 테스트와 연관돼 있을 수 있습니다.

### `DOC`

[depended-on component](http://xunitpatterns.com/DOC.html).
SUT가 의존하는 개별 클래스나 느슨한 컴포넌트(large-grained component)를 말합니다.
의존은 보통 메소드 호출을 통해 위임하는 방식 중 하나입니다.
테스트 자동화에서 완벽한 테스트 커버리지를 얻으려면 주로 DOC와 SUT 간의 상호작용을 보고 제어할 수 있어야 합니다.

### Test Fixture (Test Context)

테스트 픽처란 SUT의 동작을 검증하기 위해 테스트를 실행하려 할 때 갖춰야 하는 모든 것을 말합니다.

### Test Suite

테스트 스위트란 같이 실행하고 싶은 테스트들의 모음(composite)에 이름을 붙여주는 방법을 말합니다.

### [테스트 유형](https://www.atlassian.com/continuous-delivery/software-testing/types-of-software-testing)

| -                                     | Unit Test                  | Acceptance Test                        |
| ------------------------------------- | -------------------------- | -------------------------------------- |
| 관점                                  | 최종 클라이언트            | 프로그래머                             |
| 검증 대상                             | 시스템의 일부(하위 시스템) | 배치된 시스템                          |
| 안정감 (전체 시스템 이상 여부 신뢰도) | 상대적으로 낮음            | 높음                                   |
| 비용 (작성/관리/실행)                 | 낮음                       | 높음                                   |
| 피드백 품질                           | 높음                       | 낮음 (현상은 드러나지만 원인은 숨겨짐) |

_출처: 현실 세상의 TDD - 이규원_

#### Unit Test

단위 테스트는 애플리케이션 내부의 한 부분이 의도한 대로 동작하는지 검증합니다.

#### Integration Test

통합 테스트는 애플리케이션에서 사용하는 여러 모듈 또는 서비스가 함께 잘 작동하는지 확인합니다.
여기서 모듈은 모든 모듈이 아닌 해당 테스트가 의존하는 모듈만을 일컫습니다.
통합 테스트는 단순히 데이터베이스를 쿼리 할 수 ​​있는지 확인합니다.

#### Functional Test

기능 테스트는 애플리케이션 최종 사용자의 기능에 대한 블랙박스 테스트를 말합니다.

#### End to End Test

통합 테스트가 몇 가지 애플리케이션 간 동작을 테스트한다면
E2E 테스트는 소프트웨어가 사용자의 단계별 행동을 그대로 시뮬레이션하고 테스트합니다.

#### Acceptance Test

인수 테스트(승인 테스트)는 시스템이 비즈니스 요구 사항을 충족하는지 확인하기 위해 수행되는 테스트입니다.
애플리케이션이 프로그래머가 생각한 대로가 아닌 고객이 의도한 대로 동작하는 것을 증명하는 것이 목적입니다.

#### Customer Test

고객 테스트는 전체 시스템 중에서 눈에 보이는 기능의 일부분에 대한 동작을 검증하는 테스트입니다.

### [테스트 더블](http://xunitpatterns.com/Test%20Double.html) test double

- 테스트 코드를 작성할 때 실제 DOC를 사용할 수 없다면, DOC 대신 테스트 더블로 대체할 수 있습니다.
- 테스트 더블은 실제 DOC와 똑같이 행동하지 않아도 되며, 똑같은 API만 제공하면 됩니다.
- 테스트 더블은 테스트 목적을 위해 프로덕션 객체를 다른 무언가로 교체하는 모든 경우를 표현하는 용어입니다.

#### Dummy

SUT 메서드 인자에 구현이 전혀 안 돼 있는 객체를 전달합니다.
SUT 준비를 위해 해결되어야 하는 의존성이 테스트 대상 논리에 의해 사용되지 않는 경우에 의존 요소를 대신하는 테스트 대역입니다.

#### Fake

실제로 작동하는 구현이지만 일반적으로 프로덕션에는 적합하지 않은 꼼수(shortcut)를 사용합니다.
([InMemoryTestDatabase](https://www.martinfowler.com/bliki/InMemoryTestDatabase.html)가 좋은 예)
실행할 수 없는 테스트를 빠르게 실행하기 위해 사용됩니다.

#### Stub

테스트 중에 호출되면 미리 준비된 결과를 제공합니다.
즉, 실제 객체를 테스트용 객체로 교체해 SUT에 원하는 **간접 입력**을 보냅니다.

#### Spy

SUT로부터 다른 컴포넌트로의 **간접 출력**을 갈무리했다가 뒤에 테스트에서 검증합니다.

#### Mock

호출했을 때 사전에 정의된 명세대로의 결과를 돌려주도록 미리 프로그램 되어 있습니다.
예상치 못한 호출이 있을 경우 예외를 던질 수 있으며, 모든 호출이 예상된 것이었는지 확인할 수 있습니다.
SUT 내부의 행위를 검증합니다.
SUT의 **간접 출력**을 검증하기 위해 사용됩니다.
