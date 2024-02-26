# 개발환경

### 학습 키워드

- Node.js
- NPM(Node Package Manager)
  - package.json / package-lock.json
  - node_modules
  - npx
- ES Modules vs CommonJS

### npm 패키지

- npx는 node_module .bin 폴더에 설치되어 있는 파일들을 실행시키는 명령어다.

- fnm (Fast Node Manager)

  - fnm은 노드 버전 관리 도구이다.
  - nvm을 사용하지 않는 이유는 더 빠르고 경량화되어 있기 때문이다.

- package.json
  - 현 프로잭트에 관한 정보 및 모듈들의 의존성을 관리하는 파일

```typescript
# package.json

{
  "name": "react-demo", // 프로젝트 이름 (케밥케이스 주로 사용)
  "version": "0.0.0",
  "description": "React Application Demo",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  }, // 에러 메시지 작성
  "keywords": [],
  "author": "Koo",
  "license": "ISC"
}

```

### .gitignore

- [gitignore 파일 생성 주소](https://www.toptal.com/developers/gitignore)
- [github node gitignore](https://github.com/github/gitignore/blob/main/Node.gitignore)

### Typescript 설치 및 환경설정

### ESLint 설치 및 환경설정

```typescript
Ok to proceed? (y)

? How would you like to use ESLint?
> To check syntax, find problems, and enforce code style

// commonJS가 있으나 최근 추세는 esModule로 옮겨지고 있는 추세다
? What type of modules does your project use?
> JavaScript modules (import/export)

? Which framework does your project use?
> React

? Does your project use TypeScript?
> Yes

? Where does your code run?
> Browser

// style 가이드를 커스텀으로? 적용되어 있는 다른 스타일로
? How would you like to define a style for your project?
> Use a popular style guide

// XO 버전으로 사용하겠다.
? Which style guide do you want to follow?
> XO: https://github.com/xojs/eslint-config-xo-typescript

// eslint 포맷 방식
? What format do you want your config file to be in?
> JavaScript

? Would you like to install them now?
> Yes

? Which package manager do you want to use?
> npm
```

```typescript
// .eslintrc.js 파일 수정

// jest 파일도 검사하겠다는 뜻
env: {
  ...
  jest: true;
  ...
}
```

- .eslintignore 파일 생성 후 .gitignore 파일과 동일하게 작성

### React 설치 및 설정

### 테스트 도구 설치 (Jest)

### Parcel 설치 및 환경설정

- 번들링 명령어를 작성하기 위해 package.js 파일 수정

```typescript
"scripts": {
  "start": "parcel --port 8080", // run 명령어
  "build": "parcel build", // build 명령어
  "check": "tsc --noEmit",
  "lint": "eslint --fix --ext .js,.jsx,.ts,.tsx .", // eslint --fix 명령어
  "test": "jest",
  "coverage": "jest --coverage --coverage-reporters html",
  "watch:test": "jest --watchAll"
},
```
