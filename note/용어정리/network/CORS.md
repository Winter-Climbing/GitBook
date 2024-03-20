# CORS

## 👀 CORS란?

CORS는 교차 출처 리소스 공유 (Cross-Origin Resource Sharing)의 약자로, 웹 브라우저에서 다른 도메인의 리소스에 대한 접근을 허용하는 메커니즘이다.

## ⌛️ 왜 생겨났는가?

태초의 웹은 동일 출처 정책(Same-Origin Policy)으로 같은 도메인에서만 리소스 접근을 허용했었다. 하지만 웹의 비약적인 발전과 함께 서로 다른 도메인 간의 리소스 공유가 필수적이게 되면서 등장하게 되었다.

## 🌈 특징

CORS가 필요하다는 것을 명시해야 되기 때문에 server에서 client에 데이터를 보낼 때 header에 Access-Control-Allow-Origin를 추가해줘야 한다.

## 💩 주의할 점

CORS는 브라우저에서만 거부한다는 것을 잊지 말자!!! 브라우저에서는 에러가 나도 서버끼리의 통신에서는 아무 문제 없는 게 정상이다.

위의 방법을 이용해 다른 도메인 리소스를 접근할 때 브라우저에서 접근하는 것이 불가능하다면 프록시 서버를 만들어 해당 리소스에 접근할 수 있다. 이 때, 프록시 서버로 사용할 서버가 없다면 다양한 도구를 이용해서 해결하자 (webpack-dev-server 등등)

> 브라우저 -> 같은 origin서버 (프록시 서버) -> 다른 origin 서버

## 출처

- [MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)
- [CORS는 왜 이렇게 우리를 힘들게 할까?](https://evan-moon.github.io/2020/05/21/about-cors/)
- [비전공자의 전공자 따라잡기 - 네트워크, HTTP](https://www.inflearn.com/course/%EC%A0%84%EA%B3%B5%EC%9E%90-%EB%94%B0%EB%9D%BC%EC%9E%A1%EA%B8%B0-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-http)
