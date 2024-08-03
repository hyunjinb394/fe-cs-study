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

- 동작방식 및 구성 요소

![img](https://velog.velcdn.com/images%2Frealsnoopso%2Fpost%2F79f30823-80f0-4a6c-9731-83af961eef55%2FFrame%203.png)

### 🔍 예시 코드

```js
// Action Creator: 액션 생성 함수 / export 해서 dispatch와 함께 사용

export function createBucket(bucket) {
  return {
    type: CREATE,
    bucket: bucket,
  };
}
```

```js
// Action(Type): 액션의 타입(액션을 불러오는 주소)을 만드는 곳

const CREATE = "bucket/CREATE";
const DELETE = "bucket/DELETE";
```

```js
// Reducer: 실질적으로 store에 들어가 데이터를 변경하는 곳 / 리덕스에 저장된 state를 변경하는 함수

export default function reducer(state = initialState, action = {}) {
  switch (action.type) {
    case "bucket/CREATE": {
      const new_bucket_list = [...state.list, action.bucket];
      return { list: new_bucket_list };
    }

    case "bucket/DELETE": {
      const new_bucket_list = state.list.filter((l, idx) => {
        return parseInt(action.bucket_index) !== idx;
      });

      return { list: new_bucket_list };
    }
    default:
      return state;
  }
}
```

```js
// Store: 리덕스 적용을 위해 만드는 것 / 리듀서, 현재 애플리케이션의 상태, 리덕스에서 값을 가져오고 액션을 호출하기 위한 내장 함수가 포함됨

import { createStore } from "redux";
import reducers from "./reducers";

const store = createStore(reducers);
```

```js
// Dispatch: 스토어의 내장 함수 중 하나 / 액션을 발생시키는 역할

dispatch(액션생성함수명);
```

- 장점

1. 사용하는 곳이 많음: 참고자료 多
2. 불변객체로 유지하기 때문에 예측 가능한 상태관리
3. Redux devtools를 이용해 직관적으로 전역 상태를 볼 수 있음 -> 전역으로 관리하는 상태 값이 많을 경우 디버깅이 편한 편

- 단점

1. 다소 높은 러닝커브
2. 상태, 액션, 리듀서를 정의하는 데 추가적인 코드 필요(Store 복잡, 많은 보일러플레이트 코드)
3. 비동기를 위한 redux-thunk, redux-saga 등의 미들웨어가 필수로 요구됨

### 📍 Zustand

- 동작 방식

발행/구독 모델을 기반으로 작동, 상태는 클로저를 통해 내부적으로 관리

### 🔍 예시코드

```js
const store = createStore((set) => ({
  count: 0,
  setCount: (newCount) => set({ count: newCount }),
})); // 스토어 생성

store.subscribe((state) => console.log("상태가 변경됨: ", state)); // 상태변화를 구독하고 변화가 있을 때마다 반응
store.setState((state) => ({ count: state.count + 1 })); // setState: 새 상태를 계산, 상태가 실제로 변경되면 상태 갱신
```

카운터의 상태를 관리하며, 상태가 변경될 때 마다 콘솔에 상태 변경을 로그하는 예시코드

- 장점

1. Redux 기반(Flux 패턴): Redux의 redux devtools로 디버깅이 가능.
2. 보일러플레이트 적음
3. 낮은 러닝커브
4. provider가 필요 없음: 앱을 래핑하지 않아도 되어 불필요한 리렌더링 최소화 가능

- 단점

1. 커뮤니티의 부족

### 📍 Jotai

- 동작 방식

Atom 함수를 사용해 init, read, write, toString 메서드를 가지는 Atom Config 생성 / Atom 자체로 값을 가지는 것이 아닌 Atom을 통해 store에 접근해 값을 가져옴

### 🔍 예시코드

```js
import { atom } from "jotai";

const primitiveAtom = atom(10);

const readOnlyAtom = atom((get) => get(priceAtom) * 2);

const writeOnlyAtom = atom(null, (get, set, update) => {
  set(priceAtom, get(priceAtom) - update.discount);
});

const readWriteAtom = atom(
  (get) => get(priceAtom) * 2,
  (get, set, newPrice) => {
    set(priceAtom, newPrice / 2);
  }
);
```

예시 코드(1) atom의 사용법 4가지: primitive / 읽기전용 / 쓰기전용 / 읽기 & 쓰기

```js
import { atom, useAtom } from "jotai";
const textAtom = atom("hello");
const Input = () => {
  const [text, setText] = useAtom(textAtom);
  const handleChange = (e) => setText(e.target.value);
  return <input value={text} onChange={handleChange} />;
};
```

예시 코드(2) 초기값을 atom으로 생성, useAtom으로 값을 받고 수정

- 장점

1. React Hooks에 익숙하다면 매우 낮은 러닝커브
2. SSR, 비동기, Family 등 다양한 유틸리티 지원
3. 유연성: atom 단위를 사용하여 서로 상태 관여가 가능

- 단점

1. 커뮤니티의 부족

## 📖 Server State

- 웝 애플리케이션의 백엔드에 저장되어 있는 데이터로 데이터베이스, 파일 시스템, 캐시 등에 저장되어 관리
- Fetching 및 Updating에 비동기 API 필요
- 다중 사용자 환경에서 공유되며, 사용자가 모르는 사이 변경될 수 있음
- 클라이언트에서 요청이 있을 때 서버로부터 데이터를 가져와 업데이트 하거나 서버에 변경사항 전송

## 📖 Server State 주요 라이브러리

### 📍 Tanstack Query(구 React Query)

- 동작 방식

1. Client가 React Query에 유니크한 Key 값을 통한 데이터 요청을 보냄
2. React Query 메모리에 해당 Key 값에 대한 정보가 없다면 서버로 네트워크 요청을 보내고 서버로부터 데이터를 받아 Client에게 전달 / 이때 React Query에서는 해당 Key에 대한 정보를 메모리에 저장하여 Caching에 이용
3. Client에서 동일한 Key 값으로 데이터 요청을 한다면 React Query에 이미 저장되어 있던 데이터를 그대로 Client에게 전달
4. 만약 데이터가 오래되었다면(stale 상태라면) 서버에 다시 데이터 요청을 하여 최신의 데이터를 받은 후, Client에게 다시 업데이트된 데이터를 전달

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

- 동작 방식

캐시로부터 데이터를 반환한 후, fetch 요청을 하고, 최신화된 데이터를 가져옴

### 🔍 예시코드

```js
import useSWR from "swr";

function Profile() {
  const { data, error, isLoading } = useSWR("/api/user", fetcher);

  if (error) return <div>failed to load</div>;
  if (isLoading) return <div>loading...</div>;
  return <div>hello {data.name}!</div>;
}
```

useSWR hook이 key 문자열과 fetcher 함수를 받아 세 개의 값(data, error, isLoading) 반환하는 예시코드

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

[Redux의 동작 방법]
https://velog.io/@realsnoopso/Redux%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EB%8F%99%EC%9E%91%ED%95%A0%EA%B9%8C

[리액트에서 Zustand로 상태 관리 쉽게 하기]
https://www.allmyuniverse.com/zustand-in-react-conveniently-manage-state/

[Jotai 동작원리 파헤치기(1)]
https://byjuun.com/posts/React/jotai-1

[Jotai는 조-타이 라고 읽습니다.]
https://medium.com/pinkfong/jotai%EB%8A%94-%EC%A1%B0-%ED%83%80%EC%9D%B4-%EB%9D%BC%EA%B3%A0-%EC%9D%BD%EC%8A%B5%EB%8B%88%EB%8B%A4-6498535abe11

[TanStack Query(React Query) 시작]
https://velog.io/@mk0504/TanStack-Query-React-Query-%EC%8B%9C%EC%9E%91

[데이터 가져오기를 위한 React Hooks]
https://swr.vercel.app/ko
