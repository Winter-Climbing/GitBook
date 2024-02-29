# Type vs Interface

### 잠정적 결론은 type을 사용할 것

- 이름에서 type과 interface는 차이가 있다. type은 타입 지정만을 위한 도구로 보이는 반면, interface는 이름에서 보이듯 그 이후의 동작이 있을 것으로 판단된다. 따라서 interface는 상태와 동작이 묶여 있는 경우와 같은 특수한 상황에서 사용하는 것이 옳다고 생각한다.
- 유틸리티 타입을 사용할 경우 type이 더 간결하게 표현된다.
- 튜플 또한 type이 더 간결하다.
- interface는 선언 병합을 통해 타입에 대한 혼란이 야기될 수 있다.

### 기본적인 차이점

1. type은 객체 형태를 제외한 나머지 타입도 지정이 가능한 반면, interface는 객체 형태의 타입만 지정 가능
2. 타입을 확장할 경우 type은 &를, interface는 extends를 사용한다.
3. interface의 경우 똑같은 이름의 interface를 작성한 후 해당 객체의 키값 타입을 바로 확장할 수 있다. - 이러한 속성을 '선언 병합'이라고 한다.
4. 밑의 예시 참조

```typescript
// type의 경우 동일한 이름의 함수 타입을 변경하고 이를 이용해 코드를 작성할 수 있다.
type Test = {
  id: number
  getPermission : (id: string) => string;
};

type PlusTest = Test & {
  permissions: string[]
  getPermission : (id: string[]) : string[]
}

const testObject: PlusTest = {
  getPermission(id: string | string[]) => {
    return (typeof id === 'string' ? id : [id]) as string[] & string;
  }
}

// interface의 경우 동일한 이름의 함수의 타입들을 변경할 수 없다!
```

### 무엇을 사용할까?

1. 핸드북

- typescript 핸드북에는 인터페이스를 쓰되 type이 필요한 경우에만 type을 쓰라고 명시되어 있다. 이유는 안 적혀 있다.

[핸드북](https://www.typescriptlang.org/ko/docs/handbook/2/everyday-types.html#%ED%83%80%EC%9E%85-%EB%B3%84%EC%B9%AD%EA%B3%BC-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90)

2. Maximilian

- class의 경우 interface가 맞다.
- 오픈 소스의 경우 선언 병합의 특징을 가지고 있는 interface가 사용하기 쉽다. (타입 추가가 쉽기 때문)

[React & TypeScript - The Practical Guide](https://www.udemy.com/course/react-typescript-the-practical-guide/?couponCode=ST22FS22724)
