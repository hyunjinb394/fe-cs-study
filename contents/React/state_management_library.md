# 📚 React의 상태관리

- 상태: 관리해야 하는 데이터들 / 시간에 따라 변화
- React는 단방향 바인딩 -> Props Drilling 이슈 존재
- UX/UI의 중요성과 함께 FE에서 수행하는 역할이 늘어남
- 관리해야하는 상태가 많아짐에 따라, 상태관리 또한 중요해짐

## 📖 Client State

- 웹 애플리케이션의 프론트엔드에서 관리되는 데이터로 사용자의 브라우저 또는 애플리케이션 내에 저장되어 관리
- 초기값 설정이나 조작에 제약 사항 없음
- 단일 사용자 환경에서만 유효, 클라이언트 간에 공유되지 않음
- Client 내에서 UI/UX 흐름이나 사용자 인터랙션에 따라 변화

## 📖 Client State 주요 라이브러리

### 📍 Redux

- 장점

1. 사용하는 곳이 많음: 참고자료가 많다
2. 불변객체로 유지하기 때문에 예측 가능한 상태관리
3. Redux devtools를 이용해 직관적으로 전역 상태를 볼 수 있음 -> 전역으로 관리하는 상태 값이 많을 경우 디버깅이 편한 편

- 단점

1. 다소 높은 러닝커브
2. 상태, 액션, 리듀서를 정의하는 데 추가적인 코드 필요(Store 복잡, 많은 보일러플레이트 코드)
3. 비동기를 위한 redux-thunk, redux-saga 등의 미들웨어가 필수로 요구됨

### 📍 Zustand

- 장점

1. Redux 기반(Flux 패턴): Redux의 redux devtools로 디버깅이 가능.
2. 보일러플레이트 적음
3. 낮은 러닝커브
4. provider가 필요 없음: 앱을 래핑하지 않아도 되어 불필요한 리렌더링 최소화 가능

- 단점

1. 커뮤니티의 부족

### 📍 Jotai

- 장점

1. React Hooks에 익숙하다면 매우 낮은 러닝커브
2. SSR, 비동기, Family 등 다양한 유틸리티 지원
3. 유연성: atom 단위를 사용하여 서로 상태 관여가 가능

- 단점

1. 커뮤니티의 부족

## 📖 Server State

- 웝 애플리케이션의 백엔드에 저장되어 있는 데이터로 데이터베이스, 파일 시스템, 캐시 등에 저장되어 관리
- Fetching 및 Updateing에 비동기 API 필요
- 다중 사용자 환경에서 공유되며, 사용자가 모르는 사이 변경될 수 있음
- 클라이언트에서 요청이 있을 때 서버로부터 데이터를 가져와 업데이트 하거나 서버에 변경사항 전송

## 📖 Server State 주요 라이브러리

### 📍 React-query

- 장점

1. 간편한 데이터관리
2. 실시간 업데이트 및 자동 동기화 지원
3. 데이터 캐싱: 불필요한 API 요청 감소(애플리케이션 성능 향상)
4. 간편한 설정

- 단점

1. 높은 러닝커브
2. 단순하지 않음: 프로젝트 규모에 적합한지 검토 필요
3. 데이터에 종속적: 데이터 구조에 변경이 생길 시 코드 수정 필요할 수 있음

### 📍 SWR

- 장점

1. 별도의 provider 없이 바로 사용 가능
2. 전역 설정을 통해 fetcher를 정해둘 수 있음
3. React query에 비해 작은 번들 사이즈

- 단점

1. 정식 devtool이 없음(서드 파티 라이브러리 사용)
2. react query에 비해 지원되는 기능이 적음
   </br>

## 🗂️ 참고

[서버 상태 ❤️ 클라이언트 상태]
https://velog.io/@okko8522/%EC%84%9C%EB%B2%84-%EC%83%81%ED%83%9C-%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8-%EC%83%81%ED%83%9C

[React Query와 상태관리 (1)]
https://velog.io/@godud2604/React-Query%EC%99%80-%EC%83%81%ED%83%9C%EA%B4%80%EB%A6%AC

[상태관리 라이브러리 비교: Redux vs Recoil vs Zustand vs Jotai]
https://velog.io/@iberis/%EC%83%81%ED%83%9C%EA%B4%80%EB%A6%AC-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC-%EB%B9%84%EA%B5%90-Redux-vs-Recoil-vs-Zustand-vs-Jotai

[React 상태관리 라이브러리 비교(Redux vs MobX vs Zustand vs Recoil)]
https://owni14.github.io/dev/react-06-compare-state-library.html

[상태 관리 라이브러리에 대한 고찰(feat, redux-toolkit, recoil, zustand, jotai)]
https://yong-nyong.tistory.com/94

[상태관리, 잘하고 싶다.]
https://leetrue.hashnode.dev/recoil-jotai-zustand

[TanStack Query - Overview]
https://tanstack.com/query/latest/docs/framework/react/overview

[React-query를 사용해 상태관리를 해보자]
https://musma.github.io/2023/09/14/react-query.html

[리액트 쿼리란]
https://www.jeje01.me/react/about-react-query/

[React Query 개념잡기]
https://velog.io/@kandy1002/React-Query-%ED%91%B9-%EC%B0%8D%EC%96%B4%EB%A8%B9%EA%B8%B0

[REACT QUERY VS SWR]
https://tech.madup.com/react-query-vs-swr/
