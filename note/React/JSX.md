# JSX

JSX란 JavaScript를 확장한 문법이다. UI가 어떻게 생겨야 하는지 설명하기 위해 React와 함께 사용된다. (Vue나 Solid 등에서도 사용되긴 한다.)

## 예시

JSX가 무엇을, 어떻게 추상화 했는지 간단한 코드 예시들

```typescript
React.createElement(태그, property, value);
```

### Example #1

```typescript
<p>Hello, World</p>;

// 바벨 (or SWC) 변환

React.createElemnt('p', null, 'Hello, World');
```

### Example #2

속성은 객체로 변환되는 것을 보여준다.

```typescript
<Greeting name='world' />;

// 바벨 (or SWC) 변환

React.createElement(Greeting, { name: 'world' });
```

### Example #3

```typescript
<Button type='submit'>Send</Button>;

// 바벨 (or SWC) 변환

React.createElement(Button, { type: 'submit' }, 'Send');
```

### Example #4

```typescript
<div className='test'>
  <p>Hello, world!</p>
  <Button type='submit'>Send</Button>
</div>;

// 바벨 (or SWC) 변환

React.createElement(
  'div',
  { className: 'test' },
  React.createElement('p', null, 'Hello, world!'),
  React.createElement(Button, { type: 'submit' }, 'Send')
);
```

### Example #5

```typescript
<div>
  <p>Count: {count}!</p>
  <button type='button' onClick={() => setCount(count + 1)}>
    Increase
  </button>
</div>;

// 바벨 (or SWC) 변환

React.createElement(
  'div',
  null,
  React.createElement('p', null, 'Count: ', count, '!'),
  React.createElement(
    'button',
    { type: 'button', onClick: () => setCount(count + 1) },
    'Increase'
  )
);
```
