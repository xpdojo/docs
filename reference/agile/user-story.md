# 사용자 스토리

> 사용자 스토리: 고객 중심의 요구사항 기법 - 마이크 콘

- [사용자 스토리](#사용자-스토리)
  - [1부. 시작하기](#1부-시작하기)
    - [🎯개요](#개요)
    - [좋은 스토리의 6가지 특성 (INVEST)](#좋은-스토리의-6가지-특성-invest)
      - [(Independent) 독립적이다](#independent-독립적이다)
      - [(Negotiable) 협상 가능하다](#negotiable-협상-가능하다)
      - [(Valuable) 사용자와 고객 혹은 구매자에게 가치 있다](#valuable-사용자와-고객-혹은-구매자에게-가치-있다)
      - [(Estimatable) 추정 가능하다](#estimatable-추정-가능하다)
      - [(Small) 작다](#small-작다)
      - [(Testable) 테스트 가능하다](#testable-테스트-가능하다)
    - [사용자 역할 모델링](#사용자-역할-모델링)
      - [사용자 역할 목록을 만들기 위한 절차](#사용자-역할-목록을-만들기-위한-절차)
      - [도움이 되는 기법 2가지](#도움이-되는-기법-2가지)
    - [스토리 수집하기](#스토리-수집하기)
      - [스토리 수집 기법](#스토리-수집-기법)
    - [좋은 스토리를 위한 지침](#좋은-스토리를-위한-지침)
      - [목적 스토리로 시작하라](#목적-스토리로-시작하라)
      - [케이크 자르듯 나누어라](#케이크-자르듯-나누어라)
      - [닫힌 스토리를 작성하라](#닫힌-스토리를-작성하라)
      - [제약사항 기록하기](#제약사항-기록하기)
      - [스토리의 크기는 시간축에 맞추어라](#스토리의-크기는-시간축에-맞추어라)
      - [되도록 사용자 인터페이스를 배제하라](#되도록-사용자-인터페이스를-배제하라)
      - [스토리에 사용자 역할을 포함하라](#스토리에-사용자-역할을-포함하라)
      - [한 명의 사용자를 대상으로 작성하라](#한-명의-사용자를-대상으로-작성하라)
      - [능동태로 작성하라](#능동태로-작성하라)
      - [고객이 작성하라](#고객이-작성하라)
      - [스토리 카드에 번호를 부여하지 말라](#스토리-카드에-번호를-부여하지-말라)
      - [목적을 잊지 말라](#목적을-잊지-말라)
  - [2부. 추정과 계획](#2부-추정과-계획)
    - [스토리 점수](#스토리-점수)
    - [추정하기](#추정하기)
      - [델파이 법(Wideband Delphi)](#델파이-법wideband-delphi)
      - [삼각측량](#삼각측량)
      - [스토리가 크면 정확성이 떨어진다](#스토리가-크면-정확성이-떨어진다)
  - [3부. 자주 논의하는 것](#3부-자주-논의하는-것)
    - [스토리가 아닌 것](#스토리가-아닌-것)
      - [User Story는 IEEE 830이 아니다](#user-story는-ieee-830이-아니다)
      - [User Story는 Use Case가 아니다](#user-story는-use-case가-아니다)
      - [User Story는 Scenario가 아니다](#user-story는-scenario가-아니다)
    - [왜 사용자 스토리인가?](#왜-사용자-스토리인가)
    - [스토리 냄새 카탈로그](#스토리-냄새-카탈로그)
    - [스크럼에서 사용자 스토리 사용하기](#스크럼에서-사용자-스토리-사용하기)
      - [XP와 마찬가지로 스크럼은 반복적이고 점진적인 프로세스다.](#xp와-마찬가지로-스크럼은-반복적이고-점진적인-프로세스다)
      - [스크럼의 기본](#스크럼의-기본)
      - [스크럼에 스토리 추가하기](#스크럼에-스토리-추가하기)

## 1부. 시작하기

### 🎯개요

> 바쁘면 이 부분만 읽는다.\
시간이 좀더 남는다면 책에서 '4부 예제'를 본다.

- 사용자 스토리는 소프트웨어의 사용자나 구매자에게 가치를 줄 수 있는 기능을 서술한 것이다.
- 사용자 스토리는 다음 세 측면으로 구성된다.
  - 서술(written description): 스토리는 서술 형태로 기록되며, 계획하거나 기억하기 위한 단서로 사용된다.
  - 대화(conversation): 스토리는 대화를 통해 세부사항을 구체화한다.
  - 테스트(test): 스토리는 테스트를 통해 세부사항을 문서화하고 전달하며, 스토리의 완료 여부를 판단한다.
- 사용자 스토리의 서술은 관행적으로 종이 인덱스 카드에 손으로 작성하기 때문에, 론 제프리즈(Ron Jeffries)는 위 세 개의 측면에 카드(Card), 대화(Conversation), 확인(Confirmation)이라는 근사한 두운을 가진 이름을 붙였다.
  - '카드'는 스토리의 본문(text)을 담고 있지만, 세부사항은 '대화'를 통해 결정되며 구현을 '확인'하기 위한 테스트를 포함한다.
- 사용자 스토리는 사용자에게 가치를 평가 받을 수 있도록 기능을 표현해야 한다.
- 스토리가 너무 큰 경우에 가끔 에픽(epic)이라고 말하기도 한다. (Jira에서는 '큰 틀'이라고 번역된다)
  - 에픽은 더 작은 스토리로 나눌 수 있다.
  - 예를 들어 '사용자는 채용 정보를 검색할 수 있다'는 에픽은 다음과 같이 3개로 나눌 수 있다.
    > 사용자는 위치, 급여 수준, 직업명 등의 속성값으로 채용 정보를 검색할 수 있다.\
    사용자는 검색 조건과 일치하는 채용 정보를 볼 수 있다.\
    사용자는 채용 정보를 게시한 기업에 대한 세부 정보를 볼 수 있다.
- 고객팀(customer team)에는 소프트웨어가 사용자의 요구를 만족하는지 보증해 줄 사람들이 포함된다.
  - 여기에는 테스터, 제품 관리자(PM, Product Manager), 실제 사용자, 상호작용 설계자(Interaction Designer) 등이 포함될 것이다.
- 개발자 대신 고객팀이 사용자 스토리를 작성하는 데는 두 가지 주된 이유가 있다.
  1. 각 스토리는 기술적 전문 용어가 아닌 비즈니스 언어로 작성해야 한다. 그래야 고객팀에서 스토리를 어느 이터레이션(Iteration)이나 릴리즈(Release)에 포함시킬지 우선순위를 결정할 수 있다.
  2. 제품의 주된 기획 주체로서 고객팀은 제품의 동작을 가장 잘 설명할 수 있다.
- 개발팀과 고객팀이 합의한 내용은 스토리가 정확하게 개발되었는지를 증명하는 테스트 형태로 문서화된다.
  > 사용자는 검색 조건과 일치하는 채용 정보를 볼 수 있다.\
  \
  주) 마르코는 설명, 급여, 위치 정보를 보여 주어야 한다고 함.
- 테스트 서술은 간결해야 한다. 테스트는 어느 때라도 추가하거나 제거할 수 있다.
- 릴리즈는 하나 이상의 이터레이션으로 이루어진다.
- 이터레이션 계획(iteration planning)은 이번 이터레이션에 포함할 스토리를 선택하는 일을 말한다.
- 릴리즈 계획(release planning)은 프로젝트 일정과 구현할 기능 집합의 균형을 결정하는 일이다.
  - 릴리즈 계획은 고객 팀이 스토리에 우선순위를 매기는 것으로 시작한다. 우선순위를 부여할 때 다음 사항들을 고려해야 한다.
    - 사용자나 고객 다수가 원하는 기능인가?
    - 다수는 아니지만 중요한 사용자나 고객이 바라는 기능인가?
    - 이 스토리가 다른 스토리들과 응집성(cohesiveness)이 있는가? 예를 들어 도면 조회 시스템에서 'zoom out' 기능의 스토리는 그 자체로 우선순위가 높지 않지만 'zoom in' 기능의 스토리는 우선순위가 높을 경우, 둘의 상호 보완적 관계 때문에 두 스토리 모두 우선순위를 높게 다룰 수 있다.
  - 스토리 개발에 드는 비용 역시 우선순위를 부여할 때 고려할 요인이다.
    - 스토리 개발 비용은 개발자들이 스토리에 부여하는 추정치다.
    - 각 스토리에 '스토리 점수(story point)'를 추정치로 할당한다.
    - 한 이터레이션에서 스토리 점수 4점으로 추정한 것은, 그 스토리를 개발하는 데는 2점으로 추정한 다른 스토리보다 두 배 정도 시간이 걸릴 것을 예상한다는 의미다.
- 인수 테스트(6장)는 스토리를 개발한 뒤 그것이 고객이 기대하는 대로 정확히 동작하는지를 입증하는 과정이다.
  - '사용자는 장바구니에 담긴 아이템을 구매할 때 신용 카드로 결제할 수 있다'는 스토리를 보자.
  - 고객은 스토리 카드 뒷면에 다음과 같은 간단한 테스트들을 작성한다.
    > 비자, 마스터카드, 아메리칸익스프레스카드 테스트(통과).\
    다이너스클럽카드 테스트(실패).\
    비자직불카드 테스트(통과).\
    정상/비정상 카드 ID 테스트. 분실 카드 ID 테스트.\
    유효 기간 만료된 카드 테스트.\
    다양한 구매액 테스트(카드 한도 초과액 포함).

### 좋은 스토리의 6가지 특성 (INVEST)

#### (Independent) 독립적이다

- 가능하면 스토리 간에 의존성을 배제하도록 신경 써야 한다.
- 스토리 사이에 의존성이 있으면 우선순위 결정과 계획 수립에 문제를 야기한다.
  > 기업은 채용 공고를 게시할 때 비자카드로 결제할 수 있다.\
  기업은 채용 공고를 게시할 때 마스터카드로 결제할 수 있다.\
  기업은 채용 공고를 게시할 때 아메리칸익스프레스카드로 결제할 수 있다.
- 이런 형태의 의존성이 나타날 때에는 두 가지 방법을 시도해 볼 수 있다.
  - 의존성이 있는 스토리들을 합쳐 좀더 큰 하나의 독립적인 스토리로 만든다.
    > 기업은 채용 공고를 게시할 때 신용카드로 결제할 수 있다.
  - 스토리들을 다른 방식으로 분리한다.
      > 고객은 한 종류의 신용카드로 결제할 수 있다.\
      고객이 결제할 수 있는 신용카드는 두 종류가 더 있다.

#### (Negotiable) 협상 가능하다

- 스토리는 계약서나 요구사항 명세서처럼 꼭 구현해야 한다고 기록된 것이 아니다.
- 스토리는 기능에 대한 짧은 설명일 뿐, 세부사항은 고객과 개발 팀이 **대화**를 통해 협상해야 한다.
  - 스토리 카드는 대화를 이끌기 위한 단서지, 그 자체로 완성된 상세한 요구사항이 아니기 때문에, 필요한 모든 세부사항까지 포함할 필요가 없다.

#### (Valuable) 사용자와 고객 혹은 구매자에게 가치 있다

- 소프트웨어를 직접 사용하는 '사용자(user)'와 소프트웨어를 구매하는 '구매자(purchaser)'가 다를 수 있다.
- 스토리는 사용자 혹은 구매자에게 가치가 평가되어야 한다.
- 작성하지 말아야 하는 스토리는 개발자에게만 가치 있는 스토리다.
  > 모든 데이터베이스 연결은 커넥션풀을 통해 이루어져야 한다.\
  모든 에러 처리 및 로그 생성은 공통 클래스들을 통해 이루어져야 한다.
- 각 스토리가 고객이나 사용자에게 가치 있도록 하는 가장 좋은 방법은 고객이 직접 스토리를 작성하게 하는 것이다.

#### (Estimatable) 추정 가능하다

- 개발자들은 각 스토리의 크기 혹은 작업 소요 시간을 추정(적어도 추측)할 수 있어야 한다.
- 추정이 쉽지 않은 경우는 보통 다음의 세 가지 이유다.
    1. 해당 분야의 지식(도메인 지식)이 부족하다.
       - 해당 스토리를 작성한 고객과 직접 의논해야 한다.
    2. 기술적인 지식이 부족하다.
       - 한두 명의 개발자를 '스파이크(spike)'를 수행하도록 한다.
       - spike? 개발 예상 기간 추정이 어렵거나 리스크가 높은 스토리를 대상으로 완전하지 않지만 처음부터 끝까지 문제 영역을 살펴보는 작업.
    3. 스토리가 너무 크다.

#### (Small) 작다

- 스토리가 너무 크거나 너무 작으면 계획 단계에서 사용할 수 없기 때문에 스토리의 크기는 아주 중요하다.
- 스토리 나누기
  - 에픽은 다음 두 가지 중 하나다.
    - 복합적인 스토리: 작은 스토리를 여러 개 포함하는 에픽이다. 복합적인 스토리를 나누는 방법은 많다.
    - 복잡한 스토리: 크기가 크면서도 작은 스토리들로 나누기가 쉽지 않다.
- 스토리 합치기
  - 너무 작은 스토리란 것은, 그것을 작성하고 작업량을 추정하는 것이 내용을 변경하는 것보다 더 오래 걸릴 것 같은 스토리다.
  - 주로 버그 리포팅이나 UI 변경에 대한 스토리들이 여기에 해당한다.
  - 이런 작은 스토리들을 취급해야 한다면, 이것들을 더 큰 스토리로 합쳐서 반나절에서 며칠 정도의 작업량이 되도록 만든다.

#### (Testable) 테스트 가능하다

- 테스트를 성공적으로 통과해야 그 스토리가 성공적으로 개발되었다고 말할 수 있다.
- 가능하면 테스트를 자동화할 수 있도록 작성해야 한다.

### 사용자 역할 모델링

사용자들은 제각기 다른 배경과 목적으로 소프트웨어를 사용하겠지만,
비슷한 유형의 사용자들을 모아 '사용자 역할(user role)'로 부를 수 있을 것이다.
사용자 역할은 특정 사용자 집단이 시스템과 어떤 상호작용을 하는지 규정하는 속성의 집합이다.

#### 사용자 역할 목록을 만들기 위한 절차

- 사용자 역할 목록 초안을 위한 브레인스토밍
- 목록 초안 조직화
- 역할 통합하기
- 역할 다듬기

#### 도움이 되는 기법 2가지

- 등장인물(Persona)
  - 등장인물은 사용자 역할을 대표할 만한 가상 인물이다.
  - 등장인물을 만들기로 결정했다면, 등장인물이 실제 대상 고객을 왜곡하지 않고 나타내도록
  시장 및 인구통계에 근거해 충분한 조사가 선행되어야 함을 명심한다.
- 극단적 인물
  - 새로운 시스템을 설계할 때에는 극다적 인물을 사용하라. 극단적인 인물을 고려하면 여러분이 지나칠 수도 있는 스토리를 발견하게 된다.
  - 극단적 인물을 고려하면 새로운 사용자 스토리를 찾을 수 있지만, 이것들이 제품에 포함되어야 하는지를 판단하기란 쉽지 않다.

### 스토리 수집하기

- 애자일 프로세스는 요구사항을 처음부터 다 얻어낼 수 없다는 것을 인정한다.
- 릴리즈를 시작할 때에는 쉽게 찾아낼 수 있는 사용자 스토리를 작성하는 것으로 시작하는 것이 좋다.
- 한 가지 방법에 지나치게 의존하기보다는 여러 방법들을 같이 적용함으로써 가장 좋은 결과를 얻을 수 있다.

#### 스토리 수집 기법

- 사용자 인터뷰
  - 가장 유용한 답변을 얻기 위해서는 개방형 질문, 문맥 무관 질문을 해야 한다.
  - 개방형 질문 (open-ended, 자유 응답 질문): 응답자가 자유롭게 응답하도록 하는 형태
  - 폐쇄형 질문: 질문자가 가능한 응답 목록을 미리 지정해 놓은 형태(Y/N, 객관식 등)
  - 문맥 무관 질문 (context-free): 암시적으로 특정 답변을 유도하지 않아야 하며, 질문자의 선호도가 나타나지 않아야 한다.
    - "얼마나 빨리 검색되어야 하나요?"보다는 "애플리케이션에서 성능이 더 중요한 부분이 있나요?"
    - "제목으로 채용 정보를 검색하시나요?"보다는 "채용 정보를 어떻게 검색하고 싶은지 말씀해주세요."
- 설문
  - 이미 가지고 있는 스토리에 대한 정보를 수집하는 효과적인 기법이다. 큰 사용자 집단을 대상으로 한다면, 설문은 스토리에 우선순위를 매기기 위한 정보를 수집하는 아주 훌륭한 방법이다.
- 관찰
- 스토리 작성 워크숍

### 좋은 스토리를 위한 지침

#### 목적 스토리로 시작하라

한번에 하나씩 사용자 역할을 선택하여 그 사용자가 새 시스템을 사용하는 주 목적을 식별하는 것이 가장 효과적이었다.

#### 케이크 자르듯 나누어라

큰 스토리를 만났을 때에는 그것을 작은 스토리 조각으로 나눌 수 있다는 사실을 명심하자.

#### 닫힌 스토리를 작성하라

닫힌 스토리는 의미 있는 목적을 달성하는 형태로 작성되어 사용자로 하여금 무언가를 해냈다고 느끼게 하는 스토리를 말한다.

- 스토리를 수집할 때 개방향 질문을 통해 스토리를 찾는 것과 비교해 볼 수 있다. 새 스토리를 찾으려면 고객이나 사용자에게 개방형, 즉 열린 질문을 하고, 스토리를 작성할 때에는 닫힌 형태로 작성하여야 한다.

#### 제약사항 기록하기

어떤 스토리가 직접 구현될 내용은 아니지만 시스템이 꼭 지켜야 하는 내용인 경우 '제약사항'이라는 표식(제약사항 스토리 카드)을 달아둔다.

#### 스토리의 크기는 시간축에 맞추어라

먼 나중에 일어날 일이 아닌 가까운 미래에 일어날 중요한 일에 더 집중한다.

#### 되도록 사용자 인터페이스를 배제하라

사용자 인터페이스에 관한 세부사항은 소프트웨어가 좀더 구체적인 모양을 갖추고 스토리가 기존 기능을 수정하거나 확장하는 것을 의미하게 될 때다.

스토리가 새로운 기능을 의미할 때에는 구현 세부사항을 배제한다.

#### 스토리에 사용자 역할을 포함하라

사용자 역할을 식별해 냈다면 '사용자는 이력서를 작성할 수 있다'고 하는 대신 '구직자는 이력서를 작성할 수 있다'고 작성한다.

#### 한 명의 사용자를 대상으로 작성하라

'구직자들(Job Seekers)은 사이트에서 이력서를 삭제할 수 있다'는 스토리를 보자. 이는 어떤 구직자가 자신의 이력서뿐만 아니라 다른 사람들의 이력서도 지울 수 있는 것으로 해석될 수 있다.

#### 능동태로 작성하라

'이력서는 구직자에 의해 게시될 수 있다'고 하기보다 '구직자는 이력서를 게시할 수 있다'고 작성하는 것이 더 이해하기 쉽다.

#### 고객이 작성하라

고객에게는 이터레이션을 시작할 때 스토리의 우선순위를 매겨야 하는 책임이 있기 때문에 고객은 반드시 각 스토리를 이해하고 있어야 한다. 가장 잘 이해하는 방법은 직접 작성하는 것이다.

#### 스토리 카드에 번호를 부여하지 말라

보통 쉽게 추적하기 위해 카드에 일련번호를 부여한다. 하지만 무의미한 업무 부담만 늘리고 구체적인 기능을 논의하는 데 불필요한 추상성을 개입시키는 문제가 있다.

- 스토리 카드에 번호를 부여해야 한다는 의무감 같은 것이 느껴진다면, 그 대신 카드에 짧은 제목을 붙이고 다음부터 그 스토리를 지칭할 때 사용한다.

#### 목적을 잊지 말라

스토리 카드의 주 목적은 구현할 기능을 논의하기 위한 단서 역할이라는 점을 잊지 말아야 한다. 단서는 간결해야 한다. 카드에는 나중에 대화를 재개하기 위해 기억하면 될 정도의 세부사항만을 써넣도록 하며, 너무 많은 세부사항을 써넣어 카드가 대화를 대신하지 않게 한다.

## 2부. 추정과 계획

### 스토리 점수

개발자들이 스토리에 부여하는 이상적인 경과 시간 추정치다. 스토리 점수는 팀마다 자신들에게 맞는 정의를 채택하여 사용할 수 있다는 장점이 있다.

### 추정하기

#### 델파이 법(Wideband Delphi)

#### 삼각측량

#### 스토리가 크면 정확성이 떨어진다

스토리 점수로 추정할 때의 문제점은 수치 상의 차이를 설명하기 어렵다는 것이다. 팀은 추정치를 아래와 같이 미리 정의된 수치로만 한정할 수 있을 것이다.

> 1/2, 1, 2, 3, 5, 8, 13, 20, 40, 80

추정치가 크다는 것은 그만큼 스토리를 잘 모르기 때문이라는 사실을 반영하여 값이 커질수록 간격도 커진다는 것을 확인할 수 있다. 에픽을 추정할 때는 40점인지 80점인지만 결정하면 된다. 79점인지 80점인지 고민할 필요는 없다.

## 3부. 자주 논의하는 것

### 스토리가 아닌 것

User Story는 IEEE 830 명세서나 Use Case와는 달리 분석 작업의 결과물이 아니다.

#### User Story는 IEEE 830이 아니다

IEEE 컴퓨터 학회에서는 소프트웨어 요구사항 명세서 작성에 관한 가이드라인을 출판하였다(IEEE 1999). 'IEEE 표준 830'이라 알려진 이 문서의 가장 두드러진 특징은 기능 요구사항(functional requirements)을 작성할 때 '시스템은 ...해야 한다(The system shall...)' 형태의 문장을 사용한다는 점이다.

> 시스템은 기업이 채용 공고를 게시할 때 신용카드로 결제할 수 있어야 한다.\
시스템은 비자, 마스타, 아메리칸익스프레스카드 등을 처리할 수 있어야 한다.\
시스템은 웹 사이트에 채용 공고가 게시되기 전에 결재를 먼저하도록 해야 한다.\
시스템은 사용자에게 고유의 확인 번호를 부여해야 한다.

시스템의 요구사항을 이러한 수준으로 자세하게 문서화하다 보면 장황해지기 쉽고 실수하기도 쉬우며 시간도 많이 든다. 게다가, 솔직히 말해서 이런 문서는 읽기에 지루하다.

IEEE 830 스타일의 요구사항 기술방식은 사용자의 목적보다는 요구사항 목록 자체에 주의를 기울이게 하기 때문에 프로젝트가 방향을 잃는 경우가 많았다.

#### User Story는 Use Case가 아니다

- 범위(scope): 둘 다 비즈니스 가치를 기술하는데 적합한 크기지만 User Story는 제약 조건(개발하는 데 열흘이 넘지 않도록)을 두어, 일정 계획에 사용하기 편리하도록 작은 범위를 다룬다.
- 완전성: 스토리 카드에 인수 테스트를 더해야 Use Case와 동일하다.
- 수명(longevity): Use Case는 개발 기간이나 유지보수 기간에 계속 사용된다. 반면 User Story는 그것을 개발한 이터레이션 후에는 유지할 필요가 없다.
- 구현 세부사항: Use Case는 사용자 인터페이스에 관한 세부사항을 포함하는 경우가 많다. (그렇게 하지 말 것을 권장함에도 불구하고)
- 목적: Use Case는 개발자와 고객이 그것을 논의하고 거기에 동의하기 위해 작성된다. User Story는 릴리즈를 계획하거나 대화를 통해 상세한 요구사항을 찾기 위한 매개체로 사용된다.

#### User Story는 Scenario가 아니다

시나리오는 사용자 스토리보다 훨씬 상세한 내용을 담고 있으며 보통 여러 사용자 스토리를 포함한다.

### 왜 사용자 스토리인가?

- 사용자 스토리는 문서보다 구두 의사소통을 강조한다.
- 사용자 스토리는 이해하기 쉽다. 고객이나 개발자 모두 이해할 수 있다.
- 사용자 스토리는 계획 수립에 적합한 크기다.
- 사용자 스토리는 반복적 개발(iterative development)에 효과적이다.
- 사용자 스토리는 세부사항을 나중에 고려할 수 있게 해준다.
- 사용자 스토리는 기회주의적 개발을 지원한다.
- 사용자 스토리는 참여적 설계를 유도한다.
- 사용자 스토리는 암묵적 지식을 구축한다.

### 스토리 냄새 카탈로그

- 너무 작은 스토리
  - 증상: 추정치를 빈번히 조정해야 함.
- 상호 의존적인 스토리
  - 증상: 스토리들 간의 의존성 때문에 이터레이션을 계획하기가 어려움.
- 금도금(goldplating)
  - 증상: 개발자들이 이터레이션 계획에 포함되지 않은 기능을 추가하거나 스토리를 마음대로 해석하여 그 스토리를 구현하는 데 필요한 것 이상의 작업을 하고 있다.
- 너무 상세한 스토리
  - 증상: 스토리 구현에 앞서 세부사항들을 모으는 데 시간을 과도하게 소비한다. 또는 스토리에 대해 이야기 나누는 것보다 스토리를 작성하는 데 시간을 더 많이 소비한다.
- 사용자 인터페이스와 관련된 세부사항을 너무 일찍 포함시키기
  - 증상: 프로젝트(특히 신제품 개발 프로젝트) 초기에 작성된 스토리들이 사용자 인터페이스와 관련된 세부사항들을 포함한다.
- 너무 앞서 생각하기
  - 증상: 이 냄새는 여러 가지 증상으로 확인할 수 있다. 스토리들을 인덱스 카드에 기록하기 어렵다거나, 팀의 규모나 위치 조건 때문에 어쩔 수 없는 경우가 아닌데도 인덱스 카드보다 소프트웨어를 활용하려고 한다거나, 누군가가 세부사항들까지 잡아내기 위한 스토리 템플릿을 제안한다거나, 더 상세한 (예를 들어 일 단위 대신 시간 단위의) 추정치를 부여할 것을 제안하는 등의 증상이 있다.
- 스토리를 너무 많이 나누기
  - 증상: 이터레이션을 계획할 때 작업량을 맞추기 위해 스토리를 나누는 경우가 많다.
- 고객이 우선순위 부여를 어려워 함
  - 증상: 스토리를 선택하고 우선순위를 부여하는 일은 어렵다. 때로는 스토리에 우선순위를 부여하는 것이 너무나 어려워 거기서 냄새가 날 수도 있다.
- 고객이 스토리를 작성하거나 우선순위를 부여하지 않으려고 함
  - 증상: 고객이 스토리를 작성하고 거기에 우선순위를 부여하는 책임을 지지 않으려고 한다.

### 스크럼에서 사용자 스토리 사용하기

#### XP와 마찬가지로 스크럼은 반복적이고 점진적인 프로세스다.

- 반복적(iterative) 프로세스는 계속적인 정련(refine) 작업을 통해 진행되는 프로세스를 의미한다.
- 점진적(incremental) 프로세스는 소프트웨어를 여러 부분으로 나누어 각 부분을 개별적으로 개발하고 전달하는 프로세스를 의미한다.

#### 스크럼의 기본

- 스크럼 프로젝트는 스프린트(sprint)라 불리는 30일 단위의 이터레이션을 통해 진행된다.
- 각 스프린트를 시작할 때, 스크럼 팀은 그 스프린트 동안 수행할 작업량을 결정한다.
- 수행할 작업들은 제품 백로그(product backlog)라 불리는 우선순위가 매겨진 목록에서 선택한다.
- 스크럼 팀이 해당 스프린트동안 완료하기 위해 선택한 작업들은 제품 백로그에서 스프린트 백로그(sprint backlog)라는 목록으로 옮겨진다.
- 매일 열리는 일일 스크럼 회의(Daily Scrum Meeting)에서는 현재 진행 상황을 파악하고 대처할 수 있도록 한다.

![[https://www.scrum.org/resources/what-is-scrum](https://www.scrum.org/resources/what-is-scrum)](../../image/agile/scrum.png)

[scrum.org](https://www.scrum.org/resources/what-is-scrum)

![[http://www.controlchaos.com/scaled-professional-scrum/](http://www.controlchaos.com/scaled-professional-scrum/)](../../image/agile/scrum-nexus.png)

[controlchaos.com](http://www.controlchaos.com/scaled-professional-scrum/)

#### 스크럼에 스토리 추가하기

- 제품 백로그에 사용자 스토리만을 넣도록 제한함으로써 제품 소유자가 우선순위를 부여하는 것이 훨씬 쉬워진다. 사용자 스토리로 작성된 백로그 항목들은 제품 소유자가 이해할 수 있는 용어로 기술되어 있으므로 제품 소유자가 기능 간 우선순위를 비교하는 것이 더 쉬워진다.
- 스프린트 계획 회의 동안 제품 소유자와 팀은 제품 백로그에서 우선순위가 가장 높은 항목들을 논의한다. 그리고 나서 팀은 해당 스프린트 동안 수행할 항목들을 골라낸다.