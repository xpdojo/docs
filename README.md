# TDD

- [TDD](#tdd)
  - [개념](#개념)
    - [TDD 리듬(Rhythm)](#tdd-리듬rhythm)
  - [참고 자료](#참고-자료)
    - [Book](#book)
    - [Video](#video)
    - [Language](#language)
      - [Java](#java)
      - [Go](#go)
      - [Javascript](#javascript)
      - [Python](#python)
    - [같이 보기](#같이-보기)

## 개념

> TDD의 이름 자체에 '테스트'가 들어 있기는 하지만 사실 **TDD는 설계에 대한 실행 관례다.**

![tdd-global-lifecycle](image/tdd-global-lifecycle.png)

_출처: [위키피디아](https://en.wikipedia.org/wiki/Test-driven_development)_

### TDD 리듬(Rhythm)

<테스트 주도 개발>, 켄트 벡

1. 재빨리 **작은** 테스트를 하나 추가한다.
2. 🔴 모든 테스트를 실행하고, 실패하는 것을 확인한다.
3. 코드에 변화를 준다.
4. 🟢 모든 테스트를 실행하고, 성공하는 것을 확인한다.
   - 가짜로 구현하기: 상수로 반환하게 만들고 진짜 코드를 얻을 때까지 단계적으로 상수를 변수로 바꾸어 간다.
   - 명백한 구현 사용하기: 실제 구현을 입력한다.
   - 삼각측량(triangulation): 두 개 이상의 예제를 통해 코드를 일반화한다. 어떻게 리팩토링해야 하는지 전혀 감이 안 올 때만 삼각측량을 사용한다.
5. 🔵 중복을 제거하기 위해 리팩토링한다.

## 참고 자료

### Book

| 제목                                                                                                  | 저자                       | 링크                                                                              |
| ----------------------------------------------------------------------------------------------------- | -------------------------- | --------------------------------------------------------------------------------- |
| [소프트웨어 장인](books/the-software-craftsman.md)                                                    | 산드로 만쿠소              | [9791186659489](https://www.gilbut.co.kr/book/view?bookcode=BN001288)             |
| 테스트 주도 개발 - [Money 예제](https://github.com/tdd-kata/java/blob/main/money-kent-beck/README.md) | 켄트 벡                    | [9788966261024](https://www.aladin.co.kr/shop/wproduct.aspx?ISBN=9788966261024)   |
| [리팩터링 2판](books/refactoring-2.md)                                                                | 마틴 파울러                | [9791162242742](https://www.hanbit.co.kr/store/books/look.php?p_code=B6952616555) |
| 패턴을 활용한 리팩터링                                                                                | 조슈아 케리에브스키        | [9788991268920](https://www.aladin.co.kr/shop/wproduct.aspx?ISBN=9788991268920)   |
| 코드 컴플리트 2                                                                                       | 스티브 맥코넬              | [9791158390600](https://wikibook.co.kr/code-complete-2/)                          |
| 테스트 주도 개발로 배우는 객체 지향 설계와 실천                                                       | 스티브 프리먼, 냇 프라이스 | [9788966260843](http://ebook.insightbook.co.kr/book/19)                           |
| 클린 코드                                                                                             | 로버트 C. 마틴             | [9788966262724](http://ebook.insightbook.co.kr/book/79)                           |
| 클린 코더                                                                                             | 로버트 C. 마틴             | [9788960778818](http://www.acornpub.co.kr/book/clean-coder)                       |
| 클린 소프트웨어                                                                                       | 로버트 C. 마틴             | [9791185890852](https://jpub.tistory.com/682)                                     |

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
