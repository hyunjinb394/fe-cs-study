# 📚 React Router

## 📖 React Router란?

- 리액트에서 주소에 따른 컴포넌트 렌더링을 관리하기 위한 라이브러리
- 서버에게 별다른 요청을 보내지 않고 클라이언트의 브라우저 단에서만 페이지를 이동하는 CSR(Client Side Rendering)이다.

### 📍 React Router v5 -> v6 변경된 점

- Route 등록: switch 내부 -> routes 내부
- 경로에 맞는 컴포넌트 등록: component 속성값 -> element 속성값
- 정확한 경로지정: exact -> default로 exact 적용
- 하위 경로 모두 포함하기: exact 제외 -> path 경로 뒤에 \* 을 붙임
- Route에 path 등록: 절대경로만 사용 가능 -> 상대 경로도 사용 가능
- 페이지 이동: useHistory -> useNavigate
- 부모 경로로 이동: 절대경로사용 -> .. 사용 가능
- 파라미터로 전달된 값 확인: match의 params -> useParams
- 리다이렉트: Redirect(속성값: default, push) -> Navigate(속성값: replace, default)
- withdRouter -> useParams, useLocation, userNavigate

### 📍 Router에서 페이지를 이동할 때 a 태그가 아닌 link를 쓰는 이유?

- a 태그의 href는 페이지 이동 시 페이지를 새로 불러온다. 따라서 상태 값이 유지되지 못하고 속도도 저하됨.
- link는 HTML5 API를 사용, 브라우저의 주소만 바꾸고 페이지를 새로 불러오지 않음.
- 따라서 link를 사용하는 것이 SPA의 장점을 극대화 할 수 있어 리액트에서는 link를 권장.
  </br>

## 🔍 예시코드

```js
// Redirect -> Navigate
// Switch -> Routes
// component, render, exact등 <Route> 태그의 일부 속성 변경
// React Router v5

import { Redirect, Switch, Redirect, Route } from "react-router-dom";

return (
  <Switch>
    <Redirect exact from={"/"} to={"/login"} />
    <Route path={"/login"} render={(props) => <LoginPage {...props} />} />
  </Switch>
);
// React Router v6

import { Navigate, Routes, Route } from "react-router-dom";

return (
  <Routes>
    <Route path="/" element={<Navigate replace to="/login" {...props} />} />
    <Route path={"login"} element={<LoginPage {...props} />} />
  </Routes>
);
```

```js
// useHistory -> useNavigate
// React Router v5

import { useHistory } from "react-router-dom";
const history = useHistory();
history.push({
  pathname: "/login",
  state: {
    loginInfo: loginInfo,
  },
});
// React Router v6

import { useNavigate } from "react-router-dom";
const navigate = useNavigate();

navigate("/login", {
  replace: true,
  state: { loginInfo: loginInfo },
});
```

## 🗂️ 참고

[react router 공식문서]
https://reactrouter.com/en/main

[Router / router-dom v5 -> v6 버전 업 이해하기]
https://adjh54.tistory.com/48#1.%20%EC%A4%91%EC%B2%A9%20%EA%B2%BD%EB%A1%9C%20%EC%B6%94%EA%B0%80-1

[react router에 대해 알아보자]
https://velog.io/@jeong_lululala/react-router-routes

[TIL 26_Link와 a태그의 href의 차이]
https://velog.io/@rhfovk/TIL-26Link%EC%99%80-a%ED%83%9C%EA%B7%B8%EC%9D%98-href%EC%9D%98-%EC%B0%A8%EC%9D%B4
