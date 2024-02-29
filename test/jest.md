# Jest

### Jest?

- Facebook에서 개발한 JS 테스팅 프레임워크다.

### 기본 사용 방법

```typescript
function add(x: number, y: number): number {
  return x + y;
}

// context를 사용하여 표현력을 높인다.
const context = describe;

describe('add 함수는', () => {
  it('두 숫자의 합을 리턴한다.', () => {
    expect(add(1, 2)).toBe(3);
  });

  it('숫자를 리턴한다.', () => {
    expect(typeof add(1, 2)).toBe('number');
  });

  context('하나의 양수와 음수가 주어지면', () => {
    it('항상 하나의 양수보다 작은 값을 돌려준다.', () => {
      expect(add(1, -2)).toBeLessThan(1);
    });
  });
});
```

1. 검사할 함수 add를 작성한다.
2. add 함수를 다양한 방식으로 테스트할 describe를 선언한다. 이 때 첫 번째 인자는 설명을, 두 번째 인자는 실행할 함수들을 작성한다.
3. it을 선언한다. 이 때 첫 번째 인자는 설명을, 두 번째 인자는 테스트할 로직을 작성한다.
4. expect는 실제 예상되는 결과값이 작성된다.
5. 다양한 Jest 메서드를 활용하여 원하는 결과값을 테스트한다.
6. 원한다면 위에서 사용된 바와 같이 context를 추가하여 단락을 나눠 가시성을 높일 수 있다.
