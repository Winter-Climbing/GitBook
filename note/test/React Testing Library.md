# React Testing library

### Why?

- 테스트 코드가 작동되는 nodejs에는 DOM이 없다. 이를 위해 논리적 형태의 DOM이 필요하고 이를 수행하는 라이브러리다.

### 언제 테스트 코드를 작성하는 것이 좋을까?

- 되도록이면 only React 컴포넌트 테스트가 되는 상황은 피하는 것이 좋다.
- 테스트 코드의 본질은 유지보수를 용이하게 위함인데 테스트 코드를 위한 주객전도가 벌어지기 쉽기 때문이다.
- 따라서 상태에 신경쓰는 것이 좋다. (무엇을 기준으로 하느냐에 대한 고민이 더 중요하다)

### 기본 사용 방법

```typescript
import { render, screen } from '@testing-library/react';
import Greeting from './Greeting';

test('Greeting', () => {
  render(<Greeting name='world' />);

  screen.getByText('Hello, world');

  screen.getByText(/Hello/);

  expect(screen.queryByText(/Hello/)).toBeInTheDocument();

  expect(screen.queryByText(/Hi/)).not.toBeVisible();
});
```

- Jest와 비슷한 형태다. 다만 DOM을 조작하다 보니 다른 메서드들을 사용한다.
