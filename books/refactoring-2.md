# <리팩터링> 2판 - 마틴 파울러

- [<리팩터링> 2판 - 마틴 파울러](#리팩터링-2판---마틴-파울러)
  - [리팩터링 첫 단계](#리팩터링-첫-단계)
  - [리팩터링 원칙](#리팩터링-원칙)
    - [리팩터링하는 이유](#리팩터링하는-이유)
    - [언제 리팩터링해야 할까?](#언제-리팩터링해야-할까)
  - [코드에서 나는 악취 - 켄트 벡 공저](#코드에서-나는-악취---켄트-벡-공저)
  - [테스트 구축하기](#테스트-구축하기)
  - [리팩터링 카탈로그](#리팩터링-카탈로그)
    - [기본적인 리팩터링](#기본적인-리팩터링)
      - [함수 추출하기 (Extract Function)](#함수-추출하기-extract-function)
      - [함수 인라인하기 (Inline Function)](#함수-인라인하기-inline-function)
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

리팩터링: \[동사\]소프트웨어의 겉보기 동작(observable behavior)은 그대로 유지한 채, 여러 가지 리팩터링 기법을 적용해서 소프트웨어를 재구성(restructuring)하다.

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
  - 보기 싫은 코드를 보면 리팩터링해야 함은 당연하지만, 잘 작성된 코드 역시 수많은 리팩터링을 거쳐야 한다.
- 오래 걸리는 리팩터링

TODO: 정리

## 코드에서 나는 악취 - 켄트 벡 공저

| #   | 악취                                 | Smell                                         | 설명 | 탈취 리팩터링                                                                                                                                                                                                                                    |
| --- | ------------------------------------ | --------------------------------------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1   | 기이한 이름                          | Mysterious Name                               |      | [함수 선언 바꾸기](#함수-선언-바꾸기), [변수 이름 바꾸기](#변수-이름-바꾸기), [필드 이름 바꾸기](#필드-이름-바꾸기)                                                                                                                              |
| 2   | 중복 코드                            | Duplicated Code                               |      |                                                                                                                                                                                                                                                  |
| 3   | 긴 함수                              | Long Function                                 |      |                                                                                                                                                                                                                                                  |
| 4   | 긴 매개변수 목록                     | Long Parameter List                           |      |                                                                                                                                                                                                                                                  |
| 5   | 전역 데이터                          | Global Data                                   |      |                                                                                                                                                                                                                                                  |
| 6   | 가변 데이터                          | Mutable Data                                  |      | [변수 캡슐화하기](#변수-캡슐화하기), 변수 쪼개기, 문장 슬라이드하기, 함수 추출하기, 질의 함수와 변경 함수 분리하기, 세터 제거하기, 파생 변수를 질의 함수로 바꾸기, 여러 함수를 클래스로 묶기, 여러 함수를 변환 함수로 묶기, 참조를 값으로 바꾸기 |
| 7   | 뒤엉킨 변경                          | Divergent Change                              |      |                                                                                                                                                                                                                                                  |
| 8   | 산탄총 수술                          | Shotgun Surgery                               |      |                                                                                                                                                                                                                                                  |
| 9   | 기능 편애                            | Feature Envy                                  |      |                                                                                                                                                                                                                                                  |
| 10  | 데이터 뭉치                          | Data Clumps                                   |      |                                                                                                                                                                                                                                                  |
| 11  | 기본형 집착                          | Primitive Obsession                           |      |                                                                                                                                                                                                                                                  |
| 12  | 반복되는 switch문                    | Repeated Switches                             |      |                                                                                                                                                                                                                                                  |
| 13  | 반복문                               | Loops                                         |      |                                                                                                                                                                                                                                                  |
| 14  | 성의 없는 요소                       | Lazy Element                                  |      |                                                                                                                                                                                                                                                  |
| 15  | 추측성 일반화                        | Speculative Generality                        |      |                                                                                                                                                                                                                                                  |
| 16  | 임시 필드                            | Temporary Field                               |      |                                                                                                                                                                                                                                                  |
| 17  | 메시지 체인                          | Messafge Chains                               |      |                                                                                                                                                                                                                                                  |
| 18  | 중개자                               | Middle Man                                    |      |                                                                                                                                                                                                                                                  |
| 19  | 내부자 거래                          | Insider Trading                               |      |                                                                                                                                                                                                                                                  |
| 20  | 거대한 클래스                        | Large Class                                   |      |                                                                                                                                                                                                                                                  |
| 21  | 서로 다른 인터페이스의 대안 클래스들 | Alternative Classes with Different Interfaces |      |                                                                                                                                                                                                                                                  |
| 22  | 데이터 클래스                        | Data Class                                    |      |                                                                                                                                                                                                                                                  |
| 23  | 상속 포기                            | Refused Bequest                               |      |                                                                                                                                                                                                                                                  |
| 24  | 주석                                 | Comments                                      |      |                                                                                                                                                                                                                                                  |

## 테스트 구축하기

모든 테스트를 완전히 자동화하고 그 결과까지 스스로 검사하게 만들자.

## 리팩터링 카탈로그

### 기본적인 리팩터링

#### 함수 추출하기 (Extract Function)

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

#### 함수 인라인하기 (Inline Function)

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

```javascript
let basePrice = anOrder.basePrice;
return basePrice > 1000;
```

```javascript
return anOrder.basePrice > 1000;
```

#### 함수 선언 바꾸기

```javascript
function circum(radius) {...}
```

```javascript
function circumference(radius) {...}
```

#### 변수 캡슐화하기

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

```javascript
let a = height * width;
```

```javascript
let area = height * width;
```

#### 매개변수 객체 만들기

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

```javascript
orders.filter((o) => "high" === o.priority || "rush" === o.priority);
```

```javascript
orders.filter((o) => o.priority.higherThan(new Priority("normal")));
```

#### 임시 변수를 질의 함수로 바꾸기

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

#### 필드 옮기기

#### 문장을 함수로 옮기기

#### 문장을 호출한 곳으로 옮기기

#### 인라인 코드를 함수 호출로 바꾸기

#### 문장 슬라이드하기

#### 반복문 쪼개기

#### 반복문을 파이프라인으로 바꾸기

#### 죽은 코드 제거하기

### 데이터 조직화

#### 변수 쪼개기

#### 필드 이름 바꾸기

#### 파생 변수를 질의 함수로 바꾸기

#### 참조를 값으로 바꾸기

#### 값을 참조로 바꾸기

#### 매직 리터럴 바꾸기

### 조건부 로직 간소화

#### 조건문 분해하기

#### 조건식 통합하기

#### 중첩 조건문을 보호 구문으로 바꾸기

#### 조건부 로직을 다형성으로 바꾸기

#### 특이 케이스 추가하기

#### 어서션 추가하기

#### 제어 플래그를 탈출문으로 바꾸기

### API 리팩터링

#### 질의 함수와 변경 함수 분리하기

#### 함수 매개변수화하기

#### 플래그 인수 제거하기

#### 객체 통째로 넘기기

#### 매개변수를 질의 함수로 바꾸기

#### 질의 함수를 매개변수로 바꾸기

#### 세터 제거하기

#### 생성자를 팩터리 함수로 바꾸기

#### 함수를 명령으로 바꾸기

#### 명령을 함수로 바꾸기

#### 수정된 값 반환하기

#### 오류 코드를 예외로 바꾸기

#### 예외를 사전확인으로 바꾸기

### 상속 다루기

#### 메서드 올리기

#### 필드 올리기

#### 생성자 본문 올리기

#### 메서드 내리기

#### 필드 내리기

#### 타입 코드를 서브클래스로 바꾸기

#### 서브클래스 제거하기

#### 슈퍼클래스 추출하기

#### 계층 합치기

#### 서브클래스를 위임으로 바꾸기

#### 슈퍼클래스를 위임으로 바꾸기
