# REST

## 👀 REST란?

REpresentational State Transfer의 약자로 HTTP URI를 통해 자원을 명시하고, HTTP Method를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것을 뜻한다. 따라서 간단히 말하면 Web Service API를 작성할 때 지키면 좋은 일종의 가이드라인이다.

## ⌛️ 왜 생겨났는가?

2000년경 http를 기반으로 하는 웹 서비스가 전 세계적으로 발전하면서 네트워크 통신을 어떻게 효율적으로 관리할 수 있을까라는 생각하에 만들어졌다. (Roy Fielding)

## 🌈 특징

### RESTFUl 6 guiding constraints

1. Client-server architecture

- rest api는 클라이언트 단에 데이터를 제공할 수 있어야 한다.

2. Statelessness

- 하나의 요청이 또 다른 요청을 불러오는 것이 아닌, stateless한 상태여야 한다.
- http protocol에서 해당 기능을 제공한다.

3. Cacheability

- 캐시 기능이 제공될 수 있어야 한다.
- http protocol에서 해당 기능을 제공한다.

4. Layered System

- 실제 서버의 개수와는 상관 없이 하나의 데이터 센터에서 api를 다 가져올 수 있어야 한다.

5. code on demand

- 클라이언트에서 필요하다면 서버에서 코드를 넘겨줄 수 있어야 한다.
- 필수사항은 아니다.

6. Uniform interface

- 이것으로 Restful 하냐 안 하냐가 결정된다.
- 데이터는 성격에 맞게 식별될 수 있어야 하며, 서버에 저장되어 있는 데이터가 어떤 형태로 저장되어 있든지 클라이언트가 이해할 수 있는 데이터 포멧으로 전달되어져야 한다.
- 서버에서 받은 데이터를 어떻게 crud할 수 있는지 예측되어져야 한다.
- 클라이언트가 서버에서 데이터를 받았을 때 데이터 타입을 바로 식별할 수 있어야 한다.
- 클라이언트가 자원을 서버에서 받았을 경우, 해당 url에서 어떻게 관련 자원들을 사용할 수 있는지 제공되어져야 한다. (근데 많은 곳에서 이렇게까지는 하지 않는다)

## 🎯 사용 방법

## 출처

> [IBM](https://www.ibm.com/kr-ko/topics/rest-apis)
