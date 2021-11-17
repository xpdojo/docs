# 엘레강트 오브젝트

- [엘레강트 오브젝트](#엘레강트-오브젝트)
  - [출생](#출생)
    - [`-er`로 끝나는 이름을 사용하지 마세요](#-er로-끝나는-이름을-사용하지-마세요)
    - [생성자 하나를 주 생성자로 만드세요](#생성자-하나를-주-생성자로-만드세요)
    - [생성자에 코드를 넣지 마세요 (code-free)](#생성자에-코드를-넣지-마세요-code-free)
  - [학습](#학습)
    - [가능하면 적게 캡슐화하세요](#가능하면-적게-캡슐화하세요)
    - [최소한 뭔가는 캡슐화하세요](#최소한-뭔가는-캡슐화하세요)
    - [항상 인터페이스를 사용하세요](#항상-인터페이스를-사용하세요)
    - [**메서드 이름을 신중하게 선택하세요**](#메서드-이름을-신중하게-선택하세요)
    - [퍼블릭 상수(public constant)를 사용하지 마세요](#퍼블릭-상수public-constant를-사용하지-마세요)
    - [불변 객체로 만드세요](#불변-객체로-만드세요)
    - [**문서를 작성하는 대신 테스트를 만드세요**](#문서를-작성하는-대신-테스트를-만드세요)
    - [**모의 객체(Mock) 대신 페이크 객체(Fake)를 사용하세요**](#모의-객체mock-대신-페이크-객체fake를-사용하세요)
    - [인터페이스를 짧게 유지하고 스마트(smart)를 사용하세요](#인터페이스를-짧게-유지하고-스마트smart를-사용하세요)
  - [취업](#취업)
    - [5개 이하의 public 메서드만 노출하세요](#5개-이하의-public-메서드만-노출하세요)
    - [정적 메서드를 사용하지 마세요](#정적-메서드를-사용하지-마세요)
    - [인자의 값으로 NULL을 절대 허용하지 마세요](#인자의-값으로-null을-절대-허용하지-마세요)
    - [충성스러우면서 불변이거나, 아니면 상수이거나](#충성스러우면서-불변이거나-아니면-상수이거나)
    - [절대 getter와 setter를 사용하지 마세요](#절대-getter와-setter를-사용하지-마세요)
    - [부 ctor 밖에서는 new를 사용하지 마세요](#부-ctor-밖에서는-new를-사용하지-마세요)
    - [인트로스펙션과 캐스팅을 피하세요](#인트로스펙션과-캐스팅을-피하세요)
  - [은퇴](#은퇴)
    - [절대 NULL을 반환하지 마세요](#절대-null을-반환하지-마세요)
    - [체크 예외(checked exception)만 던지세요](#체크-예외checked-exception만-던지세요)
    - [**final이나 abstract이거나**](#final이나-abstract이거나)
    - [RAII를 사용하세요](#raii를-사용하세요)

> **_이 책의 목표는 코드의 유지보수성(maintainability)을 향상시키는 것입니다._**

## 출생

객체지향 세계에 살고 있는 엔터티(entity)를 의인화하여 출생부터 은퇴까지를 다룹니다.

### `-er`로 끝나는 이름을 사용하지 마세요

- 클래스는 객체를 생성합니다. 일반적으로 클래스가 객체를 인스턴스화한다(instantiate)라고 표현합니다.
  - 클래스는 객체의 능동적인 관리자(active manager)라고 생각해야 한다는 것입니다.
  - 객체를 살아있는 생명체라고 생각한다면 클래스는 객체의 어머니라고 할 수 있습니다.
- 클래스의 이름은 무엇을 하는지(what he does)가 아니라 무엇인지(what he is)에 기반해야 합니다.
  - 클래스의 이름은 객체가 노출하고 있는 기능에 기반해서는 안됩니다!
  - 객체는 그의 역량(capability)으로 특징지어져야 합니다.
    제가 어떤 사람인지는 키, 몸무게, 피부색과 같은 속성(attribute)이 아니라, 제가 할 수 있는 일(what I can do)로 설명해야 합니다.
- 객체는 캡슐화된 데이터의 대표자(representative)입니다.
  - 객체는 외부 세계와 내부 세계를 이어주는 연결장치(connect`or`)가 아닙니다.
    - Manager, Controller, Helper, Handler, Writer, Reader, Converterm Validator, Router, Dispatcher, Observer, Listener, Sorter, Encoder, Decoder, Printer, Formatter, ...
  - 객체는 내부에 캡슐화된 데이터를 다루기 위해 요청할 수 있는 절차의 집합이 아닙니다.
  - 연결장치는 스스로 어떤 일을 수행할 만큼 똑똑하지 못하기 때문에 단순히 정보를 전달하기만 합니다.
  - 반면에 대표자는 스스로 결정을 내리고 행동할 수 있는 자립적인 엔터티입니다.
    - Target, EncodedText, DecodedData, Content, SortedLines, ValidPage, Source, ...

### 생성자 하나를 주 생성자로 만드세요

- 하나의 주 생성자(primary constructor)와 다수의 부 생성자(secondary constructor)는
  중복 코드를 방지하고 설계를 더 간결하게 만들기 때문에 유지보수성이 향상됩니다.

```java
class Cash {
  private int dollars;

  // 부 생성자
  Cash(float dlr) {
    this((int) dlr);
  }

  // 부 생성자
  Cash(String dlr) {
    this(Cash.parse(dlr));
  }

  // 주 생성자
  Cash(int dlr) {
    this.dollars = dlr;
  }
}
```

### 생성자에 코드를 넣지 마세요 (code-free)

- 진정한 객체지향에서 인스턴스화(instantiation)란 더 작은 객체들을 조합해서(compose) 더 큰 객체를 만드는 것을 의미합니다.
  - 새로운 계약을 준수하는 새로운 엔터티(entity)가 필요하기 때문입니다.
- 생성자 안에서 어떤 일을 처리하고 있다면 예측하기 어렵고 나중에 리팩토링하기가 훨씬 어렵습니다.

```java
class Cash {
  private int dollars;
  Cach(String dlr) {
    this.dollars = Integer.parseInt(dlr);
  }
}
```

## 학습

객체를 다른 객체와 상호작용할 수 있도록 준비시키기 위해 필요한 몇 가지 원칙을 설명합니다.
객체를 학교에 보내서 예의범절과 관련된 훌륭한 교훈을 몇 가지 가르칠 예정입니다.

### 가능하면 적게 캡슐화하세요

- OOP의 '객체'는 고수준의 행동을 낳기 위해 함께 동작하는 객체들의 집합체(aggregation)입니다.
  - 책은 페이지, 표지, ISBN의 집합체 - 책장은 책과 제목의 집합체
  - 자동차는 바퀴, 엔진, 앞 유리의 집합체 - 차고는 자동차와 주소의 집합체
  - 직원은 이름, 나이, 봉급의 집합체 - 회사는 직원, 이름, 관리자의 집합체
- 내부에 캡슐화된 객체 전체를 가리켜 객체의 '상태(state)' 또는 '식별자(identity)'라고 부릅니다.
  - **4개 또는 그 이하**의 객체를 캡슐화할 것을 권장합니다.
  - 더 많은 객체를 캡슐화해야 한다면, 클래스에 문제가 있는 것이기 때문에 리팩토링이 필요합니다.
  - 아래 클래스는 3개의 객체를 캡슐화하고, 이 3개가 모여 `Cash` 클래스의 객체를 식별합니다.
    다시 말해서 동일한 값의 달러, 센트, 통화를 캡슐화하는 `Cash` 클래스의 두 객체는 서로 동일하다는(same) 의미입니다.
    - Java 언어의 관점에서는 이것이 기술적으로 올바른 의미가 아니지만, 이것은 Java 언어가 안고 있는 설계적 결함 때문입니다.

```java
class Cash {
  private Integer digits;
  private Integer cents;
  private String currency;
}
```

```java
class Car {
  private Brand brand;
  private Model model;
  private VehicleIndentificationNumber vehicleIndentificationNumber;
  private Cash price;
}
```

- Java의 결함을 해결하기 위해 `==` 연산자를 사용하지 말고 `equals()` 메서드를 오버라이드하기 바랍니다.
  - `==`: 참조 변수의 주소값(`hashCode()`:int) 비교 / 원시값 비교
  - `equals()`: 참조 변수가 갖는 값 비교

### 최소한 뭔가는 캡슐화하세요

- 너무 많이 캡슐화하는 방식도 좋지 않지만, 아무것도 캡슐화하지 않는 방식 또한 바람직하지 않습니다.
- property가 없는 클래스는 객체지향 프로그래밍에서 악명이 높은 정적 메서드(static method)와 유사합니다.
- 객체가 '무(nothing)'와 아주 비슷한 어떤 것이 아니라면 무언가를 캡슐화해야 합니다.
- 오직 하나만 존재하고 생존이나 자신의 좌표를 표현하기 위해 다른 엔터티를 필요로 하지 않는 엔터티만이 아무 것도 캡슐화하지 않을 수 있습니다.
- 반대로 어떤 일을 수행하는 객체는 다른 객체들과 공존하면서 이들을 사용합니다.

### 항상 인터페이스를 사용하세요

- 객체들은 서로를 필요로 하기 때문에 결합(coupled)됩니다.
- 애플리케이션 전체를 유지보수 가능하도록 만들기 위해서는 객체를 분리해야(decoupled) 합니다.
  - 기술적인 관점에서 객체 분리란 상호작용하는 다른 객체를 수정하지 않고도 해당 객체를 수정할 수 있도록 만든다는 것을 의미합니다.
  - 이를 가능하게 하는 가장 훌륭한 도구가 인터페이스(interface)입니다.

### **메서드 이름을 신중하게 선택하세요**

- 뭔가를 만들고 새로운 객체를 반환하는 `빌더(builder)`의 이름은 `명사`로 짓습니다.
  - 일반적으로 제과점에 들러 "브라우니 주세요" 또는 "커피 한 잔 주세요"라고 말합니다.
    브라우니를 요리하거나 커피를 끓이는 정확한 방법은 제 관심사가 아닙니다.
  - 아래의 두 메서드는 실제로는 객체의 메서드가 아닙니다. 이들은 프로시저(procedure)입니다.
  - 우리는 지금 객체가 아닌 컴퓨터처럼 사고하고 있으며, 제과점을 신뢰하지 않습니다.
    따라서 취향에 맞는 커피를 주문하고나서 커피를 만드는 방법을 제과점에게 전적으로 위임하는 대신,
    "가서 이러이러한 커피를 끓여오세요"라고 구체적으로 지시하고 있는 것입니다.

```java
class Bakery {
  Food cookBrownie();
  Drink brewCupOfCoffee(String flavor);
}
```

- Java를 포함한 많은 언어에서 숫자는 객체가 아니라 스칼라(scala) 값이지만, 이것은 단지 이 언어들이 안고 있는 결함일 뿐입니다.
  진정한 객체지향 환경에서는 모든 것이 객체입니다.
  - ~~문자열, 숫자, 논리형, 비트와 바이트 역시 예외가 아닙니다.~~ (`Boolean` 래퍼 클래스가 아닌 `enabled`와 같은 값을 말하는 듯)
- 객체로 추상화한 실세계 엔터티를 수정하는 `조정자(manipulator)`의 이름은 `동사`로 짓습니다. 반환 타입은 항상 void입니다.
- 형용사나 부사를 넣어 더 풍부한 정보를 포함할 수 있습니다.
- 빌더와 조정자 사이에는 어떤 메서드도 존재해서는 안 됩니다.
  - 즉, 뭔가를 조작한 후 반환하거나, 뭔가를 만드는 동시에 조작하는 메서드가 있어서는 안된다는 것입니다.
- 빌더 패턴(pattern)은 유지보수성이 낮고 응집도가 떨어지는 더 커다란 객체를 만들도록 조장합니다.
  - 빌더 패턴은 생성자에 너무 많은 인자를 전달하고 싶지 않을 때 유용하게 사용할 수 있습니다.
    하지만 애초에 인자의 수가 많다는 것 자체가 문제입니다.
    빌더 패턴을 사용하는 대신 복잡한 객체를 더 작은 객체들로 나눠야 합니다.
- Boolean 값을 반환하는 메서드는 빌더에 속하지만, 가독성 측면에서 이름은 형용사로 지어야 합니다.

```java
boolean empty();    // is empty
boolean readble();  // is readble
boolean negative(); // is negative
boolean equalsTo(); // is equals to
boolean present();  // is present
```

### 퍼블릭 상수(public constant)를 사용하지 마세요

- '상수(constant)'라고도 불리는 `public static final` 프로퍼티는 객체 사이에 **데이터를 공유**하기 위해 사용하는 매우 유명한 메커니즘입니다.
- 하지만 객체들은 어떤 것도 공유해서는 안됩니다. 독립적이어야 하고 '닫혀 있어야(closed)' 합니다.
- 상수를 이용한 공유 메커니즘은 캡슐화와 객체지향적인 사고 전체를 부정하는 일입니다.
  코드 중복이라는 하나의 문제를 해결하기 위해 두 개의 더 큰 문제를 추가하는 것입니다.
  첫 번째 문제는 결합도(coupling)가 높아진 것이고, 두 번째 문제는 응집도(cohesion)가 낮아진 것입니다.
- 객체 사이에 데이터를 중복해서는 안 됩니다. 대신, **기능을 공유**할 수 있도록 **새로운 클래스**를 만들어야 합니다.
  - 작은 클래스를 많이 만드세요.
- Java의 열거형(enum)에 대해서도 정확하게 동일한 규칙이 적용됩니다. 열거형과 퍼블릭 상수 사이에는 아무런 차이도 없기 때문에 열거형 역시 사용해서는 안됩니다.
- `java.io.File`이 여러 코드에서 사용될 경우 정확하게 어떤 파일을 의미하는 지 파악하기 어려운 경우가 있습니다.
  - 대신 TextFile, JPGFile, TempFile을 사용한다면 코드를 이해하기가 훨씬 수월해집니다.

```java
String body = new HttpRequest()
  .method(HttpMethods.POST)
  .fetch();
```

```java
String body = new PostRequest(new HttpRequest())
  .fetch();
```

### 불변 객체로 만드세요

- 인스턴스를 생성한 후에 상태를 변경할 수 없는 객체를 불변 객체(immutagble object)라고 부릅니다.
- 불변 객체를 수정해야 한다면 프로퍼티를 수정하는 대신 새로운 객체를 생성해야 합니다.
- 가변 객체는 전반적인 객체 패러다임의 오용입니다. 절대로 가변 객체를 만들지 마세요.

```java
Cash five = new Cash(5);
five.mul(10); // five: $50
```

- 모든 사람들은 five 객체가 '5달러'처럼 행동할 것이라고 기대하지만 예상과 달리 객체는 '50달러'처럼 행동하고 있습니다.

```java
Cash five = new Cash(5);
Cash fifty = five.mul(10); // five: $5
```

- 5는 생명이 다하는 그 순간까지 항상 5입니다. five는 fifty가 될 수 없습니다.

```java
Cash money = new Cash(5); // money: $5
money.mul(10);            // money: $50
```

- 위와 같은 해결방법은 단순히 구체적인 이름을 추상적인 이름으로 대체한 것 뿐입니다.
  - 일반적으로 이런 방법은 형편없는 전략입니다. 극단적으로 모든 변수의 이름을 var로 지을 수도 있을 것입니다.
- 불변 클래스가 가변 클래스보다 더 좋다고 주장하는 것이 아니라, 가변 객체는 존재해서는 안된다는 것입니다.
  가변성은 절차적인 프로그래밍의 끔찍한 유산입니다.
- Haskell 언어에서 제약하는 방식처럼 게임, UI, 모바일, 알고리즘 등 도메인의 종류와 상관없이
  모든 클래스는 상태를 절대로 변경하지 않는 불변 객체를 인스턴스화 해야 합니다.
- 250줄을 넘는 클래스는 리팩토링이 필요합니다. Ruby의 경우에는 100줄 이하로 유지하는 것이 좋습니다.
- 불변 객체을 사용해야 하는 이유
  - 식별자 가변성(Indentity Mutability) 문제가 없습니다.
  - 실패 원자성(Failure Atomicity)을 가집니다. 실패 원자성이란 완전하고 견고한 상태의 객체를 가지거나 아니면 실패하거나 둘 중 하나만 가능한 특성입니다. (트랜잭션과 동일)
  - 시간적 결합(Temporal Coupling)을 제거할 수 있습니다.
  - 부수효과를 제거할 수 있습니다. (Side effect-free)
  - NULL 참조를 제거할 수 있습니다.
  - 스레드 안전성(Thread Safety)을 가집니다.
  - 객체를 더 작고 더 단순하게(Simplicity) 만듭니다.

```java
Cash price = new Cash();
price.setDollars(29);
price.setCents(95);
System.out.println(price); // "$29.95"
```

_시간적 결합이란?_ 먼저, 모든 private 프로퍼티가 NULL 값을 가지도록 '골격(skeleton)'을 만듭니다(인스턴스화).
그리고 나서 'setter'를 이용해 프로퍼티 값들을 설정합니다(초기화).
이 방법은 JavaBeans, JPA, JAXB 등의 다양한 표준에서 Java 객체를 조작하기 위해 권장하는 방식입니다.
이런 표준들은 진정한 '객체 사고(object thinking)'의 관점에서는 완전히 잘못된 방식입니다.
가변 객체의 수가 많은 상황에서 가변 객체들을 처리하는 연산들의 순서를 일일이 기억해야 한다면
유지보수하기 어려워집니다.

### **문서를 작성하는 대신 테스트를 만드세요**

- 더 읽기 쉬운 코드를 만들기 위해서는, 코드를 읽게 될 사람이 비즈니스 도메인,
  프로그래밍 언어, 디자인 패턴, 알고리즘을 거의 이해하지 못하는 주니어 프로그래머라고 가정해야 합니다.
- 이상적인 코드는 스스로를 설명하기 때문에 어떤 추가 문서도 필요하지 않습니다.

```java
Employee jeff = department.employee("Jeff");
jeff.giveRaise(new Cash("$5,000"));
if (jeff.performance() < 3.5) {
  jeff.fire();
}
```

```java
class WebPage {
  String content() { ... }
  void update(String content) { ... }
}
```

- 위와 같은 코드는 코드 자체만으로도 의미가 명확하게 전달된다고 생각합니다.

```java
class Helper {
  int saveAndCheck(float x) { ... }
  float extract(String text) { ... }
  boolean convert(int value, boolean extra) { ... }
}
```

- 반면에 위와 같은 코드는 메서드의 이름도 형편없고 클래스 이름도 엉망인데다
  '클래스'의 전반적인 설계 역시 형편 없습니다.
- 나쁜 설계는 문서를 작성하도록 강요합니다.
  - 코드만으로는 이 클래스가 어떤 일을 하는지, 메서드의 목적이 무엇인지, 메서드를 어떻게 사용해야 하는 지를 도무지 이해할 수가 없습니다.
- Cash라는 클래스를 테스트하는 '클래스'의 이름은 관례에 따라 CashTest로 짓지만 이를 허용해서는 안됩니다.
  - 단위 테스트가 없는 상황에서도 클래스를 추가할 수 있습니다.
- 올바르게 작성된 단위 테스트는 여러분의 클래스를 이해하는데 큰 도움이 되고 국제적이기도 합니다.
  - Java로 작성된 단위 테스트를 이해하기 위해서 영어에 유창할 필요는 없습니다.
  - 하지만 Javadoc을 이해하기 위해서는 어느 정도의 영어 독해 능력이 요구됩니다.
- 한 장의 그림이 수천 단어 만큼의 가치가 있는 것처럼, 하나의 단위 테스트는 한 페이지 분량의 문서 만큼이나 가치가 있습니다.
  - (문서를 봐도 동작 방식이 이해되지 않을 때, GitHub에서 소스를 검색하는 것과 같지 않을까...)

### **모의 객체(Mock) 대신 페이크 객체(Fake)를 사용하세요**

- Fake를 사용하면 테스트를 더 짧게 만들 수 있기 때문에 유지보수성이 눈에 띄게 향상됩니다.
- 반면에 Mocking의 경우, 테스트가 매우 장황해지고, 이해하거나 리팩토링하기 어려워 집니다.
  - 단순히 장황함만이 문제가 아니라 Mocking은 가정(assumption)을 사실(facts)로 전환시키기 때문에 단위 테스트를 유지보수하기 어렵게 만듭니다.
- 클래스의 행동이 변경되면 단위 테스트가 실패하기 때문에, 단위 테스트는 코드 리팩토링에 큰 도움이 됩니다(참 양성, true positive).
  - 하지만 동시에 행동이 변경되지 않을 경우에는 실패해서는 안됩니다(거짓 양성, false positive).
- 우리의 관심사는 클래스와 우리 사이의 상호작용 방법이지 클래스가 다른 클래스와 상호작용하는 방법이 아닙니다.
  - 우리에게는 객체의 구현 방법을 알 권리가 없습니다.
  - 테스트가 객체 내부의 구현 세부사항을 알면 테스트가 취약해지고 유지보수하기도 어려워집니다.

### 인터페이스를 짧게 유지하고 스마트(smart)를 사용하세요

- 클래스를 작게 만드는 것이 중요하다면 인터페이스를 작게 만드는 것은 훨씬 더 중요합니다.
  - 클래스가 다수의 인터페이스를 구현하기 때문입니다.
  - 만약 두 개의 인터페이스가 각각 5개의 메서드를 선언하고 있다면, 두 인터페이스를 모두 구현하는 클래스는 10개의 public 메서드를 가집니다.

```java
interface Exchange {
  float rate(String target);
  float rate(String source, String target);
}
```

- 하나의 인자를 받는 rate() 메서드는 이 인터페이스에 포함되어서는 안됩니다.

```java
interface Exchange {
  float rate(String source, String target);
  final class Smart {
    private final Exchange origin;
    public float toUsd(String source) {
      return this.origin.rate(source, "USD");
    }
  }
}
```

- 이 스마트 클래스는 아주 명확하고 공통적인 작업을 수행하는 많은 메서드들을 포함할 수 있습니다.

## 취업

지금까지 설명한 내용이 지나치게 추상적이고 이론적으로 느껴질 수도 있지만, 실제로는 매우 현실적인 이야기입니다.
이번 장에서는 앞에서 살펴본 내용들의 이유를 설명하고 유용한 예제들을 제공합니다.
한 문장으로 요약하면 거대한 객체, 정적 메서드, NULL 참조, getter, setter, new 연산자에 반대한다는 것입니다.

### 5개 이하의 public 메서드만 노출하세요

- 가장 우아하고, 유지보수가 가능하고, 응집력이 높으면서, 테스트하기도 용이한 객체는 작은 객체입니다.
- 클래스의 크기를 정하는 기준으로 public 메서드(protected 메서드 포함)의 개수를 사용하기를 권합니다.
  - 개인적으로 적절하다고 생각하는 public 메서드의 수는 5개입니다.
  - '정확한' 숫자를 찾는 것은 불가능합니다.
  - 5라는 숫자가 무조건 따라야 하는 절대적인 기준은 아닙니다.
- 클래스가 작으면 메서드와 프로퍼티가 더 '가까이' 있을 수 있기 때문에 응집도가 높아집니다.
  - 각각의 메서드가 클래스의 모든 프로퍼티를 사용합니다. 그리고 이것이 응집도의 정의이기도 합니다.

### 정적 메서드를 사용하지 마세요

- OOP에 정적 메서드를 도입한 결정은 NULL을 도입한 것 이상으로 커다란 실수입니다.
  - 더 나은 방식은 정적 메서드 대신 객체를 사용하는 것입니다.
- object vs. computer thinking
  - 정적 메서드는 소프트웨어를 유지보수하기 어렵게 만듭니다.
  - 객체지향 언어의 문법을 이용해서 절차적인 코드를 작성하도록 부추길 뿐입니다.
- declarative vs. imperative
  - 선언형 프로그래밍에서는 제어 흐름을 서술하지 않고 계산 로직을 표현합니다.
  - 명령형 프로그래밍에서는 프로그램의 상태를 변경하는 문장(statement)을 사용해서 계산 방식을 서술합니다.

### 인자의 값으로 NULL을 절대 허용하지 마세요

```java
public Iterable<File> find(String mask) {
  if (mask == null) {
    // 모든 파일을 찾는다
  } else {
    // 마스크를 사용해서 파일을 찾는다
  }
}
```

- 이 코드에서 문제가 되는 부분은 `mask == null`입니다.
  - mask 객체에게 **이야기하는** 대신, 이 객체를 피하고 무시합니다.
  - mask 객체를 존중했다면 조건의 존재 여부를 객체 스스로 결정하게 했을 것입니다.

### 충성스러우면서 불변이거나, 아니면 상수이거나

```java
class WebPage {
  private final URI uri;

  WebPage(URI path) {
    this.uri = path;
  }

  public String content() {
    // HTTP GET 요청을 전송해서,
    // 웹 페이지의 컨텐츠를 읽은 후,
    // 읽혀진 컨텐츠를 UTF-8 문자열로 변환한다
  }
}
```

- 상수(constant)는 항상 동일한 데이터를 반환합니다.
- 불변 객체는 결과가 변하기 때문에 상수는 아니지만, 객체가 대표하는 엔터티에 '충성하기(loyal)' 때문에 불변 객체로 분류됩니다.

```java
public void echo() {
  File f = new File("/tmp/test.txt");
  System.out.println("File size: %d", f.length());
}
```

- 객체란 디스크에 있는 파일, 웹 페이지, 바이트 배열, 해시맵, 달력의 월과 같은 실제 엔터티(reallife entity)의 대표자(representative)입니다.
  - 모든 객체는 식별자(identity), 상태(state), 행동(behavior)을 포함합니다.
  - 식별자는 f를 다른 객체와 구별합니다.
  - 상태는 f가 디스크 상의 파일에 대해 알고 있는 것입니다. (ex: 파일의 좌표)
  - 행동은 요청을 수신했을 때 f가 할 수 있는 작업을 나타냅니다. (ex: 길이 반환)
  - 위에서 객체 f는 `/tmp/test.txt` 파일의 대표자입니다. 객체 f는 실제 파일의 입장을 대변합니다.
    우리는 파일의 사이즈를 알아내기 위해 객체 f의 `length()` 메서드와 의사소통하고 있습니다.
- 불변 객체에는 식별자가 존재하지 않으며, 절대로 상태를 변경할 수 없습니다.
  [불변 객체의 식별자는 객체의 상태와 완전히 동일합니다](#가능하면-적게-캡슐화하세요).
  - 동일한 URI를 가진 두 개의 WebPage 인스턴스를 생성할 경우, 두 객체는 동일한 실제 웹 페이지를 대표합니다.
  - 별도로 인스턴스를 생성했다고 하더라도, 두 객체는 동일합니다.

```java
class WebPage {
  private final URI uri;

  WebPage(URI path) {
    this.uri = path;
  }

  @Override
  public void equals(Object obj) {
    return this.uri.equals(WebPage.class.cast(obj).uri);
  }

  @Override
  public int hashCode() {
    return this.uri.hashCode();
  }
}

```

### 절대 getter와 setter를 사용하지 마세요

```c
// 구조체 in C
struct Cash {
  int dollars;
}

printf("Cash value is %d", cash.dollars);
```

```cpp
// 클래스 in C++
#include <string>
class Cash {
public:
  Cash(int v): dollars(v) {};
  std::string print() const;
private:
  int dollars;
};

printf("Cash value is %s", cash.print());
```

- struct의 경우, 멤버인 dollars에 직접 접근한 후 해당 값을 정수로 취급합니다.
  - struct를 가지고는 어떤 일도 하지 않으며, struct와 아무런 의사소통도 하지 않습니다.
- 반면에 클래스는 어떤 식으로든 멤버에게 접근하는 것을 허용하지 않습니다.
  - 게다가 자신의 멤버를 노출하지도 않습니다. 이것이 바로 캡슐화(encapsulation)입니다.
- 객체가 일급 시민이며, 생성자를 통한 객체 초기화가 곧 소프트웨어입니다.
  - 소프트웨어는 연산자나 구문이 아닌 생성자를 통해 구성됩니다.
  - 코드는 OOP에서 부차적인 요소입니다.
- 근본적으로 getter와 setter는 캡슐화 원칙을 위반하기 위해 설계되었습니다.
  - `getDollars()`는 "데이터 중에 dollars를 찾은 후 반환하세요"라고 이야기합니다.
  - `dollars()`는 객체를 데이터의 저장소로 취급하지 않고, 객체를 존중합니다. 결코 이 객체를 자료구조(struct)라고 생각하지 않습니다.

### 부 ctor 밖에서는 new를 사용하지 마세요

```java
class Cash {
  private final int dollars;

  public int euro() {
    return new Exchange().rate("USD", "EUR") * this.dollars;
  }
}

Cash five = new Cash("5.00");
print("$5 equals to %d", five.euro());
```

- 이 코드의 문제는 '하드코딩된 의존성(hard-coded dependency)'입니다.
  - Cash 클래스는 Exchange 클래스에 직접 연결되어 있기 때문에,
    의존성을 끊기 위해서는 Cash 클래스의 내부 코드를 변경할 수 밖에 없습니다.

```java
class Cash {
  private final int dollars;
  private final Exchange exchange;

  // 부 생성자
  Cash() {
    this(0);
  }

  // 부 생성자
  Cash(int value) {
    this(value, new NYSE());
  }

  // 주 생성자
  Cash(int value, Exchange exch) {
    this.dollars = value;
    this.exchange = exch;
  }

  public int euro() {
    return this.exchange.rate("USD", "EUR") * this.dollars;
  }
}

Cash five = new Cash(5, new FakeExchange());
print("$5 equals to %d", five.euro());
```

- 클래스의 부 생성자를 제외한 어떤 곳에서도 `new`를 사용하지 마세요.

### 인트로스펙션과 캐스팅을 피하세요

- 타입 인트로스펙션(introspection)은 리플렉션(reflection)이라는 더 포괄적인 용어로 불리는 여러 가지 기법들 중 하나입니다.
  - 리플렉션을 사용하면 메서드, 명령어, 구문, 클래스, 객체, 타입 등을 변경할 수 있습니다.
  - 코드가 런타임에 다른 코드에 의해 수정된다는 사실을 항상 기억해야 한다면, 코드를 읽기가 매우 어려울 것입니다.
- 런타임에 객체의 타입을 조사(introspect)하는 것은 클래스 사이의 결합도가 높아지는 것입니다.
  - 메서드 오버로딩(method overloading)을 사용하세요.
  - `instanceof` 연산자나 클래스 캐스팅(class casting)을 사용하지 마세요.

## 은퇴

메서드 결과로 반환되는 NULL, 예외 처리, 리소스 획득에 관해 살펴봅니다.
이번 장에서 다루는 내용은 논쟁의 여지가 있으며 아직까지 실용적인 수준이라고 말하기는 어렵습니다.

### 절대 NULL을 반환하지 마세요

- 반환값을 검사하는 방식은 애플리케이션에 대한 신뢰가 부족하다는 명백한 신호입니다.
- 소프트웨어 견고성(software robustness)과 실패 탄력회복성(failure resilience) 관련해서 상반되는 두 가지 철학이 존재합니다.
  - 필자는 빠르게 실패하기(fail fast)의 열렬한 지지자이며,
    안전하게 실패하기(fail safe)에 대해서는 강하게 반대하는 입장입니다.
  - 안전하게 실패하기는 버그, 입출력 문제, 메모리 오버플로우 등이 발생한 상황에서도
    소프트웨어 계속 실행될 수 있도록 최대한 많은 노력을 기울일 것을 권장합니다.

```java
public User user(String name) {
  if (/* 데이터베이스에서 발견하지 못했다면 */) {
    return null;
  }
  return /* 데이터베이스로부터 */;
}
```

- 위와 같은 코드는 '안전하게 실패하기' 철학과 매우 유사합니다.

```java
public Collection<User> users(String name) {
  if (/* 데이터베이스에서 발견하지 못했다면 */) {
    return new ArrayList<>(0);
  }
  return Collections.singleton(/* 데이터베이스로부터 */);
}
```

- 위와 같은 코드는 기술적으로 NULL과 크게 다르지 않지만 더 깔끔합니다.
  - 이 경우 클라이언트는 객체를 추출하기 위해서 어떤 식으로든 컬렉션에 접근해야만 합니다.
- 찾지 못한 뭔가를 반환할 필요가 있다면 NULL 대신
  컬렉션을 반환하거나, 예외를 던지거나, 널 객체(null object)를 반환하세요.
  이 세 가지 방법이 최선입니다.
- `java.util.Optional`은 컬렉션과 동일하지만, 오직 하나의 요소만 포함할 수 있습니다.
  - 의미론적으로 부정확하기 때문에 OOP와 대립한다고 생각하며 사용을 권하지 않습니다.
  - 메서드 이름은 user()지만, 실제로 반환하는 객체는 사용자가 아니라 사용자를 포함하는 일종의 봉투입니다.
    마치 NULL 참조와 매우 비슷합니다.

### 체크 예외(checked exception)만 던지세요

- 언체크 예외(unchecked exception)를 사용하는 것은 실수이며, 모든 예외는 체크 예외(checked exception)여야 합니다.
  - 언체크 예외의 경우 예외의 타입을 선언하지 않아도 무방한 반면에 체크 예외는 항상 예외의 타입을 공개해야 합니다.
- 가능하면 예외를 더 높은 레벨로 전파하세요.
  - 반드시 예외를 잡아야 하는 이유가 있거나 다른 선택의 여지가 없는 경우가 아니라면 예외를 잡아서는 안됩니다.
  - '잡아서 로깅하기(catching and logging)'는 끔찍한 안티패턴입니다.
  - 문제가 발생한 장소에서 어떻게든 문제를 해결해서 소프트웨어를 견고하게 만드는 철학은
    코드 전체를 유지보수하기 어렵고 매우 불안정하게 만듭니다.

```java
public int length(File file) {
  try {
    return content(file).length();
  } catch (IOException ex) {
    return 0;
  }
}
```

- 위 코드는 안전하게 실패하기 방법의 전형적인 예로 `length()` 메서드는 더할 나위 없이 안전합니다.
  - 파일 시스템에 어떤 일이 발생하더라도 메서드는 종료되지 않습니다.
  - 이런 접근방법을 '흐름 제어를 위한 예외 사용(using exceptions for flow control)'이라고 부릅니다.
  - 예외는 분기를 위한 도구가 아닙니다.

```java
public int length(File file) throws Exception {
  try {
    return content(file).length();
  } catch (IOException ex) {
    throw new Exception("길이를 계산할 수 없다.", ex);
  }
}
```

- 항상 예외를 체이닝(exception chaining)하고 절대로 원래 예외를 무시하지 마세요.
  - 여기에서 핵심은 문제를 발생시켰던 낮은 수준의 근본 원인(root cause) `ex`를 소프트웨어의 더 높은 수준으로 이동시켰다는 것입니다.

```java
public int length(File file) throws Exception {
  try {
    return content(file).length();
  } catch (IOException ex) {
    // 근본 원인인 `ex`를 무시하고
    // 새로운 메시지를 가지는 새로운 타입의 새로운 문제를 생성한다.
    throw new Exception("계산할 수 없다.");
  }
}
```

- 위의 코드는 문제를 발생시킨 근본 원인에 관한 매우 가치있는 정보가 손실되기 때문에 매우 나쁜 프랙티스입니다.
- 다만, 최상위 수준(진입점)에서는 예외를 되던지지 않고 잡아야 합니다.
  - 예를 들어, main 함수에서 예외를 잡지 않는다면 런타임 환경으로 예외가 전달되고
    결국 JVM이 예외를 잡게 됩니다. 이 경우에도 사용자는 메시지를 보지만, 그 메시지는 사용자 친화적이지 않을 것입니다.
    스택 트레이스 전체를 노출하는 시스템 메시지가 사용자에게 출력될 것입니다.
  - 이곳이 복구하기에 적합한 유일한 장소입니다.
  - 항상 예외를 잡고, 체이닝하고, 다시 던지세요. 가장 최상위 수준에서 오직 한번만 복구하세요.
- 관점-지향 프로그래밍(AOP, aspect-oriented programming)을 사용하세요.
  - 핵심 클래스로부터 덜 중요한 기술과 메커니즘을 분리해서 코드 중복을 제거할 수 있습니다.

### **final이나 abstract이거나**

- 대부분의 경우 캡슐화가 상속(inheritance)보다 더 나은 대안입니다.
- 클래스를 쌓아 만든 피라미드의 높이가 5단계를 넘어가는 순간부터는 상속 관계로 연결된 클래스의 계층 구조를 이해하기 어려워집니다.

```java
class Document {
  public int length() {
    return this.content().length();
  }
  public byte[] content() {
    // 문서의 내용을
    // 바이트 배열로 로드한다
  }
}

class EncryptedDocument extends Document {
  @Override
  public byte[] content() {
    // 문서를 로드해서,
    // 즉시 보호하고,
    // 복호화한 내용을 반환한다.
  }
}
```

- 문제를 일으키는 주범은 가상 메서드(virtual method)입니다.
  - 클래스와 메서드를 final이나 abstract 둘 중 하나로만 제한한다면 문제가 발생할 수 있는 가능성을 없앨 수 있습니다.

```java
interface Document {
  int length();
  byte[] content();
}

final class DefaultDocument implements Document {
  @Override
  public int length() {
    // 동일
  }
  @Override
  public byte[] content() {
    // 동일
  }
}

final class EncryptedDocument implements Document {
  private final Document plain;
  EncryptedDocument(Document doc) {
    this.plain = doc;
  }
  @Override
  public int length() {
    return this.plain.length();
  }
  @Override
  public byte[] content() {
    byte[] raw = this.plain.content();
    return /* 원래 내용(raw)을 복호화한다 */;
  }
}
```

- 클래스의 행동을 확장(extend)하지 않고 정제(refine)할 때는 상속이 적절합니다.
  - 확장이란 새로운 행동을 추가해서 기존의 행동을 부분적으로 보완하는 일을 의미합니다.
  - 정제란 부분적으로 불완전한 행동을 완전하게 만드는 일을 의미합니다.

```java
abstract class Document {
  public abstract byte[] content();
  public final int length() {
    return this.content().length;
  }
}

// refine
final class DefaultDocument extends Document {
  @Override
  public byte[] content() {
    // 디스크에서 내용을 로드한다.
  }
}

// refine
final class EncryptedDocument extends Document {
  @Override
  public byte[] content() {
    // 디스크에서 내용을 로드하고,
    // 내용을 암호화한 후 반환한다.
  }
}
```

### RAII를 사용하세요

- 리소스 획득이 초기화(RAII, Resource Acquisition Is Initialization)는 C++에 존재하는 매우 강력한 기법입니다.
- 여기에서 요령은 객체가 살아있는 동안에만 리소스를 확보하는 것입니다.
- 객체가 더 이상 필요하지 않으면 리소스를 해제하고 객체는 파괴됩니다.
- Java를 포함한 많은 고수준 언어에는 파괴자가 존재하지 않고 GC를 사용하기 때문에
  RAII 기법을 적용할 수 없습니다.
- 하지만 Java 7 에서 try-with-resources 기법을 사용해 RAII와 유사한 처리를 할 수는 있습니다.

```java
int main() {
  try (Text t = new Text("/tmp/test.txt")) {
    t.content();
  }
}
```

- 이 방법을 사용하기 위해서는 Text 클래스가 `Closable` 인터페이스를 구현하도록만 하면 됩니다.
- 파일, 스트림, 데이터베이스 커넥션 등 실제 리소스를 사용하는 모든 곳에서 RAII를 사용할 것을 적극 추천합니다.
