# 자바와 JUnit을 활용한 실용주의 단위 테스트

> 제프 랭어, 앤디 헌트, 데이브 토마스

- [자바와 JUnit을 활용한 실용주의 단위 테스트](#자바와-junit을-활용한-실용주의-단위-테스트)
  - [테스트 구성](#테스트-구성)
    - [Triple-A (AAA)](#triple-a-aaa)
    - [동작 테스트 vs. 메서드 테스트](#동작-테스트-vs-메서드-테스트)
    - [내부 동작 노출 vs. 내부 데이터 노출](#내부-동작-노출-vs-내부-데이터-노출)
    - [테스트 분리의 장점](#테스트-분리의-장점)
    - [단위 테스트는 문서 역할](#단위-테스트는-문서-역할)
  - [단위 테스트 (Unit Test) 가이드 라인](#단위-테스트-unit-test-가이드-라인)
    - [FIRST: 좋은 테스트의 속성](#first-좋은-테스트의-속성)
    - [Right-BICEP: 무엇을 테스트할 것인가?](#right-bicep-무엇을-테스트할-것인가)
    - [CORRECT: 경계 조건은 올바른가?](#correct-경계-조건은-올바른가)

## 테스트 구성

### Triple-A (AAA)

테스트 코드를 준비, 실행, 단언 부분으로 가시적으로 작성합니다.

- 준비(Arrange): 테스트 코드를 실행하기 전에 시스템이 적절한 상태에 있는지 확인합니다.
- 실행(Act): 테스트 코드를 실행합니다.
- 단언(Assert): 실행한 코드가 기대한 대로 동작하는지 확인합니다.

### 동작 테스트 vs. 메서드 테스트

- 단위 테스트를 작성할 때는 먼저 전체적인 시각에서 시작해야 합니다.
- 개별 메서드를 테스트하는 것이 아니라 클래스의 종합적인 동작을 테스트해야 합니다.

### 내부 동작 노출 vs. 내부 데이터 노출

- 비공개 코드를 호출하는 테스트는 그 자체로 구현 세부 사항과 결속하게 됩니다.
- 내부의 세부 사항을 테스트하는 것은 저품질로 이어질 수도 있습니다.
  코드의 작은 변화가 수많은 테스트를 자주 깨면 깰수록 프로그래머는 리팩토링을 꺼립니다.
  그리고 리팩토링이 줄어들수록 코드 베이스는 빠르게 퇴화합니다.
- 테스트를 위해 내부 데이터를 노출하는 것은 테스트와 프로덕션 코드 사이에 과도한 결합을 초래합니다.
  내부 동작을 노출하는 것은 다른 문제입니다.
- 내부 행위를 테스트하려는 충동이 든다면 설계에 문제가 있는 것입니다.

### 테스트 분리의 장점

- 단언이 실패했을 때 실패한 테스트 이름이 표시되기 때문에 어느 동작에서 문제가 있는지 빠르게 파악할 수 있습니다.
- 실패한 테스트를 해독하는 데 필요한 시간을 줄일 수 있습니다.
- 모든 케이스가 실행되었음을 보장할 수 있습니다. 단언이 실패하면 현재 테스트 메서드는 중단합니다.
  단언 실패는 `java.lang.AssertionError`를 던지기 때문입니다.

### 단위 테스트는 문서 역할

- 테스트는 코드 자체로 쉽게 설명할 수 없는 가능성들을 알려줍니다.
- 테스트가 없었으면 주석으로 적어 놓았을 많은 내용을 보충하기도 합니다.
- BDD 양식(given-when-then)을 예로 들 수 있습니다.

## 단위 테스트 (Unit Test) 가이드 라인

### FIRST: 좋은 테스트의 속성

- `F`ast: 빨라야 합니다.
  - 단위 테스트 스위트(suite)의 가치는 SUT에 대한 지속적이고 종합적인 빠른 피드백을 주지 못하면 그만큼 저하됩니다.
- `I`solated: 어떤 순서나 시간에 관계없이 실행할 수 있어야 합니다.
  - SRP에 따르면 클래스는 작고 단일한 목적을 가져야 합니다. 테스트를 실행하기 전에 수동으로 준비 단계를 만드는 어리석은 짓은 하지 마세요.
- `R`epeatable: 반복 가능해야 합니다.
  - 직접 통제할 수 없는 외부 환경에 있는 항목들과 격리시켜 실행할 때마다 결과가 같아야 합니다.
- `S`elf-validating: 스스로 검증 가능해야 합니다.
  - 테스트는 기대하는 것이 무엇인지 단언하지 않으면 테스트가 아닙니다.
- `T`imely: 적시에 작성해야 합니다.
  - 단위 테스트로 코드를 검증하는 것을 미룰수록 치석이 끼고 충치가 늘어날 것입니다.

### Right-BICEP: 무엇을 테스트할 것인가?

- `Right`: 결과가 올바른가?
- `B`oundary Conditions: 경계 조건은 맞는가?
  - [CORRECT](#correct-경계-조건은-올바른가)
- `I`nverse Relationship: 역 관계를 검사할 수 있는가?
  - 때때로 논리적인 역 관계를 적용하여 행동을 검사할 수 있습니다.
- `C`ross-Check: 다른 수단을 활용하여 교차 검사할 수 있는가?
  - 내가 선택한 해법이 올바른지 검사할 수 있는 다른 해법이 있는가?
  - 프로덕션 시스템에 활용하기에는 너무 느리거나 유연하지 않겠지만,
    그것들이 믿을 수 있고 참값을 보장한다면 기존에 선택한 최선의 해법을 교차 검사할 때 활용할 수 있습니다.
- `E`rror Conditions: 오류 조건을 강제로 일어나게 할 수 있는가?
  - 오류 조건을 강제로 일어나게 할 수 있는가?
  - 발생할 가능성이 있는 문제들을 예상하여 강제로 일어나게 하고 시뮬레이션 할 수 있어야 합니다.
- `P`erformance Characteristics: 성능 조건은 기준에 부합하는가?
  - 추측만으로 성능 문제에 바로 대응하기보다는 단위 테스트를 설계하여 진짜 문제가 어디에 있으며
    예상한 변경 사항으로 어떤 차이가 생겼는지 파악해야 합니다.
  - 느린 테스트는 빠른 것과 분리하세요. 성능 테스트는 야밤에 한 번이면 충분합니다.
  - 동일한 머신이라도 실행 시간은 시스템 로드처럼 잡다한 요소에 따라 달라질 수 있습니다.
  - (역주: 성능을 테스트할 때는 사전 조건을 단단하게 정의해 놓아야 반복성과 재현성을 보장할 수 있습니다)

### CORRECT: 경계 조건은 올바른가?

- `C`onformance: 준수
  - 값이 기대한 양식을 준수하고 있는가?
  - 모호하고 일관성 없는 입력 값. 예를 들어 특수 문자가 포함된 파일 이름(`"!*W:X\&Gi/w$→>$g/h#WQ@.txt`)
  - 잘못된 양식의 데이터. 예를 들어 최상위 도메인이 빠진 이메일 주소(`fred@foobar.`)
  - 헤더가 없거나 헤더만 있거나.
- `O`rdering: 순서
  - 값의 집합이 적절하게 정렬되거나 정렬되지 않았나?
  - 정렬 알고리즘에 이미 정렬된 입력 값을 넣는 경우나 정렬 알고리즘에 역순 데이터를 넣는 경우
- `R`ange: 범위
  - 이성적인 기댓값을 훨씬 벗어나는 값. (이성적인 최솟값과 최댓값 안에 있는가?)
  - 므두셀라(Methuselah)보다 나이가 많다거나 음수의 나이
  - 수치적 오버플로를 일으키는 계산
- `R`eference: 참조
  - 코드 자체에서 통제할 수 없는 어떤 외부 참조를 포함하고 있는가?
  - 범위를 넘어서는 것을 참조하고 있지 않은지
  - 외부 의존성은 무엇인지
  - 특정 상태에 있는 객체를 의존하고 있는지
  - 반드시 존재해야 하는 그 외 다른 조건들
- `E`xistence: 존재
  - 값이 존재하는가?
  - 비거나 빠진 값. 예를 들어 `0`, `0.0`, `""` 혹은 `null`
  - 널이 아니거나(non-null), 0이 아니거나(nonzero), 집합에 존재하는가 등
- `C`ardinality: 기수
  - 정확히 충분한 값들이 있는가?
  - 울타리 기둥 오류(fencepost errors)
  - 교실의 당번표처럼 중복을 허용해서는 안 되는 목록에 중복 값이 있는 경우
  - 0-1-n 법칙
- `T`ime: 모든 것이 순서대로 일어나는가? 정확한 시간에?
  - 절대적 시간(측정된 시간): DST(Daylight saving time), 윤년
  - 상대적 시간(시간 순서): 타임 아웃
  - 동시성 문제들: 책 <자바 병렬 프로그래밍>
  - HTTP 서버가 OPTIONS 메서드의 결과를 POST 메서드보다 먼저 반환해야 하지만 그 후에 반환하는 경우
