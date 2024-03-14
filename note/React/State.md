# State

## 키워드

- React의 State
- useState와 비동기

### React의 State

- DRY와 SSOT를 지킬 것!
- State는 변경을 다루기 위한 요소다. 따라서 상태 변경 이후의 불필요한 re-rendering을 최소화하기 위해서라도 중복된 State가 다루어져선 안 된다.

#### 파생상태

- 다른 state나 props의 상태 변화에 파생되어진 상태는 state로 다루지 않는다.
- 해당 state는 JS 코드로 작성하여 불필요한 re-rendering을 안 일으키도록 한다.

### useState와 비동기

- state의 변경은 setState로만 이루어진다. 왜냐하면 state의 변경은 컴포넌트가 re-rendering 될 때까지 state를 갱신하지 않기 때문이다.
- setState는 state의 변경을 감지하고 state를 변경을 위해 re-rendering을 일으킨다.
- state, props, refs는 내부적으로 완전히 조정된 트리를 참조하도록 보장되어 있다. 즉, setState가 여러 번 호출되었다면 해당 호출이 다 이뤄지고 난 뒤 업데이트가 실시된다.

### 참고

아이템 목록에서 key가 value인 것만 선택하기

```typescript
function select<ItemType, ValueType>(
  items: ItemType[],
  key: keyof ItemType,
  value: ValueType
) {
  return items.filter((item) => item[key] === value);
}
```
