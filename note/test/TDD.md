# TDD

## 👀 TDD란?

TDD란 Test-Driven development의 약자로 개발 전 테스트 코드를 먼저 작성하면서 어플리케이션을 작성해나가는 개발 과정을 뜻한다. 구현하기 전 테스트 코드를 먼저 작성하고 (이 때 가벼운 수준의 테스트 코드만 작성한다.) 코드가 다 정상 작동하면 다시 실제 구현 코드를 작성한다.

## ⌛️ 왜 생겨났는가?

요구 사항을 올바르게 이해했는지 분석하고 이해하는데 도움이 되고, 나아가 이를 바탕으로 전체적인 코드를 설계하는데 도움이 되기 때문이다. 즉, 테스트 코드를 작성하는 과정에서 모든 요구 사항에 대해 점검할 수 있고, 구현이 아닌 인터페이스 기반의 코드를 작성할 수 있다.

<br>

## 🌈 장점

1. 좋은 문서화

테스트 코드를 작성할 경우, 해당 코드가 어떤 역할을 하는지 쉽게 파악할 수 있다.

2. 코드 품질 향상

테스트 코드가 존재할 경우, 리팩터링을 진행하기 쉬워지고 요구사항을 명확하게 반영해서 코드를 작성할 수 있다.

<br>

## 🎯 TDD 방법

1. 순서

테스트를 작성한다 -> 실패를 체크한다 -> 통과했을 경우 -> 리팩터링을 진행하고 다시 테스트를 진행한다

2. 언제 테스트 코드를 작성하는게 좋을까

- 요규사항이 명확할 때
- 비니지스 로직일 때
- 협업시 명세서 역할이 필요할 때
- 설계에 대한 고민이 필요할 때

<br>

## 💩 주의할 점

1. Merge 할 때 테스트 코드는 같이 포함되어야 한다.

이를 통해 내가 작성한 코드에는 버그가 없다는 것을 팀원들에게 알려야 한다.

2. 테스트 커버리지에 매몰되지 말자.

모든 코드를 다 테스트 할 필요는 없다. UI 같은 경우 안 하는 경우도 많다.

## 출처

- [실무에 바로 적용하는 프런트엔드 테스트](https://www.inflearn.com/course/lecture?courseSlug=%EC%8B%A4%EB%AC%B4%EC%A0%81%EC%9A%A9-%ED%94%84%EB%9F%B0%ED%8A%B8%EC%97%94%EB%93%9C-%ED%85%8C%EC%8A%A4%ED%8A%B8-1%EB%B6%80&unitId=183253)
- [이혜승 - 테알못 신입은 어떻게 테스트를 시작했을까?](https://www.slideshare.net/OKJSP/okkycon-120498066)