# Component

## 키워드

- SRP(단일 책임 원칙)
- Atomic Design
- SSOT(Single Source of Truth)

### SRP

- 컴포넌트를 생성할 때 단일 책임 원칙을 지킬 것을 유념하자.
- 하나의 컴포넌트가 다양한 일을 한다면 재사용성이 떨어지고 테스트하기 어려워진다.
- 디자인적 관점에서 SRP를 바라볼 수도 있다. 대표적인 패턴이 아토믹 패턴
- 데이터 관점에서 SRP를 바라볼 수도 있다. Information Architecture로 JSON Schema의 영향을 받았다.

### Atomic Design

1. Atom

- 아톰은 가장 아래 계층에 위치하며, 버튼/텍스트 등 더 이상 분할할 수 없는 컴포넌트를 구현한다.
- 크기, 문장, 색상과 같은 요소들까지 부모로부터 제어 받는다.

2. Molecules

- 라벨이 붙은 텍스트 박스와 같이 아톰 여러 개를 조합해서 구축한 UI 컴포넌트이다.
- 몰리큘 역시 아톰과 같이 상태나 동작을 갖지 않으며, 필요한 데이터는 부모로부터 제어 받는다.
- 몰리큘은 단일한 역할을 갖는 UI만을 구현한다.

3. Organisms

- 등록 폼, 헤더와 같이 보다 구체적인 UI 컴포넌트를 구현한다.
- 도메인 지식에 의존한 데이터를 받거나, 독자적인 작동을 가질 . 수있다.
- 다만 오거니즘부터는 프레젠테이션 컴포넌트와 컨테이너 컴포넌트를 구분해서 구현한다. (여기서 알 수 있는 것은 한 계층에서도 여러 컴포넌트로 구현될 수 있다는 점이다.)

4. Templates

- 전체 레이아웃을 구현한다.
- 오거니즘 컴포넌트를 가져와 배치하고 css로 각 컴포넌트의 레이아웃을 조정한다.

5. Page

- 최상위 컴포넌트로 페이지 단위의 UI 컴포넌트를 구현한다.
- 레이아웃은 템플릿에서 하고 여기서는 상태 관리, 라우터 처리, API 호출 등의 사이드 이펙트를 처리한다.

### SSOT(Single Source of Truth)

- 모든 비즈니스 데이터는 하나의 공간에 저장되어야 한다.
- React로 이야기하면 트리 구조에서 최상위 컴포넌트에서 비즈니스 데이터를 가지고 props로 전달해줘야 한다고 얘기할 수 있겠다.