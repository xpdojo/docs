# 리팩터링 2판

> 마틴 파울러

- [리팩터링 2판](#리팩터링-2판)
  - [리팩터링 첫 단계](#리팩터링-첫-단계)
  - [리팩터링 원칙](#리팩터링-원칙)
    - [리팩터링하는 이유](#리팩터링하는-이유)
    - [언제 리팩터링해야 할까?](#언제-리팩터링해야-할까)
  - [코드에서 나는 악취 - 켄트 벡 공저](#코드에서-나는-악취---켄트-벡-공저)
  - [테스트 구축하기](#테스트-구축하기)
  - [리팩터링 카탈로그](#리팩터링-카탈로그)
    - [기본적인 리팩터링](#기본적인-리팩터링)
      - [함수 추출하기](#함수-추출하기)
      - [함수 인라인하기](#함수-인라인하기)
      - [변수 추출하기](#변수-추출하기)
      - [변수 인라인하기](#변수-인라인하기)
      - [함수 선언 바꾸기](#함수-선언-바꾸기)
      - [변수 캡슐화하기](#변수-캡슐화하기)
      - [변수 이름 바꾸기](#변수-이름-바꾸기)
      - [매개변수 객체 만들기](#매개변수-객체-만들기)
      - [여러 함수를 클래스로 묶기](#여러-함수를-클래스로-묶기)
      - [여러 함수를 변환 함수로 묶기](#여러-함수를-변환-함수로-묶기)
      - [단계 쪼개기](#단계-쪼개기)
    - [캡슐화](#캡슐화)
      - [레코드 캡슐화하기](#레코드-캡슐화하기)
      - [컬렉션 캡슐화하기](#컬렉션-캡슐화하기)
      - [기본형을 객체로 바꾸기](#기본형을-객체로-바꾸기)
      - [임시 변수를 질의 함수로 바꾸기](#임시-변수를-질의-함수로-바꾸기)
      - [클래스 추출하기](#클래스-추출하기)
      - [클래스 인라인하기](#클래스-인라인하기)
      - [위임 숨기기](#위임-숨기기)
      - [중개자 제거하기](#중개자-제거하기)
      - [알고리즘 교체하기](#알고리즘-교체하기)
    - [기능 이동](#기능-이동)
      - [함수 옮기기](#함수-옮기기)
      - [필드 옮기기](#필드-옮기기)
      - [문장을 함수로 옮기기](#문장을-함수로-옮기기)
      - [문장을 호출한 곳으로 옮기기](#문장을-호출한-곳으로-옮기기)
      - [인라인 코드를 함수 호출로 바꾸기](#인라인-코드를-함수-호출로-바꾸기)
      - [문장 슬라이드하기](#문장-슬라이드하기)
      - [반복문 쪼개기](#반복문-쪼개기)
      - [반복문을 파이프라인으로 바꾸기](#반복문을-파이프라인으로-바꾸기)
      - [죽은 코드 제거하기](#죽은-코드-제거하기)
    - [데이터 조직화](#데이터-조직화)
      - [변수 쪼개기](#변수-쪼개기)
      - [필드 이름 바꾸기](#필드-이름-바꾸기)
      - [파생 변수를 질의 함수로 바꾸기](#파생-변수를-질의-함수로-바꾸기)
      - [참조를 값으로 바꾸기](#참조를-값으로-바꾸기)
      - [값을 참조로 바꾸기](#값을-참조로-바꾸기)
      - [매직 리터럴 바꾸기](#매직-리터럴-바꾸기)
    - [조건부 로직 간소화](#조건부-로직-간소화)
      - [조건문 분해하기](#조건문-분해하기)
      - [조건식 통합하기](#조건식-통합하기)
      - [중첩 조건문을 보호 구문으로 바꾸기](#중첩-조건문을-보호-구문으로-바꾸기)
      - [조건부 로직을 다형성으로 바꾸기](#조건부-로직을-다형성으로-바꾸기)
      - [특이 케이스 추가하기](#특이-케이스-추가하기)
      - [어서션 추가하기](#어서션-추가하기)
      - [제어 플래그를 탈출문으로 바꾸기](#제어-플래그를-탈출문으로-바꾸기)
    - [API 리팩터링](#api-리팩터링)
      - [질의 함수와 변경 함수 분리하기](#질의-함수와-변경-함수-분리하기)
      - [함수 매개변수화하기](#함수-매개변수화하기)
      - [플래그 인수 제거하기](#플래그-인수-제거하기)
      - [객체 통째로 넘기기](#객체-통째로-넘기기)
      - [매개변수를 질의 함수로 바꾸기](#매개변수를-질의-함수로-바꾸기)
      - [질의 함수를 매개변수로 바꾸기](#질의-함수를-매개변수로-바꾸기)
      - [세터 제거하기](#세터-제거하기)
      - [생성자를 팩터리 함수로 바꾸기](#생성자를-팩터리-함수로-바꾸기)
      - [함수를 명령으로 바꾸기](#함수를-명령으로-바꾸기)
      - [명령을 함수로 바꾸기](#명령을-함수로-바꾸기)
      - [수정된 값 반환하기](#수정된-값-반환하기)
      - [오류 코드를 예외로 바꾸기](#오류-코드를-예외로-바꾸기)
      - [예외를 사전확인으로 바꾸기](#예외를-사전확인으로-바꾸기)
    - [상속 다루기](#상속-다루기)
      - [메서드 올리기](#메서드-올리기)
      - [필드 올리기](#필드-올리기)
      - [생성자 본문 올리기](#생성자-본문-올리기)
      - [메서드 내리기](#메서드-내리기)
      - [필드 내리기](#필드-내리기)
      - [타입 코드를 서브클래스로 바꾸기](#타입-코드를-서브클래스로-바꾸기)
      - [서브클래스 제거하기](#서브클래스-제거하기)
      - [슈퍼클래스 추출하기](#슈퍼클래스-추출하기)
      - [계층 합치기](#계층-합치기)
      - [서브클래스를 위임으로 바꾸기](#서브클래스를-위임으로-바꾸기)
      - [슈퍼클래스를 위임으로 바꾸기](#슈퍼클래스를-위임으로-바꾸기)

> 같은 프로젝트를 여러 번 부숴 본다. 프로젝트 레이아웃을 변경한다던지 클래스를 나눠 본다던지 마음껏 부수다 보면 여기서 말하는 냄새들을 맡아볼 수 있다.

## 리팩터링 첫 단계

리팩터링하기 전에 제대로 된 테스트부터 마련한다.
테스트는 반드시 자가진단하도록 만든다.

나는 리팩터링 시 테스트에 상당히 의지한다.
내가 저지른 실수로부터 보호해주는 버그 검출기 역할을 해주기 때문이다.

...
이러한 사실은 코드를 분석해서 얻은 정보다.
워드 커닝햄(Ward Cunningham)이 말하길, 이런 식으로 파악한 정보는
휘발성이 높기로 악명 높은 저장 장치인 내 머릿속에 기록되므로,
잊지 않으려면 재빨리 코드에 반영해야 한다.
...

컴퓨터가 이해하는 코드는 바보도 작성할 수 있다.
사람이 이해하도록 작성하는 프로그래머가 진정한 실력자다.

...
반복문을 쪼개서 성능이 느려지지 않을까 걱정할 수 있다.
이처럼 반복문이 중복되는 것을 꺼리는 이들이 많지만,
이 정도 중복은 성능에 미치는 영향이 미미할 때가 많다.
경험 많은 프로그래머조차 코드의 실제 성능을 정확히 예측하지 못한다.
똑똑한 컴파일러들은 최신 캐싱 기법 등으로 무장하고 있어서
우리의 직관을 초월하는 결과를 내어주기 때문이다.
...

좋은 코드를 가늠하는 확실한 방법은 '얼마나 수정하기 쉬운가'다.

1장의 예시를 통해 배울 수 있는 가장 중요한 것은 바로 리팩터링하는 리듬이다.
사람들에게 내가 리팩터링하는 과정을 보여줄 때마다,
각 단계를 굉장히 잘게 나누고 매번 컴파일하고 테스트하여 작동하는 상태로 유지한다는 사실에 놀란다.
나도 20년 전에 디트로이트의 어느 호텔방에서 켄트 벡이 이렇게 작업하는 것을 처음 봤을 때 비슷한 심정이었다.
리팩터링을 효과적으로 하는 핵심은, 단계를 잘게 나눠야 더 빠르게 처리할 수 있고,
코드는 절대 깨지지 않으며, 이러한 작은 단계들이 모여서 상당히 큰 변화를 이룰 수 있다는 사실을 깨닫는 것이다.

## 리팩터링 원칙

리팩터링? `[verb]` 소프트웨어의 겉보기 동작(observable behavior)은 그대로 유지한 채, 여러 가지 리팩터링 기법을 적용해서 소프트웨어를 재구성(restructuring)하다.

누군가 "리팩터링하다가 코드가 깨져서 며칠이나 고생했다"라고 한다면 십중팔구 리팩터링한 것이 아니다.

나는 소프트웨어를 개발할 때 목적이 '기능 추가'냐, 아니면 '리팩터링'이냐를 명확히 구분해 작업한다.
켄트 벡은 이를 두 개의 모자(two hats)에 비유했다.

- 기능을 추가할 때는 '기능 추가' 모자를 쓴 다음 기존 코드는 절대 건드리지 않고 새 기능을 추가하기만 한다.
  - 진척도는 테스트를 추가해서 통과하는지 확인하는 방식으로 측정한다.
- 반면 리팩터링할 때는 '리팩터링'모자를 쓴 다음 기능 추가는 절대 하지 않기로 다짐한 뒤 오로지 코드 재구성에만 전념한다.
  - 앞 과정에서 놓친 테스트 케이스를 발견하지 않는 한 테스트도 새로 만들지 않는다.

소프트웨어를 개발하는 동안 나는 두 모자를 자주 바꿔 쓴다.
새 기능을 추가하다 보면 코드 구조를 바꿔야 작업하기 훨씬 쉽겠다는 생각이 들기도 하는데,
그러면 잠시 모자를 바꿔 쓰고 리팩터링한다.

### 리팩터링하는 이유

- 리팩터링하면 소프트웨어 설계가 좋아진다.
- 리팩터링하면 소프트웨어를 이해하기 쉬워진다.
  - 난 굉장히 게으른 프로그래머다.
    단적인 예로 내가 작성한 코드를 전혀 머리에 담아두지 않는다.
    다시 말해 코드를 보면 알 수 있는 것들은 의도적으로 기억하지 않는다.
    내 기억 용량을 초과할까봐 두렵기 때문이다.
    그래서 기억할 필요가 있는 것들은 최대한 코드에 담으려고 한다.
    그러면 모디뜨(Maudite) 맥주가 뇌세포를 파괴하더라도 걱정할 필요가 없다.
- 리팩터링하면 버그를 쉽게 찾을 수 있다.
- 리팩터링하면 프로그래밍 속도를 높일 수 있다.

### 언제 리팩터링해야 할까?

- 준비를 위한 리팩터링 | Preparatory Refactoring
  - 리팩터링하기 가장 좋은 시점은 코드베이스에 기능을 새로 추가하기 직전이다.
  - 이 시점에 현재 코드를 살펴보면서, 구조를 살짝 바꾸면 다른 작업을 하기가 훨씬 쉬워질 만한 부분을 찾는다.
- 이해를 위한 리팩터링 | Comprehension Refactoring
  - 코드의 의도가 더 명확하게 드러나도록 리팩터링할 여지는 없는지 찾아본다.
- 쓰레기 줍기 리팩터링 | Litter-Pickup Refactoring
  - 코드를 파악하던 중에 비효율적으로 처리하는 모습을 발견할 때가 있다.
  - 간단히 수정할 수 있는 것은 즉시 고친다.
  - 시간이 좀 걸리는 일은 짧은 메모만 남긴 다음, 하던 일을 끝내고 나서 처리한다.
  - 물론 수정하려면 몇 시간이나 걸리고 당장은 더 급한 일이 있을 수 있다. 그렇더라도 조금이나마 개선해두는 것이 좋다.
- 계획된 리팩터링과 수시로 하는 리팩터링
  - 리팩터링은 프로그래밍과 구분되는 별개의 활동이 아니다. 리팩터링 시간을 일정에 따로 잡아두지 않고, 대부분의 리팩터링을 다른 일을 하는 중에 처리한다.
  - 보기 싫은 코드를 보면 리팩터링해야 함은 당연하지만, 잘 작성된 코드 역시 수많은 리팩터링을 거쳐야 한다.
  - 어제는 적합했던 기준이 오늘 하는 다른 작업에는 맞지 않을 수 있다. 이렇게 상황이 변해 기준을 변경해야 할 때 코드가 이미 깔끔하다면 리팩터링하기가 더 쉽다.
  - "무언가 수정하려 할 때는 먼저 수정하기 쉽게 정돈하고(단, 만만치 않을 수 있다) 그런 다음 쉽게 수정하자." - 켄트 벡
  - 그동안 리팩터링에 소홀했다면, 따로 시간을 내서 새 기능을 추가하기 쉽도록 코드베이스를 개선할 필요가 있다.
  - 계획된 리팩터링을 하게 되는 일은 최소한으로 줄여야 한다. 리팩터링 작업 대부분은 드러나지 않게, 기회가 될 때마다 해야 한다.
- 오래 걸리는 리팩터링
  - 팀 전체가 리팩터링에 매달리는 것보다 주어진 문제를 몇 주에 걸쳐 조금씩 해결해가는 편이 효과적일 때가 많다.
  - 누구든지 리팩터링해야 할 코드와 관련한 작업을 하게 될 때마다 원하는 방향으로 조금씩 개선하는 식이다.
- 코드 리뷰에 리팩터링 활용하기
  - 내 눈에는 명확한 코드가 다른 팀원에게는 그렇지 않을 수 있다. 자신이 하는 일에 익숙하지 않은 사람의 관점에서 바라보기란 누구에게나 어렵기 때문이다.
  - 코드 작성자 없이 검토하는 Pull Request 모델보다 나란히 앉아 코드를 훑어가면서 리팩터링하는 Pair Programming이 더 효과적이다. 작성자가 맥락을 설명해줄 수 있고 리뷰어의 변경 의도를 제대로 이해할 수 있기 때문이다.
- 리팩터링하지 말아야 할 때
  - 지저분한 코드를 발견해도 굳이 수정할 필요가 없다면 리팩터링하지 않는다. 외부 API 다루듯 호출해서 쓰는 코드라면 지저분해도 그냥 둔다. 내부 동작을 이해해야 할 시점에 리팩터링해야 효과를 제대로 볼 수 있다.
  - 리팩터링하는 것보다 처음부터 새로 작성하는 게 쉬울 때도 리팩터링하지 않는다. 직접 리팩터링해보기 전에는 처음부터 새로 작성하는 게 더 쉬운지 확실히 알 수 없을 때도 많다. 리팩터링할지 새로 작성할지를 잘 결정하려면 뛰어난 판단력과 경험이 뒷받침돼야 한다.

## 코드에서 나는 악취 - 켄트 벡 공저

| #   | 악취                                 | Smell                                         | 탈취 리팩터링                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| --- | ------------------------------------ | --------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | 기이한 이름                          | Mysterious Name                               | [함수 선언 바꾸기](#함수-선언-바꾸기), [변수 이름 바꾸기](#변수-이름-바꾸기), [필드 이름 바꾸기](#필드-이름-바꾸기)                                                                                                                                                                                                                                                                                                                                                                      |
| 2   | 중복 코드                            | Duplicated Code                               | [함수 추출하기](#함수-추출하기), [문장 슬라이드하기](#문장-슬라이드하기), [메서드 올리기](#메서드-올리기)                                                                                                                                                                                                                                                                                                                                                                                |
| 3   | 긴 함수                              | Long Function                                 | [함수 추출하기](#함수-추출하기), [임시 변수를 질의 함수로 바꾸기](#임시-변수를-질의-함수로-바꾸기), [매개변수 객체 만들기](#매개변수-객체-만들기), [객체 통째로 넘기기](#객체-통째로-넘기기), [함수를 명령으로 바꾸기](#함수를-명령으로-바꾸기), [조건문 분해하기](#조건문-분해하기), [조건부 로직을 다형성으로 바꾸기](#조건부-로직을-다형성으로-바꾸기), [반복문 쪼개기](#반복문-쪼개기)                                                                                               |
| 4   | 긴 매개변수 목록                     | Long Parameter List                           | [매개변수를 질의 함수로 바꾸기](#매개변수를-질의-함수로-바꾸기), [객체 통째로 넘기기](#객체-통째로-넘기기), [매개변수 객체 만들기](#매개변수-객체-만들기), [플래그 인수 제거하기](#플래그-인수-제거하기), [여러 함수를 클래스로 묶기](#여러-함수를-클래스로-묶기)                                                                                                                                                                                                                        |
| 5   | 전역 데이터                          | Global Data                                   | [변수 캡슐화하기](#변수-캡슐화하기)                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| 6   | 가변 데이터                          | Mutable Data                                  | [변수 캡슐화하기](#변수-캡슐화하기), [변수 쪼개기](#변수-쪼개기), [문장 슬라이드하기](#문장-슬라이드하기), [함수 추출하기](#함수-추출하기), [질의 함수와 변경 함수 분리하기](#질의-함수와-변경-함수-분리하기), [세터 제거하기](#세터-제거하기), [파생 변수를 질의 함수로 바꾸기](#파생-변수를-질의-함수로-바꾸기), [여러 함수를 클래스로 묶기](#여러-함수를-클래스로-묶기), [여러 함수를 변환 함수로 묶기](#여러-함수를-변환-함수로-묶기), [참조를 값으로 바꾸기](#참조를-값으로-바꾸기) |
| 7   | 뒤엉킨 변경                          | Divergent Change                              | [단계 쪼개기](#단계-쪼개기), [함수 옮기기](#함수-옮기기), [함수 추출하기](#함수-추출하기), [클래스 추출하기](#클래스-추출하기)                                                                                                                                                                                                                                                                                                                                                           |
| 8   | 산탄총 수술                          | Shotgun Surgery                               | [함수 옮기기](#함수-옮기기), [필드 옮기기](#필드-옮기기), [여러 함수를 클래스로 묶기](#여러-함수를-클래스로-묶기), [여러 함수를 변환 함수로 묵기](#여러-함수를-변환-함수로-묶기), [단계 쪼개기](#단계-쪼개기), [함수 인라인하기](#함수-인라인하기), [클래스 인라인하기](#클래스-인라인하기)                                                                                                                                                                                              |
| 9   | 기능 편애                            | Feature Envy                                  | [함수 옮기기](#함수-옮기기), [함수 추출하기](#함수-추출하기)                                                                                                                                                                                                                                                                                                                                                                                                                             |
| 10  | 데이터 뭉치                          | Data Clumps                                   | [클래스 추출하기](#클래스-추출하기), [매개변수 객체 만들기](#매개변수-객체-만들기), [객체 통째로 넘기기](#객체-통째로-넘기기)                                                                                                                                                                                                                                                                                                                                                            |
| 11  | 기본형 집착                          | Primitive Obsession                           | [기본형을 객체로 바꾸기](#기본형을-객체로-바꾸기), [타입 코드를 서브클래스로 바꾸기](#타입-코드를-서브클래스로-바꾸기), [조건부 로직을 다형성으로 바꾸기](#조건부-로직을-다형성으로-바꾸기), [클래스 추출하기](#클래스-추출하기), [매개변수 객체 만들기](#매개변수-객체-만들기)                                                                                                                                                                                                          |
| 12  | 반복되는 switch문                    | Repeated Switches                             | [조건부 로직을 다형성으로 바꾸기](#조건부-로직을-다형성으로-바꾸기)                                                                                                                                                                                                                                                                                                                                                                                                                      |
| 13  | 반복문                               | Loops                                         | [반복문을 파이프라인으로 바꾸기](#반복문을-파이프라인으로-바꾸기)                                                                                                                                                                                                                                                                                                                                                                                                                        |
| 14  | 성의 없는 요소                       | Lazy Element                                  | [함수 인라인하기](#함수-인라인하기), [클래스 인라인하기](#클래스-인라인하기), [계층 합치기](#계층-합치기)                                                                                                                                                                                                                                                                                                                                                                                |
| 15  | 추측성 일반화                        | Speculative Generality                        | [계층 합치기](#계층-합치기), [함수 인라인하기](#함수-인라인하기), [클래스 인라인하기](#클래스-인라인하기), [함수 선언 바꾸기](#함수-선언-바꾸기), [죽은 코드 제거하기](#죽은-코드-제거하기)                                                                                                                                                                                                                                                                                              |
| 16  | 임시 필드                            | Temporary Field                               | [클래스 추출하기](#클래스-추출하기), [함수 옮기기](#함수-옮기기), [특이 케이스 추가하기](#특이-케이스-추가하기)                                                                                                                                                                                                                                                                                                                                                                          |
| 17  | 메시지 체인                          | Messafge Chains                               | [위임 숨기기](#위임-숨기기), [함수 추출하기](#함수-추출하기), [함수 옮기기](#함수-옮기기)                                                                                                                                                                                                                                                                                                                                                                                                |
| 18  | 중개자                               | Middle Man                                    | [중개자 제거하기](#중개자-제거하기), [함수 인라인하기](#함수-인라인하기), [서브클래스를 위임으로 바꾸기](#서브클래스를-위임으로-바꾸기), [슈퍼클래스를 위임으로 바꾸기](#슈퍼클래스를-위임으로-바꾸기)                                                                                                                                                                                                                                                                                   |
| 19  | 내부자 거래                          | Insider Trading                               | [함수 옮기기](#함수-옮기기), [필드 옮기기](#필드-옮기기), [위임 숨기기](#위임-숨기기), [서브클래스를 위임으로 바꾸기](#서브클래스를-위임으로-바꾸기), [슈퍼클래스를 위임으로 바꾸기](#슈퍼클래스를-위임으로-바꾸기)                                                                                                                                                                                                                                                                      |
| 20  | 거대한 클래스                        | Large Class                                   | [클래스 추출하기](#클래스-추출하기), [슈퍼클래스 추출하기](#슈퍼클래스-추출하기), [타입 코드를 서브클래스로 바꾸기](#타입-코드를-서브클래스로-바꾸기)                                                                                                                                                                                                                                                                                                                                    |
| 21  | 서로 다른 인터페이스의 대안 클래스들 | Alternative Classes with Different Interfaces | [함수 선언 바꾸기](#함수-선언-바꾸기), [함수 옮기기](#함수-옮기기), [슈퍼클래스 추출하기](#슈퍼클래스-추출하기)                                                                                                                                                                                                                                                                                                                                                                          |
| 22  | 데이터 클래스                        | Data Class                                    | [레코드 캡슐화하기](#레코드-캡슐화하기), [세터 제거하기](#세터-제거하기), [함수 옮기기](#함수-옮기기), [함수 추출하기](#함수-추출하기), [단계 쪼개기](#단계-쪼개기)                                                                                                                                                                                                                                                                                                                      |
| 23  | 상속 포기                            | Refused Bequest                               | [메서드 내리기](#메서드-내리기), [필드 내리기](#필드-내리기), [서브클래스를 위임으로 바꾸기](#서브클래스를-위임으로-바꾸기), [슈퍼클래스를 위임으로 바꾸기](#슈퍼클래스를-위임으로-바꾸기)                                                                                                                                                                                                                                                                                               |
| 24  | 주석                                 | Comments                                      | [함수 추출하기](#함수-추출하기), [함수 선언 바꾸기](#함수-선언-바꾸기), [어서션 추가하기](#어서션-추가하기)                                                                                                                                                                                                                                                                                                                                                                              |

## 테스트 구축하기

- 모든 테스트를 완전히 자동화하고 그 결과까지 스스로 검사하게 만들자.
- 리팩터링을 제대로 하려면 불가피하게 저지르는 실수를 잡아주는 견고한 test suite가 뒷받침돼야 한다.
- 버그 리포트를 받으면 가장 먼저 그 버그를 드러내는 단위 테스트부터 작성하자.

## 리팩터링 카탈로그

### 기본적인 리팩터링

#### 함수 추출하기

Extract Function

```javascript
function printOwing(invoice) {
  printBanner();
  let outstanding = calculateOutstanding();

  console.log(`고객명: ${invoice.customer}`);
  console.log(`채무액: ${outstanding}`);
}
```

```javascript
function printOwing(invoice) {
  printBanner();
  let outstanding = calculateOutstanding();
  printDetails(outstanding);

  function printDetails(outstanding) {
    console.log(`고객명: ${invoice.customer}`);
    console.log(`채무액: ${outstanding}`);
  }
}
```

#### 함수 인라인하기

Inline Function

```javascript
function getRating(driver) {
  return moreThanFiveLateDeliveries(driver) ? 2 : 1;
}

function moreThanFiveLateDeliveries(driver) {
  return driver.numberOfLateDeliveries > 5;
}
```

```javascript
function getRating(driver) {
  return driver.numberOfLateDeliveries > 5 ? 2 : 1;
}
```

#### 변수 추출하기

Extract Variable

```javascript
return (
  order.quantity * order.itemPrice -
  Math.max(0, order.quantity - 500) * order.itemPrice * 0.05 +
  Math.min(order.quantity * order.itemPrice * 0.1, 100)
);
```

```javascript
const basePrice = order.quantity * order.itemPrice;
const quantityDiscount =
  Math.max(0, order.quantity - 500) * order.itemPrice * 0.05;
const shipping = Math.min(basePrice * 0.1, 100);

return basePrice - quantityDiscount + shipping;
```

#### 변수 인라인하기

Inline Variable

```javascript
let basePrice = anOrder.basePrice;
return basePrice > 1000;
```

```javascript
return anOrder.basePrice > 1000;
```

#### 함수 선언 바꾸기

Change Function Declaration

```javascript
function circum(radius) {...}
```

```javascript
function circumference(radius) {...}
```

#### 변수 캡슐화하기

Encapsulate Variable

```javascript
let defaultOwner = { firstName: "마틴", lastName: "파울러" };
```

```javascript
let defaultOwner = { firstName: "마틴", lastName: "파울러" };
export function defaultOwner() {
  return defaultOwnerData;
}
export function setDefaultOwner(arg) {
  defaultOwnerData = arg;
}
```

#### 변수 이름 바꾸기

Rename Variable

```javascript
let a = height * width;
```

```javascript
let area = height * width;
```

#### 매개변수 객체 만들기

Introduce Parameter Object

```javascript
function amountInvoiced(startDate, endDate) {...}
function amountReceived(startDate, endDate) {...}
function amountOverdue(startDate, endDate) {...}
```

```javascript
function amountInvoiced(aDateRange) {...}
function amountReceived(aDateRange) {...}
function amountOverdue(aDateRange) {...}
```

#### 여러 함수를 클래스로 묶기

Combine Functions into Class

```javascript
function base(aReading) {...}
function taxableCharge(aReading) {...}
function calculateBaseCharge(aReading) {...}
```

```javascript
class Reading {
  base() {...}
  taxableCharge() {...}
  calculateBaseCharge() {...}
}
```

#### 여러 함수를 변환 함수로 묶기

Combine Functions into Transform

```javascript
function base(aReading) {...}
function taxableCharge(aReading) {...}
```

```javascript
function enrichReading(argReading) {
  const aReading = _.cloneDeep(argReading);
  aReading.baseCharge = base(aReading);
  aReading.taxableCharge = taxableCharge(aReading);
  return aReading;
}
```

#### 단계 쪼개기

Split Phase

```javascript
const orderData = orderString.split(/\s+/);
const productPrice = priceList[orderData[0].split("-")[1]];
const orderPrice = parseInt(orderData[1]) * productPrice;
```

```javascript
const orderRecord = parseOrder(order);
const orderPrice = price(orderRecord, priceList);

function parseOrder(aString) {
  const values = aString.split(/\s+/);
  return {
    productID: values[0].split("-")[1],
    quantity: parseInt(values[1]),
  };
}

function price(order, priceList) {
  return order.quantity * priceList[order.productID];
}
```

### 캡슐화

#### 레코드 캡슐화하기

Encapsulate Record

```javascript
organization = { name: "애크미 구스베리", country: "GB" };
```

```javascript
class Organization {
  constructor(data) {
    this._name = data.name;
    this._country = data.country;
  }
  get name() {
    return this._name;
  }
  set name(arg) {
    this._name = arg;
  }
  get country() {
    return this._country;
  }
  set country(arg) {
    this._country = arg;
  }
}
```

#### 컬렉션 캡슐화하기

Encapsulate Collection

```javascript
class Person {
  get courses() {
    return this._courses;
  }
  set courses(aList) {
    this._courses = aList;
  }
}
```

```javascript
class Person {
  get courses()         { return this._courses.slice(); }
  addCourse(aCourse)    {...}
  removeCourse(aCourse) {...}
}
```

#### 기본형을 객체로 바꾸기

Replace Primitive with Object

```javascript
orders.filter((o) => "high" === o.priority || "rush" === o.priority);
```

```javascript
orders.filter((o) => o.priority.higherThan(new Priority("normal")));
```

#### 임시 변수를 질의 함수로 바꾸기

Replace Temp with Query

```javascript
const basePrice = this._quantity * this._itemPrice;
if (basePrice > 1000) return basePrice * 0.95;
else return basePrice * 0.98;
```

```javascript
get basePrice() { this._quantity * this._itemPrice; }
...
if (this.basePrice > 1000)
  return this.basePrice * 0.95;
else
  return this.basePrice * 0.98;
```

#### 클래스 추출하기

Extract Class

```javascript
class Person {
  get officeAreaCode() {
    return this._officeAreaCode;
  }
  get officeNumber() {
    return this._officeNumber;
  }
}
```

```javascript
class Person {
  get officeAreaCode() { return this._telephoneNumber.areaCode; }
  get officeNumber()   { return this._telephoneNumber.number; }
}

class TelephoneNumber() {
  get areaCode()  { return this._areaCode; }
  get number()    { return this._number; }
}
```

#### 클래스 인라인하기

Inline Class

```javascript
class Person {
  get officeAreaCode() { return this._telephoneNumber.areaCode; }
  get officeNumber()   { return this._telephoneNumber.number; }
}

class TelephoneNumber() {
  get areaCode()  { return this._areaCode; }
  get number()    { return this._number; }
}
```

```javascript
class Person {
  get officeAreaCode() {
    return this._officeAreaCode;
  }
  get officeNumber() {
    return this._officeNumber;
  }
}
```

#### 위임 숨기기

Hide Delegate

```javascript
manager = aPerson.department.manager;
```

```javascript
manager = aPerson.manager;
class Person {
  get manager() {
    return this.department.manager;
  }
}
```

#### 중개자 제거하기

Remove Middle Man

```javascript
manager = aPerson.manager;

class Person {
  get manager() {
    return this.department.manager;
  }
}
```

```javascript
manager = aPerson.department.manager;
```

#### 알고리즘 교체하기

Substitute Algorithm

```javascript
function foundPerson(people) {
  for (let i = 0; i < people.length; i++) {
    if (people[i] === "Don") {
      return "Don";
    }
    if (people[i] === "John") {
      return "John";
    }
    if (people[i] === "Kent") {
      return "Kent";
    }
  }
  return "";
}
```

```javascript
function foundPerson(people) {
  const candidates = ["Don", "John", "Kent"];
  return people.find((p) => candidates.includes(p)) || "";
}
```

### 기능 이동

#### 함수 옮기기

Move Function

```javascript
class Account {
  get overdraftCharge() {...}
}
```

```javascript
class AccountType {
  get overdraftCharge() {...}
}
```

#### 필드 옮기기

Move Field

```javascript
class Customer {
  get plan() {
    return this._plan;
  }
  get discountRate() {
    return this._discountRate;
  }
}
```

```javascript
class Customer {
  get plan() {
    return this._plan;
  }
  get discountRate() {
    return this.plan._discountRate;
  }
}
```

#### 문장을 함수로 옮기기

Move Statements into Function

```javascript
result.push("<p>제목: ${person.photo.title}</p>");
result.concat(photoData(person.photo));

function photoData(aPhoto) {
  return [
    "<p>위치: ${aPhoto.location}</p>",
    "<p>날짜: ${aPhoto.date.toDateString()}</p>",
  ];
}
```

```javascript
result.concat(photoData(person.photo));

function photoData(aPhoto) {
  return [
    "<p>제목: ${person.photo.title}</p>",
    "<p>위치: ${aPhoto.location}</p>",
    "<p>날짜: ${aPhoto.date.toDateString()}</p>",
  ];
}
```

#### 문장을 호출한 곳으로 옮기기

Move Statements to Callers

```javascript
emitPhotoData(outStream, person.photo);

function emitPhotoData(outStream, photo) {
  outStream.write("<p>제목: ${photo.title}</p>\n");
  outStream.write("<p>위치: ${photo.location}</p>\n");
}
```

```javascript
emitPhotoData(outStream, person.photo);
outStream.write("<p>위치: ${photo.location}</p>\n");

function emitPhotoData(outStream, photo) {
  outStream.write("<p>제목: ${photo.title}</p>\n");
}
```

#### 인라인 코드를 함수 호출로 바꾸기

Replace Inline Code with Function Call

```javascript
let appliesToMass = false;
for (const s of states) {
  if (s === "MA") appliesToMass = true;
}
```

```javascript
appliesToMass = states.includes("MA");
```

#### 문장 슬라이드하기

Slide Statements

```javascript
const pricingPlan = retrievePricingPlan();
const order = retrieveOrder();
let charge;
const chargePerUnit = pricingPlan.unit;
```

```javascript
const pricingPlan = retrievePricingPlan();
const chargePerUnit = pricingPlan.unit;
const order = retrieveOrder();
let charge;
```

#### 반복문 쪼개기

Split Loop

```javascript
let averageAge = 0;
let totalSalary = 0;
for (const p of people) {
  averageAge += p.age;
  totalSalary += p.salary;
}
averageAge = averageAge / people.length;
```

```javascript
let totalSalary = 0;
for (const p of people) {
  totalSalary += p.salary;
}

let averageAge = 0;
for (const p of people) {
  averageAge += p.age;
}

averageAge = averageAge / people.length;
```

#### 반복문을 파이프라인으로 바꾸기

Replace Loop with Pipeline

```javascript
const names = [];
for (const i of input) {
  if (i.job == "programmer") names.push(i.name);
}
```

```javascript
const names = input.filter((i) => i.job === "programmger").map((i) => i.name);
```

#### 죽은 코드 제거하기

Remove Dead Code

```javascript
if (false) {
  doSomethingThatUsedToMatter();
}
```

```diff
- if (false) {
-   doSomethingThatUsedToMatter();
- }
```

### 데이터 조직화

#### 변수 쪼개기

Split Variable

```javascript
let temp = 2 * (height + width);
console.log(temp);
temp = height * width;
console.log(temp);
```

```javascript
const perimeterr = 2 * (height + width);
console.log(perimeter);
const area = height * width;
console.log(area);
```

#### 필드 이름 바꾸기

Rename Field

```javascript
class Organization {
  get name() {...}
}
```

```javascript
class Organization {
  get title() {...}
}
```

#### 파생 변수를 질의 함수로 바꾸기

Replace Derived Variable with Query

```javascript
get discountedTotal() { return this._discountedTotal; }
set discount(aNumber) {
  const old = this._discount;
  this._discount = aNumber;
  this._discountedTotal += old - aNumber;
}
```

```javascript
get discountedTotal() { return this._baseTotal - this._discount; }
set discount(aNumber) { this._discount = aNumber; }
```

#### 참조를 값으로 바꾸기

Change Reference to Value

```javascript
class Product {
  applyDiscount(arg) {
    this._price.amount -= arg;
  }
}
```

```javascript
class Product {
  applyDiscount(arg) {
    this._price = new Money(this._price.amount - arg, this._price.currency);
  }
}
```

#### 값을 참조로 바꾸기

Change Value to Reference

```javascript
let customer = new Customer(customerData);
```

```javascript
let customer = customerRepository.get(customerData.id);
```

#### 매직 리터럴 바꾸기

Replace Magic Literal

```javascript
function potentialEnergy(mass, height) {
  return mass * 9.81 * height;
}
```

```javascript
const STANDARD_GRAVITY = 9.81;
function potentialEnergy(mass, height) {
  return mass * STANDARD_GRAVITY * height;
}
```

### 조건부 로직 간소화

#### 조건문 분해하기

Decompose Conditional

```javascript
if (!aDate.isBefore(plan.summerStart) && !aDate.isAfter(plan.summerEnd))
  charge = quantity * plan.summerRate;
else charge = quantity * plan.regularRate + plan.regularServiceCharge;
```

```javascript
if (summer()) {
  charge = summerCharge();
else
  charge = regularCharge();
}
```

#### 조건식 통합하기

Consolidate Conditional Expression

```javascript
if (anEmployee.seniority < 2) return 0;
if (anEmployee.monthsDisabled > 12) return 0;
if (anEmployee.isPartTime) return 0;
```

```javascript
if (isNotEligibleForDisability()) return 0;

function isNotEligibleForDisability() {
  return (
    anEmployee.seniority < 2 ||
    anEmployee.monthsDisabled > 12 ||
    anEmployee.isPartTime
  );
}
```

#### 중첩 조건문을 보호 구문으로 바꾸기

Replace Nested Conditional with Guard Clauses

```javascript
function getPayAmount() {
  let result;
  if (isDead) result = deadAmount();
  else {
    if (isSeparated) result = separatedAmount();
    else {
      if (isRetired) result = retiredAmount();
      else result = normalPayAmount();
    }
  }
  return result;
}
```

```javascript
function getPayAmount() {
  if (isDead) return deadAmount();
  if (isSeparated) return separatedAmount();
  if (isRetired) return retiredAmount();
  return normalPayAmount();
}
```

#### 조건부 로직을 다형성으로 바꾸기

Replace Conditional with Polymorphism

```javascript
switch (bird.type) {
  case "유럽 제비":
    return "보통이다";
  case "아프리카 제비":
    return bird.numberOfCoconuts > 2 ? "지쳤다" : "보통이다";
  case "노르웨이 파랑 앵무":
    return bird.voltage > 100 ? "그을렸다" : "예쁘다";
  default:
    return "알 수 없다";
}
```

```javascript
class EuropeanSwallow {
  get plumage() {
    return "보통이다";
  }
}

class AfricanSwallow {
  get plumage() {
    return this.numberOfCoconuts > 2 ? "지쳤다" : "보통이다";
  }
}

class NorwegianBlueParrot {
  get plumage() {
    return this.voltage > 100 ? "그을렸다" : "예쁘다";
  }
}
```

#### 특이 케이스 추가하기

Introduce Special Case

```javascript
if (aCustomer === "미확인 고객") customerName = "거주자";
```

```javascript
class UnknownCustomer {
  get name() {
    return "거주자";
  }
}
```

#### [어서션 추가하기](#어서션-추가하기)

Introduce Assertion

```javascript
if (this.discountRate) base = base - this.discountRate * base;
```

```javascript
assert(this.discountRate >= 0);
if (this.discountRate) base = base - this.discountRate * base;
```

#### 제어 플래그를 탈출문으로 바꾸기

Replace Control Flag with Break

```javascript
for (const p of people) {
  if (!found) {
    if (p === "조커") {
      sendAlert();
      found = true;
    }
    ...
  }
  ...
}
```

```javascript
for (const p of people) {
  if (p === "조커") {
    sendAlert();
    break;
  }
  ...
}
```

### API 리팩터링

#### 질의 함수와 변경 함수 분리하기

Separate Query from Modifier

```javascript
function getTotalOutstandingAndSendBill() {
  const result = customer.invoices.reduce(
    (total, each) => each.amount + total,
    0
  );
  sendBill();
  return result;
}
```

```javascript
function totalOutstanding() {
  return customer.invoices.reduce((total, each) => each.amount + total, 0);
}

function sendBill() {
  emailGateway.send(formatBill(customer));
}
```

#### 함수 매개변수화하기

Parameterize Function

```javascript
function tenPercentRaise(aPerson) {
  aPerson.salary = aPerson.salary.multiply(1.1);
}

function fivePercentRaise(aPerson) {
  aPerson.salary = aPerson.salary.multiply(1.05);
}
```

```javascript
function raise(aPerson, factor) {
  aPerson.salary = aPerson.salary.multiply(1 + factor);
}
```

#### 플래그 인수 제거하기

Remove Flag Argument

```javascript
function setDimension(name, value) {
  if (name === "height") {
    this._height = value;
    return;
  }
  if (name === "width") {
    this._width = value;
    return;
  }
}
```

```javascript
function setHeight(value) {
  this._height = value;
}
function setWidth(value) {
  this._width = value;
}
```

#### 객체 통째로 넘기기

Preserve Whole Object

```javascript
const low = aRoom.daysTempRange.low;
const high = aRoom.daysTempRange.high;
if (aPlan.withinRange(low, high)) {...}
```

```javascript
if (aPlan.withinRange(aRoom.daysTempRange)) {...}
```

#### 매개변수를 질의 함수로 바꾸기

Replace Parameter with Query

```javascript
availableVacation(anEmployee, anEmployee.grade);

function availableVacation(anEmployee, grade) {
  // 연휴 계산...
}
```

```javascript
availableVacation(anEmployee);

function availableVacation(anEmployee) {
  const grade = anEmployee.grade;
  // 연휴 계산...
}
```

#### 질의 함수를 매개변수로 바꾸기

Replace Query with Parameter

```javascript
targetTemperature(aPlan);

function targetTemperature(aPlan) {
  currentTemperature = thermostat.currentTemperature;
  ...
}
```

```javascript
targetTemperature(aPlan, thermostat.currentTemperature);

function targetTemperature(aPlan, currentTemperature) {
  ...
}
```

#### 세터 제거하기

Remove Setting Method

```javascript
class Person {
  get name() {...}
  set name(aString) {...}
}
```

```javascript
class Person {
  get name() {...}
}
```

#### 생성자를 팩터리 함수로 바꾸기

Replace Constructor with Factory Function

```javascript
leadEngineer = new Employee(document.leadEngineer, "E");
```

```javascript
leadEngineer = createEngineer(document.leadEngineer);
```

#### 함수를 명령으로 바꾸기

Replace Function with Command

```javascript
function score(candidate, medicalExam, scoringGuide) {
  let result = 0;
  let healthLevel = 0;
  ...
}
```

```javascript
class Scorer {
  constructor(candidate, medicalExam, scoringGuide) {
    this._candidate = candidate;
    this._medicalExam = medicalExam;
    this._scoringGuide = scoringGuide;
  }

  execute() {
    this._result = 0;
    this._healthLevel = 0;
    ...
  }
}
```

#### 명령을 함수로 바꾸기

Replace Command with Function

```javascript
class ChargeCalculator {
  constructor(customer, usage) {
    this._customer = customer;
    this._usage = usage;
  }
  execute() {
    return this._customer.rate * this._usage;
  }
}
```

```javascript
function charge(customer, usage) {
  return customer.rate * usage;
}
```

#### 수정된 값 반환하기

Return Modified Value

```javascript
let totalAscent = 0;
calculateAscent();

function calculateAscent() {
  for (let i = 1; i < points.length; i++) {
    const verticalChange = points[i].elevation - points[i - 1].elevation;
    totalAscent += verticalChange > 0 ? verticalChange : 0;
  }
}
```

```javascript
const totalAscent = calculateAscent();

function calculateAscent() {
  let result = 0;
  for (let i = 1; i < points.length; i++) {
    const verticalChange = points[i].elevation - points[i - 1].elevation;
    result += verticalChange > 0 ? verticalChange : 0;
  }
  return result;
}
```

#### 오류 코드를 예외로 바꾸기

Replace Error Code with Exception

```javascript
if (data) return new ShippingRules(data);
else return -23;
```

```javascript
if (data) return new ShippingRules(data);
else throw new OrderProcessingError(-23);
```

#### 예외를 사전확인으로 바꾸기

Replace Exception with Precheck

```javascript
double getValueForPeriod(int periodNumber) {
  try {
    return values[periodNumber];
  } catch (ArrayIndexOutOfBoundsException e) {
    return 0;
  }
}
```

```javascript
double getValueForPeriod(int periodNumber) {
  return (periodNumber >= values.length) ? 0 : values[periodNumber];
}
```

### 상속 다루기

#### 메서드 올리기

Pull Up Method

```javascript
class Employee {...}

class Salesperson extends Employee {
  get name() {...}
}

class Engineer extends Employee {
  get name() {...}
}
```

```javascript
class Employee {
  get name() {...}
}

class Salesperson extends Employee {...}
class Engineer extends Employee {...}
```

#### 필드 올리기

Pull Up Field

```java
// Java
class Employee {...}

class Salesperson extends Employee {
  private String name;
}

class Engineer extends Employee {
  private String name;
}
```

```java
class Employee {
  protected String name;
}

class Salesperson extends Employee {...}
class Engineer extends Employee {...}
```

#### 생성자 본문 올리기

Pull Up Constructor Body

```javascript
class Party {...}

class Employee extends Party {
  constructor(name, id, monthlyCost) {
    super();
    this._id = id;
    this._name = name;
    this._monthlyCost = monthlyCost;
  }
}
```

```javascript
class Party {
  constructor(name) {
    this._name = name;
  }
}

class Employee extends Party {
  constructor(name, id, monthlyCost) {
    super(name);
    this._id = id;
    this._monthlyCost = monthlyCost;
  }
}
```

#### 메서드 내리기

Push Down Method

```javascript
class Employee {
  get quota {...}
}

class Engineer extends Employee {...}
class Salesperson extends Employee {...}
```

```javascript
class Employee {...}

class Engineer extends Employee {...}
class Salesperson extends Employee {
  get quota {...}
}
```

#### 필드 내리기

Push Down Field

```java
// Java
class Employee {
  private String quota;
}

class Engineer extends Employee {...}
class Salesperson extends Employee {...}
```

```java
class Employee {...}

class Engineer extends Employee {...}
class Salesperson extends Employee {
  protected String quota;
}
```

#### 타입 코드를 서브클래스로 바꾸기

Replace Type Code with Subclasses

```javascript
function createEmployee(name, type) {
  return new Employee(name, type);
}
```

```javascript
function createEmployee(name, type) {
  switch (type) {
    case "engineer":
      return new Engineer(name);
    case "salesperson":
      return new Salesperson(name);
    case "manager":
      return new Manager(name);
  }
}
```

#### 서브클래스 제거하기

Remove Subclass

```javascript
class Person {
  get genderCode() {
    return "X";
  }
}

class Male extends Person {
  get genderCode() {
    return "M";
  }
}

class Female extends Person {
  get genderCode() {
    return "F";
  }
}
```

```javascript
class Person {
  get genderCode() {
    return this._genderCode;
  }
}
```

#### 슈퍼클래스 추출하기

Extract Superclass

```javascript
class Department {
  get totalAnnualCost() {...}
  get name() {...}
  get headCount() {...}
}

class Employee {
  get annualCost() {...}
  get name() {...}
  get id() {...}
}
```

```javascript
class Party {
  get name() {...}
  get annualCost() {...}
}

class Department extends Party {
  get annualCost() {...}
  get headCount() {...}
}

class Employee extends Party {
  get annualCost() {...}
  get id() {...}
}
```

#### 계층 합치기

Collapse Hierarchy

```javascript
class Employee {...}
class Salesperson extends Employee {...}
```

```javascript
class Employee {...}
```

#### 서브클래스를 위임으로 바꾸기

Replace Subclass with Delegate

```javascript
class Order {
  get daysToShip() {
    return this._warehouse.daysToShip;
  }
}

class PriorityOrder extends Order {
  get daysToShip() {
    return this._priorityPlan.daysToShip;
  }
}
```

```javascript
class Order {
  get daysToShip() {
    return this._priorityDelegate
      ? this._priorityDelegate.daysToShip
      : this._warehouse.daysToShip;
  }
}

class PriorityOrderDelegate {
  get daysToShip() {
    return this._priorityPlan.daysToShip;
  }
}
```

#### 슈퍼클래스를 위임으로 바꾸기

Replace Superclass with Delegate

```javascript
class List {...}
class Stack extends List {...}
```

```javascript
class Stack {
  constructor() {
    this._storage = new List();
  }
}
class List {...}
```
