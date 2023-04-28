# ⚡ 서버 사이드 렌더링(SSR)

## 📌 서버 사이드 렌더링이란?

### 🔷 MPA(Multi Page Application) + ajax + pushState

- 브라우저가 페이지에 첫 진입할 때 서버는 HTML을 만들어 내린다.
- 이후로 페이지 전환이 발생하더라도 브라우저는 ajax와 pushState로 페이지 이동 없이 서버로부터 HTML 파일만 받을 수 있다.

🤷‍♂️ 왜 SSR을 해야할까?

1. 검색 엔진 최적화
 - 과거에는 ajax 호출을 통한 렌더링 결과를 수집하지 못했다. 하지만 요즘엔 검색 엔진이 발전하여 수집하는 경우도 있다.

2. 더 빠른 초기 로딩 속도
 - Client-Side 렌더링은 브라우저 렌더링 후 데이터를 가져오기 위한 로직이 수행되어야 해서 더 느릴 수 밖에 없다. 첫 렌더링 후엔 Client-Side 렌더링을 택하면 된다.

❗ 기존 SSR의 문제점
 - Server-Side와 Client-Side에서 각각 렌더링을 위한 코드를 따로 만들어야 했다.

이를 해결하기 위해 Isomorphic(Universal)이라는 방식이 등장했다.

같은 코드로 Server와 Client에서 동일하게 실행되는 환경
같은 언어로 동작하는 Node.js를 서버로 사용하는 경우가 많다.
대신, 하나의 자바스크립트 코드에 제약이 많이 붙는다. 같은 코드로 동작할 수 있도록 만들어야하기 때문.
NEXT.js가 이를 지원한다. (react 기반)

- Vercel에서 오픈 소스로 제공
- https://nextjs.org/
- yarn create next-app --typescript
or
- npx create-next-app@latest --typescript

## 원리
    - pages/about.js 를 만들면 자동으로 /about 으로 라우팅
    - 동적 라우팅의 경우 대괄호 사이에 파라미터를 넣어주는 식으로 사용
    - pages/posts/[id].js -> posts/1, posts/2
    - yarn dev 로 실행

## 구조
    - index.jsx: 실행시켰을 때 가장 처음 보이는 페이지
    - _app.tsx: 모든 페이지가 거쳐서 실행되는 곳
    - public: 리소스들을 올려놓는 곳
    - styles: next.js는 기본적으로 css 모듈을 제공하는데 확장자와 이름 사이에 `module`을 넣어 파일을 생성한다.
    - 우리는 대신 emotion을 사용할 것이다.

https://velog.io/@bzeromo/next
