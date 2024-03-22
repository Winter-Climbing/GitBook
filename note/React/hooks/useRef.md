# useRef

## 👀 useRef란?

useState와 비슷하나 렌더링에 필요하지 않은 값을 참조할 수 있는 훅이다. useState와 비슷하게 변경된 상태는 추적하되 렌더링을 일으키지 않는다.

<br>

## 🌈 특징

- useRef는 반환값인 객체 내부에 있는 current로 값에 접근 또는 변경할 수 있다.
- useRef는 그 값이 변하더라도 렌더링을 발생시키지 않는다.

<br>

## 🎯 잘 사용하는 방법

usePrevious hook을 구현해보자

```typescript
function usePrevious(value) {
  const ref = useRef();
  useEffect(() => {
    ref.current = value;
  }, [value]);
  return ref.current;
}

function SomeComponent() {
  const [counter, setCounter] = useState(0);
  const previousCounter = usePrevious(counter);

  function handleClick() {
    setCopunter((prev) => prev + 1);
  }

  // 0
  // 0, 1
  // 2, 1
  // 3, 2
  return (
    <button onClick={handleClick}>
      {counter} {previousCounter}
    </button>
  );
}
```

<br>

## 💩 주의할 점

1. useRef 최초 기본값은 초기값을 설정하지 않을 경우, DOM이 아닌 useRef()로 넘겨받은 인수이다. 따라서 useRef가 선언 된 당시에는 아직 컴포넌트가 렌더링 되기 전이라 return으로 컴포넌트의 DOM이 반환되기 전이므로 undefined다.

## 출처

- [리액트 공식문서](https://ko.react.dev/reference/react/useRef)
- [모던 리액트 Deep Dive](https://m.yes24.com/Goods/Detail/123161563)
