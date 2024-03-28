# useEffect

## 👀 useEffect란?

useEffect는 기존의 상식과는 달리 생명주기 메서드를 대체하기 위해 만들어진 훅이 아니라, 컴포넌트들의 여러 값들을 활용해 동기적으로 부수 효과를 만드는 hook이다. 따라서 부수 효과가 '언제' 일어나는지에 집중할 것이 아니라 어떤 '상태값'과 함께 실행되는지 살펴보는 것이 중요하다.

<br>

## 🌈 특징

1. useEffect 안과 밖은 어떤 차이가 있을까?

```typescript
// 1
function Component() {
  console.log(1);
}

// 2
function Component() {
  useEffect(() => {
    console.log(1);
  });
}
```

- SSR을 기준으로 1번은 계속해서 실행된다. 하지만 2번은 CSR에서 실행되는 것을 보장한다.
- useEffect는 렌더링의 부수효과다!! 즉, 컴포넌트 렌더링이 완료된 이후 실행된다. 하지만 1번은 렌더링 작업 도중에 실행되고 이는 컴포넌트 반환 작업을 느리게 할 수 있다.

<br>

2. 클린업 함수

클린업 함수는 언마운트라기보다 컴포넌트가 리렌더링 됐을 때 의존성 변화가 있었을 당시 이전의 값을 청소해 주는 개념으로 보는 것이 맞다. 정확히 얘기하면 컴포넌트가 랜더링 안에 있는 모든 함수는 (이벤트 핸들러, 이펙트, 타임아웃이나 그 안에서 호출되는 API 등) 랜더가 호출될 때 정의된 props와 state 값을 잡아둔다.

예시)

```typescript
useEffect(() => {
  ChatAPI.subscribeToFriendStatus(props.id, handleStatusChange);
  return () => {
    ChatAPI.unsubscribeFromFriendStatus(props.id, handleStatusChange);
  };
});
```

첫 번째 랜더링에서 prop 이 {id: 10} 이고, 두 번째 랜더링에서 {id: 20} 이라고 하자.

- 리액트가 {id: 20} 을 가지고 UI를 랜더링한다.
- 브라우저가 실제 그리기를 한다. 화면 상에서 {id: 20} 이 반영된 UI를 볼 수 있다.
- 리액트는 {id: 10} 에 대한 이펙트를 클린업한다.
- 리액트가 {id: 20} 에 대한 이펙트를 실행한다.

<br>

## 🎯 잘 사용하는 방법

1. 익명 함수를 경우에 따라 잘 작명하자

```typescript
// 익명 함수
useEffect(() => {
  logging(user.id)
}, [user.id])

// 함수명을 써서 좀 더 명료해졌다.
useEffect(
  function logActiveUser () {
    logging(user.id)
  }.
  [user.id]
)
```

2. 데이터 페칭하기 (주의할 점 4번과 연결)

```typescript
useEffect(() => {
  let ignore = false;

  async function startFetching() {
    const json = await fetchTodos(userId);
    if (!ignore) {
      setTodos(json);
    }
  }

  startFetching();

  return () => {
    ignore = true;
  };
}, [userId]);
```

더 이상 관련이 없는 페치가 애플리케이션에 계속 영향을 끼치지 않도록 해야 한다. 따라서 클린업 함수를 통해서 해결해줘야 한다. 참고로 개발 환경에서는 네트워크 탭에 두 개의 페치가 표시되나 신경 꺼도 된다. 상용 환경에서는 하나만 있을 것이다.

<br>

## 💩 주의할 점

1. eslint-disable-line react-hooks/exhaustive-deps 주석은 최대한 자제해라

간단하게 말해 의존성 배열에 []을 되도록 사용하지 말라는 말이다. 만약 useEffect 안에서 변경되는 상태가 계속해서 변경된다면 해당 상태는 반영되지 않을 것이다. 즉, 데이터 흐름이 단절될 수 있다는 것이다. 따라서 []을 사용할 때는 정말로 useEffect의 부수 효과가 컴포넌트의 상태와 별개로 작동해야만 하는지, 혹은 여기서 호출하는 게 최선인지 한 번 더 검토해봐야 한다.

2. 거대한 useEffect를 만들지 마라

useEffect가 거대해져 부수 효과의 크기가 커질수록 어플리케이션의 성능을 안 좋아질 수 있다. 만약 부득이한 사정이 있다면 적은 의존성 배열을 사용하는 useEffect로 분리하자. 성능도 문제지만 useEffect 타이밍을 알 수 없다는 것도 문제다.

3. 불필요한 외부 함수를 만들지 마라

useEffect 내부에서 사용할 부수 효과라면 내부에서 만들어 정의하는 것이 훨씬 낫다.

4. 경쟁 상태 (race condition)

useEffect 인수로 받는 함수를 비동기 함수로 작성할 경우, 내부에 있는 비동기 상태 관련 코드들 사이에서 응답 속도에 관한 문제들이 발생할 수 있다. 따라서 인수 자체를 비동기 함수로 작성하는 것이 아니라 내부에서 비동기 관련 코드들을 작성하면 별 문제가 없을 것이다. 클린업 함수를 통해 비동기 함수의 반복을 막기만 한다면 말이다.

```typescript
useEffect(() => {
  let shouldIgnore = false;

  async function fetchData() {
    const response = await fetch('');
    const result = await response.json();
    if (!shouldIgnore) {
      setData(result);
    }
  }

  fetchData();

  return () => {
    shouldIgnore = true;
  };
}, []);
```

## 출처

- [리액트 공식문서](https://react-ko.dev/learn/synchronizing-with-effects)
- [useEffect 완벽 가이드](https://overreacted.io/a-complete-guide-to-useeffect/)
- [모던 리액트 Deep Dive](https://m.yes24.com/Goods/Detail/123161563)
