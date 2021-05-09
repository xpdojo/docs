# 커밋 메시지 작성

- [커밋 메시지 작성](#커밋-메시지-작성)
  - [참고](#참고)
  - [개요](#개요)
    - [git 커밋 메시지를 잘 쓰려고 노력해야 하는 이유](#git-커밋-메시지를-잘-쓰려고-노력해야-하는-이유)
  - [기준 세우기](#기준-세우기)
    - [AngularJS Git Commit Message Conventions](#angularjs-git-commit-message-conventions)
  - [커밋 메시지 카탈로그](#커밋-메시지-카탈로그)
    - [FIX](#fix)
      - [Fix A](#fix-a)
      - [Fix A in B](#fix-a-in-b)
      - [Fix A of B](#fix-a-of-b)
      - [Fix A that[which] B](#fix-a-thatwhich-b)
      - [Fix for A](#fix-for-a)
      - [Fix A to V / Fix A for N](#fix-a-to-v--fix-a-for-n)
      - [Fix A so that B](#fix-a-so-that-b)
      - [Fix A where B](#fix-a-where-b)
      - [Fix A when B](#fix-a-when-b)
    - [ADD](#add)
      - [Add A](#add-a)
      - [Add A to B](#add-a-to-b)
      - [Add A for B](#add-a-for-b)
    - [REMOVE](#remove)
      - [Remove A](#remove-a)
      - [Remove A from B](#remove-a-from-b)
      - [Remove A in B](#remove-a-in-b)
      - [Remove A to avoid B](#remove-a-to-avoid-b)
    - [USE](#use)
      - [Use A instead of B](#use-a-instead-of-b)
      - [Use A in B](#use-a-in-b)
      - [Use A for B](#use-a-for-b)
      - [Use A to V](#use-a-to-v)
    - [CHANGE](#change)
      - [Change A to V](#change-a-to-v)
      - [Change A to N](#change-a-to-n)
      - [Change A for N (Replace A with B)](#change-a-for-n-replace-a-with-b)
    - [CONVERT](#convert)
      - [Convert A to B](#convert-a-to-b)
    - [REFACTOR](#refactor)
      - [Refactor A](#refactor-a)
      - [Refactor A for B](#refactor-a-for-b)
    - [SIMPLIFY](#simplify)
      - [Simplify A](#simplify-a)
    - [UPDATE](#update)
      - [Update A](#update-a)
      - [Update to A](#update-to-a)
      - [Update A to N](#update-a-to-n)
      - [Update A to V](#update-a-to-v)
      - [Update A with N](#update-a-with-n)
      - [Update A for B](#update-a-for-b)
    - [IMPROVE](#improve)
      - [Improve A](#improve-a)
    - [MAKE](#make)
      - [Make A B](#make-a-b)
      - [Make it A to V](#make-it-a-to-v)
      - [Make sure to V](#make-sure-to-v)
      - [Make sure (that) A](#make-sure-that-a)
    - [IMPLEMENT](#implement)
      - [Implement A](#implement-a)
      - [Implement A to B](#implement-a-to-b)
    - [REVISE](#revise)
      - [Revise A](#revise-a)
    - [CORRECT](#correct)
      - [Correct A](#correct-a)
    - [ENSURE](#ensure)
      - [Ensure A](#ensure-a)
    - [PREVENT](#prevent)
      - [Prevent A](#prevent-a)
      - [Prevent A from B](#prevent-a-from-b)
    - [AVOID](#avoid)
      - [Avoid A](#avoid-a)
      - [Avoid A to B](#avoid-a-to-b)
      - [Avoid A if/when B](#avoid-a-ifwhen-b)
    - [MOVE](#move)
      - [Move A to/into B](#move-a-tointo-b)
    - [RENAME](#rename)
      - [Rename A to B](#rename-a-to-b)
    - [ALLOW](#allow)
      - [Allow A](#allow-a)
      - [Allow A to V](#allow-a-to-v)
    - [VERIFY](#verify)
      - [Verify A](#verify-a)
    - [SET](#set)
      - [Set A to B](#set-a-to-b)
      - [Set A for B](#set-a-for-b)

## 참고

- [커밋 메시지 GitHub에서 검색하기](https://github.com/search?q=org:google+change+to&type=commits)
- [좋은 git commit 메시지를 위한 영어 사전](https://blog.ull.im/engineering/2019/03/10/logs-on-git.html) - Reid
- [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/) - Chris Beams
  - 번역: [좋은 git 커밋 메시지를 작성하기 위한 8가지 약속](https://djkeh.github.io/articles/How-to-write-a-git-commit-message-kor/)
- [AngularJS Git Commit Message Conventions](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/)
  - [gist](https://gist.github.com/stephenparish/9941e89d80e2bc58a153)
  - [GitHub](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#-commit-message-format)
  - [번역1](http://dogfeet.github.io/articles/2013/angularjs-git-commit-message-conventions.html)
  - [번역2](https://velog.io/@outstandingboy/Git-%EC%BB%A4%EB%B0%8B-%EB%A9%94%EC%8B%9C%EC%A7%80-%EA%B7%9C%EC%95%BD-%EC%A0%95%EB%A6%AC-the-AngularJS-commit-conventions)
- [GitHub 에서 자주 쓰이는 영어 정리해 봤습니다](https://tagilog.tistory.com/588) - 탁이

## 개요

네이밍만큼 어려운 커밋 메시지 작성법을 정리합니다.
그런데 이제 영작문을 곁들인...

### git 커밋 메시지를 잘 쓰려고 노력해야 하는 이유

1. 더 좋은 커밋 로그 가독성
2. 더 나은 협업과 리뷰 프로세스
3. 더 쉬운 코드 유지보수

## 기준 세우기

기준은 사람마다 팀마다 프로젝트마다 다를 수 있다.

- 제목과 본문을 한 줄 띄워 분리하기
  - `git shortlog`
  - `git log --online`
- 제목은 영문 기준 50자 이내로
- 제목은 첫 글자를 대문자로 한 명령문으로
  - Git Built-in Convention과 일관성 유지
    - `Merge branch 'myfeature'`
    - `Merge pull request #123 from someuser/somebranch`
    - `Revert "Add the thing with the stuff"`
  - 명령조가 어색하다면 앞에 `If applied, this commit will`을 붙여본다.
    - (If applied, this commit will) Refactor subsystem X for readability
- 동명사보다 명사를 사용한다.
- 관사(`a`, `an`, `the`)는 사용하지 않는다.
- 제목 끝에 마침표(`.`) 금지
- Github - 제목(이나 본문)에 이슈 번호 붙이기
- 본문은 영문 기준 72자마다 줄 바꾸기
- 본문은 `어떻게`보다 `무엇을`, `왜`에 맞춰 작성하기
- 커밋 메시지로 Github 이슈(issue)를 자동 종료시키기
  - close, closes, closed: 일반 개발 이슈
  - fix, fixes, fixed: 버그 픽스나 핫 픽스 이슈
  - resolve, resolves, resolved: 문의나 요청 사항에 대응한 이슈

### AngularJS Git Commit Message Conventions

```text
<header>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

- header
  - type
    - feat : 새로운 기능 추가
    - fix : 버그 수정
    - docs : 문서 관련
    - style : 스타일 변경 (포매팅 수정, 들여쓰기 추가 등)
    - refactor : 코드 리팩토링
    - test : 테스트 관련 코드
    - ~~chore : 그 외 자잘한 수정~~
      - build : 빌드 관련 파일 수정
      - ci : CI 설정 파일 수정
      - perf : 성능 개선
  - scope
    - 어디가 변경되었는지, 변경된 부분은 모두 들어갈 수 있다.
    - 예를 들어, $location, $browser, $compile, $rootScope, ngHref, ngClick, ngView, 등등
    - scope은 optional 필드
  - subject(short summary)
    - 군더더기 없이 간략하게 현재형으로 적는다: 'changed'나 'changes'가 아니라 'change'로 적는다.
    - 굳이 첫 문자를 대문자로 적지 않는다.
    - 문장 끝에 마침표(.)로 끝내지 않는다.

```text
커밋 메시지 헤더
<type>(<scope>): <short summary>
  │       │             │
  │       │             └─⫸ 명령문, 현재 시제로 작성합니다. 대문자를 사용하지 않으며, 마침표로 끝내지 않습니다.
  │       │
  │       └─⫸ Commit Scope: animations|bazel|benchpress|common|compiler|compiler-cli|core|
  │                          elements|forms|http|language-service|localize|platform-browser|
  │                          platform-browser-dynamic|platform-server|router|service-worker|
  │                          upgrade|zone.js|packaging|changelog|dev-infra|docs-infra|migrations|
  │                          ngcc|ve
  │
  └─⫸ 커밋 유형: build|ci|docs|feat|fix|perf|refactor|test
The <type> and <summary> fields are mandatory, the (<scope>) field is optional.
```

- body
  - subject와 마찬가지로 군더더기 없이 간략하게 현재형으로 적는다: 'changed'나 'changes'가 아니라 'change'로 적는다.
  - 기존과 무엇이 달라졌고 왜 수정했는지에 대한 내용이 들어가야 한다.
- footer
  - 주요 변경 내용(Breaking changes)
  - 주요 변경 내용은 푸터에 언급한다. 무엇을 고쳤는지, 왜 고쳤는지, 마이그레이션은 어떻게 해야 하는지 설명한다.
  - 참조 이슈 (Closes #123, #235)

```text
fix($compile): couple of unit tests for IE9

Older IEs serialize html uppercased, but IE9 does not...
Would be better to expect case insensitive, unfortunately jasmine does
not allow to user regexps for throw expectations.

Closes #392
Breaks foo.bar api, foo.baz should be used instead
```

```text
feat($compile): simplify isolate scope bindings

Changed the isolate scope binding options to:
  - @attr - attribute binding (including interpolation)
  - =model - by-directional model binding
  - &expr - expression execution binding

This change simplifies the terminology as well as
number of choices available to the developer. It
also supports local name aliasing from the parent.

BREAKING CHANGE: isolate scope bindings definition has changed and
the inject option for the directive controller injection was removed.

To migrate the code follow the example below:

Before:

scope: {
  myAttr: 'attribute',
  myBind: 'bind',
  myExpression: 'expression',
  myEval: 'evaluate',
  myAccessor: 'accessor'
}

After:

scope: {
  myAttr: '@',
  myBind: '@',
  myExpression: '&',
  // myEval - usually not useful, but in cases where the expression is assignable, you can use '='
  myAccessor: '=' // in directive's template change myAccessor() to myAccessor
}

The removed `inject` wasn't generaly useful for directives so there should be no code using it.
```

## 커밋 메시지 카탈로그

### FIX

#### Fix A

> A를 교정한다

```text
Fix stat cache
Fix changelog entry
Fix broken jsiexecutor search path
```

#### Fix A in B

> B에 있는 A를 교정한다

```text
Fix typo in docs
Fix calculation in process.uptime()
Fix build warning in node_report.cc
Fix error condition in Verify::VerifyFinal
Fix typo in callback.cc
Fix duplicate symbols linker error in xcodeproj
```

#### Fix A of B

> B의 A를 교정한다

```text
Fix location of favicon
```

#### Fix A that[which] B

> B절인 A를 교정한다

```text
Fix crash that happens when a component throws an exception that contains a null message
Fix incorrect type which makes animated gifs not loop forever on device
```

#### Fix for A

> A에 대해 교정한다

```git
Fix for #4183
```

#### Fix A to V / Fix A for N

> V하기 위해 A를 수정한다

```text
Fix inability to remove 'Disabled' state from AccessibilityStates
Fix HTTP connection timeout callback to be appropriately called
```

#### Fix A so that B

> A를 수정해서 B가 되도록 한다

`Fix A to B`와 의미는 비슷하지만 고쳐진 B의 상태를 보다 강조한다.

```markup
Fix react-native init --help so that it doesn't return undefined
Fix Android 28's inverted ScrollView so that momentum is in the proper direction
```

#### Fix A where B

> B처럼 발생하는 A를 수정한다

A는 보통 'issue', 'error', 'crash' 등이 들어간다.
B는 문제가 발생한 모습을 적어주면 된다.

```commit
Fix case where content of inline views didn't get relaid out
Fix case where inline view is visible even though it should have been truncated
Fix issue where Image.resizeMode isn't respected while source is loading, resulting in unexpected padding
```

#### Fix A when B

B일 때 발생하는 A를 수정한다

A는 보통 'issue', 'error', 'crash' 등이 들어간다.
B는 문제가 발생하는 상황을 적어주면 된다.

```bash
Fix accidental showing of Modal when visible prop is undefined or null
Fix crash when removing root nodes
```

### ADD

#### Add A

> A를 추가한다

추가하는 행위는 대부분 목표나 목적이 명시되기 때문에 이 패턴은 자주 사용되지 않는다.

```text
Add null check
Add ERR_INSPECTOR_COMMAND error
Add Windows Support
Add suppor for callback
```

#### Add A to B

> B에 A를 추가한다

```text
Add `.js` to import
Add error description to Image onError callback
Add displayName to ActivityIndicator
Add deprecation notice to SwipeableListView
```

#### Add A for B

> B를 위해 A를 추가한다

```text
Add test for bug #3116
Add documentation for the defaultPort option
Add example for setting Vary: Accept-Encoding header in zlib.md
Add missing includes for vtune build
Add test for dynamically enabling node.async_hooks tracing
Add test for InterpolatorType
Add devDependencies support for templates
```

### REMOVE

#### Remove A

> A를 제거한다

```text
Remove deprecated methods
Remove fallback cache
Remove unnecessary italics from child_process.md
Remove useless additionnal blur call
Remove unneeded .gitignore entries
Remove unused variable
Remove duplicated buffer negative allocation test
Remove use of the deprecated method
```

#### Remove A from B

> B에서 A를 제거한다

```text
Remove debug from tests
Remove absolute path parameter from transformers
Remove trailing slash from origin header if no port is specified
```

#### Remove A in B

> B에 있는 A를 제거한다

```text
Remove duplication in render function
```

#### Remove A to avoid B

> B를 피하기 위해 A를 제거한다

```text
Remove methods to avoid warnings
```

### USE

특별히 무언가를 사용해 구현을 하는 경우

#### Use A instead of B

> B 대신 A를 사용한다

```text
Use `++` instead of `+= 1`
Use babel runtime instead of relying on global babelHelpers and regenerator
```

#### Use A in B

> B에서 A를 사용한다

```text
Use stub in testing
Use smart pointer in UDPWrap::OnSend
Use same parameter name in node_report.cc
Use TextLegend example in Android as well
Use main.jsbundle in iOS template for production build
Use new Metro configuration in react-native cli
```

#### Use A for B

> B에 A를 사용한다

```text
Use Ruby for mocking
Use fake MessageEvent for port.onmessage
Use object writer for thrown errors
Use ru_stime for system CPU calculation
Use relative path for SCRIPTDIR
```

#### Use A to V

> V하도록 A를 사용한다

```text
use common operations to define browser globals
use triggerReport() to handle signals
use PauseOnNextJavascriptStatement to implement --inspect-brk-node
```

### CHANGE

#### Change A to V

> V하기 위해 A를 수정한다

```text
Change syntax to use dots
```

#### Change A to N

> A를 N으로 수정한다

```text
Change water to wine
```

#### Change A for N (Replace A with B)

> A를 N으로 대체한다

```text
Change my red shirt for a white one
```

### CONVERT

#### Convert A to B

> A를 B로 변환한다

```text
Convert time to string
```

### REFACTOR

#### Refactor A

> A를 리팩터링한다

```text
Refactor tick objects prune function
Refactor thread life cycle management
Refactor QueryWrap lifetime management
Refactor argument validation
Refactor thread life cycle management
Refactor MockNativeMethods in Jest
```

#### Refactor A for B

> B를 위해 A를 리팩터링한다

```text
Refactor subsystem X for readability
```

### SIMPLIFY

#### Simplify A

> A를 단순화한다

```text
Simplify code and remove obsolete checks
Simplify the setup of async hooks trace events
Simplify heap space iteration
Simplify TriggerNodeReport()
Simplify AliasedBuffer lifetime management
Simplify loop arithmetic in GetCPUInfo
```

### UPDATE

코드보다는 주로 문서나 리소스, 라이브러리 등에 사용한다.

#### Update A

> A를 업데이트한다

```text
Update getting started documentation
```

#### Update to A

> A로 업데이트한다

```text
Update to a new version
```

#### Update A to N

> A를 N으로 업데이트한다

```text
Update kubectl to v1.21
```

#### Update A to V

> A를 V하기 위해 업데이트한다

```text
Update react-devtools-core and plist to include security fixes reported by npm audit
Update RCTLinkingManager.h to explicitly state the 'nullability' of parameters
Update repo docs to use HTTPS
Update app icons to match recent Android releases
```

#### Update A with N

> N을 위해 A를 업데이트한다

```text
Update babelHelpers with Babel 7 support
```

#### Update A for B

> B를 위해 A를 업데이트한다

```text
Update `README.md` for #1563
```

### IMPROVE

#### Improve A

> A를 향상시킨다

```text
Improve compatibility with http/1
Improve Unicode handling
Improve test coverage in perf_hooks
Improve validation of report output
Improve performance of test-crypto-timing-safe-equal-benchmarks
Improve color detection
Improve Android Network Security config
Improve Accessibility
Improve iOS's accessibilityLabel performance by up to 20%
```

### MAKE

주로 기존 동작의 변경을 명시한다

#### Make A B

> A를 B하게 만든다

```text
Make config object read-only
Make 'floating patch' message informational
Make values optional in ViewPropTypes
Make read() be called indefinitely if the user wants so
Make IsolateData store ArrayBufferAllocator
```

#### Make it A to V

> V하기를 A하게 한다

```text
Make it easy to check platform requirements in a command
```

#### Make sure to V

> 반드시 V하도록 한다

```text
Make sure to reset default_url_options
```

#### Make sure (that) A

> 반드시 A하도록 한다

```text
Make sure all packages rebuild
```

### IMPLEMENT

'Add'에 비해 더 큰 단위의 코드 추가에 사용되며, 특히 모듈이나 클래스 등의 단위에 사용된다.
따라서 목적을 명시해주지 않아도 되는 경우가 많다.

#### Implement A

> A를 구현한다

```text
Implement date object
Implement Image.defaultSource
Implement bundle sync status
```

#### Implement A to B

> B를 위해 A를 구현한다

```text
Implement requiresMainQueueSetup in RCTTVNavigationEventEmitter to satisfy Xcode warning
Implement an in-memory cache store to save parsed and validated documents and provide performance benefits for repeat executions of the same document
```

### REVISE

Update와 비슷하나 문서의 개정이 있을 때 주로 사용한다.

#### Revise A

> A 문서를 개정한다

```text
Revise deprecation semverness info in Collaborator Guide
```

### CORRECT

#### Correct A

> A를 교정한다

```text
Correct grammatical error in BUILDING.md
Correct parameters, return types in crypto.md
Correct styling of _GitHub_ in onboarding doc
Correct buffer changelog ordering
Correct async_hooks resource names
```

### ENSURE

무엇이 확실하게 보장받는다는 것을 명시한다.
if 구문처럼 조건을 확실하게 주었을 때에도 사용될 수 있다.
'Make sure'도 같은 용도로 사용될 수 있다.

#### Ensure A

> A가 확실히 보장되도록 수정한다

```text
Ensure quiet always takes precedence
Ensure cookies with illegal characters are not sent to okhttp
Ensure require.main for CJS top-level loads
Ensure Stream.pipeline re-throws errors without callback
Ensure options.flag defaults to 'r' in readFile
```

### PREVENT

#### Prevent A

> A하지 못하게 막는다

```text
Prevent multiple connection errors
Prevent constructing console methods
Prevent event loop blocking
Prevent a potential error in event handling if Object.prototype is extended.
Prevent an infinite loop when attempting to render portals with SSR.
```

#### Prevent A from B

> A를 B하지 못하게 막는다

```text
Prevent event handlers from receiving extra argument in development.
```

### AVOID

'Prevent'’는 못하게 막지만, 'Avoid'는 회피한다.
if 구문으로 특정한 동작을 제외시키는 경우에도 사용할 수 있다.

#### Avoid A

> A를 회피한다

```text
Avoid flusing uninitialized traces
Avoid overrun on UCS-2 string write
Avoid race condition in OnHeaderCallback
Avoid memory leak on gc observer
Avoid materializing ArrayBuffer for creation
```

#### Avoid A to B

> B하기 위해 A를 회피한다

```text
Avoid method call to compact
```

#### Avoid A if/when B

> B인 상황에서 A를 회피한다

```text
Avoid importing entire crypto dependency tree if not in Node.js
Avoid "Member not found" exception in IE10 when calling preventDefault() in Synthetic Events
Avoid input validation warning from browsers when changing type
Avoid double reload event when reloading JS
```

### MOVE

코드의 이동이 있을 때 사용한다.

#### Move A to/into B

> A를 B로 옮긴다

```text
Move strings to strings.js
Move test-process-uptime to parallel
Move function from header to source file
Move async hooks trace events setup to pre_execution.js
move initialization of node-report into pre_execution.js
```

### RENAME

#### Rename A to B

> A 이름을 B로 수정한다

```text
Rename parser to converter
```

### ALLOW

Make와 비슷하지만, 허용을 표현할 때 사용한다.

#### Allow A

> A하는 것을 허용한다

```text
Allow passing parseOptions to ApolloServerBase constructor
```

#### Allow A to V

> A가 V하는 것을 허용한다

```text
Allow the use to drag faster
Allow the output filename to be a {Function}
Allow Node.js-like runtimes to identify as Node.js as well
Allow an optional function to resolve the rootValue, passing the DocumentNode AST to determine the value
```

### VERIFY

검증 코드를 넣을 때 주로 사용한다.

#### Verify A

> A를 검증한다

```text
Verify heap buffer allocations occur
```

### SET

변수 값을 변경하는 등의 작은 수정에 주로 사용한다.

#### Set A to B

> A를 B로 설정한다

```text
Set default kernel to Gaussian
set tls.DEFAULT_ECDH_CURVE to 'auto'
```

#### Set A for B

> B에 대한 A를 설정한다

```text
Set release date for 0.10.1
```
