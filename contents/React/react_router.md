# 📚 React Router

## 📖 React Router란?

- 리액트에서 주소에 따른 컴포넌트 렌더링을 관리하기 위한 라이브러리
- 서버에게 별다른 요청을 보내지 않고 클라이언트의 브라우저 단에서만 페이지를 이동하는 CSR(Client Side Rendering)

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

- a 태그의 href는 페이지 이동 시 페이지를 새로 불러오기 때문에 상태 값이 유지되지 못하고 속도도 저하됨
- link는 HTML5 API를 사용, 브라우저의 주소만 바꾸고 페이지를 새로 불러오지 않음
- 따라서, link를 사용하는 것이 SPA의 장점을 극대화 할 수 있어 리액트에서는 link를 권장
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

</br>

## 📖 동적 라우팅이란?

- 보통 웹 사이트는 전체 아이템이 보여지는 리스트 페이지와 특정 아이템 선택 시 보이는 상세 페이지로 구분
- 예를 들면 FEStudy/List/ 끝에 해당 아이템의 id 값이 추가되어 페이지 이동
- 라우트 경로에 특정 값을 넣어 해당 페이지로 이동할 수 있게 하는 것이 `동적 라우팅`

</br>

### 📍 Path Parameter
- 라우트 경로 끝에 들어가는 id 값을 저장하는 매개 변수

## 🔍 예시코드
```js
localhost:3000/products/2
localhost:3000/products/45
localhost:3000/products/125
```
- 2, 45, 125와 같이 라우트 경로 끝에 들어가는 id값을 저장하는 매개변수

</br>

```js
<Router>
	<Routes>
		<Route path='/product/:id' element={<productDetail />} />
	</Routes>
</Router>

function ProductDetail() {
	const params = useParams();
	const productId = params.id;
}
```
- : 는 Path Parameter가 올 것을 의미
- id는 해당 Path Parameter 의 이름을 의미 (변수명과 같이 임의 설정 가능)

</br>

### 📍 useNavigate, useParams, useLocation Hook
- useNavigate 는 페이지 이동을 위한 메서드
- useLocation 은 현재 url 경로에 대한 정보 담음
- useParams 는 Path Parameter에 대한 정보 담음


## 🔍 예시코드
```js
// Routes.js
<Route exact path='/product/detail/:id' element={<ProductDetail />} />

// ProductDetail.js
const navigate = useNavigate();
const location = useLocation();
const params = useParams();

<Link to="" />
navigate(`/product/detail/${productId}`);
const productId = params.id;

// { history: {}, location: {}, match: {}, ... }
console.log({ history, location, match }) 
return (
	...
);	
```

</br>

### 📍 useParams().id
- Path Parameter로 명시해 둔 값은 params 객체에 담김


## 🔍 예시코드
```js
// ProductDetail.js
// current url -> localhost:3000/product/1

function ProductDetail() {
	const params = useParams();

	console.log(params.id) // 1

	return (
		...
	);	
}
```

</br>

### 📍 동적 라우팅의 구현 흐름
- 리스트 페이지의 개별 상품 클릭 (navigate로 상세페이지 이동)
- 상세 페이지 이동 시, url 변경
- 페이지에 필요한 데이터 fetching
- 서버에서 가져온 데이터 state에 저장
- UI 렌더링

## 🔍 예시코드
```js
const params = useParams();

useEffect(() => {
	const { id } = params;
	fetch(`http://123.456.123.123:8000/products/${id}`) // 1
		.then(res => res.json())
		.then(res => setState({ data: res }))
}, [match]);
```

</br>

## 📖 Error Boundary 란?

- 하위 컴포넌트 트리의 어디에서든 자바스크립트 에러 기록
- 깨진 컴포넌트 트리 대신 fallback UI를 보여주는 React 컴포넌트
- 이벤트 핸들러, 비동기적 코드, 서버사이드 렌더링, 자식 컴포넌트가 아닌 에러 경계 자체에서 발생하는 에러에서는 포착 불가

</br>

## 🔍 예시코드
```js
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    // 다음 렌더링에서 폴백 UI가 보이도록 상태 업데이트
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    // 에러 리포팅 서비스에 에러를 기록
    logErrorToMyService(error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      // 폴백 UI를 커스텀하여 렌더링
      return <h1>Something went wrong.</h1>;
    }

    return this.props.children;
  }
}
```
- React hook에는 static getDerivedStateFromError() 나 componentDidCatch()와 같은 메소드가 없기 때문에 리액트 공식 문서에는 class형 컴포넌트 사용 예시만 존재
- 클래스 형으로 작성된 에러바운더리는 대부분 함수형으로 작성된 리액트 프로젝트에 일관성 해침

</br>


### 📍 react-error-boundary
- 클래스형 에러 바운더리와 거의 동일한 기능을 하면서 함수형으로 작성 가능
- [npm - react-error-boundary](https://www.npmjs.com/package/react-error-boundary)


## 🔍 예시코드
```js
<ErrorBoundary
	fallbackRender={fallbackProps => <ErrorFallback {...fallbackProps} />}
>
	{children}
</ErrorBoundary>
```
- 기본 props로는 fallback, fallbackRender 등이 있음
- fallbackRender : 에러 시 보여줄 컴포넌트

</br>

```js
const ErrorFallback = ({ error, resetErrorBoundary }: FallbackProps) => {

return (
      <section>
        <div>
          <p>이용에 불편을 드려 죄송합니다.</p>
          <p>
            동일한 현상이 계속될 경우 문의 주시기 바랍니다.
          </p>
          <button onClick={resetErrorBoundary}>
            다시 시도하기
          </button>
        </div>
      </section>
      )
}
```
- error : 발생한 에러 정보
- resetErrorBoundary : 에러바운더리 리셋 후 렌더링 재시도하는 함수

</br>

```js
<ErrorBoundary resetKeys={location.pathname}> {cildren} </ErrorBoundary>
```
- resetKeys : 에러바운더리에 key를 지정해 key가 바뀌면 자동으로 리셋
- onReset : 에러 바운더리가 리셋될 때 호출되는 속성

</br>


## 🗂️ 참고

[react router 공식문서](https://reactrouter.com/en/main)

[Router / router-dom v5 -> v6 버전 업 이해하기](https://adjh54.tistory.com/48#1.%20%EC%A4%91%EC%B2%A9%20%EA%B2%BD%EB%A1%9C%20%EC%B6%94%EA%B0%80-1)

[react router에 대해 알아보자](https://velog.io/@jeong_lululala/react-router-routes)

[TIL 26_Link와 a태그의 href의 차이](https://velog.io/@rhfovk/TIL-26Link%EC%99%80-a%ED%83%9C%EA%B7%B8%EC%9D%98-href%EC%9D%98-%EC%B0%A8%EC%9D%B4
)

[Velog - 동적라우팅(Dynamic Routing)](https://velog.io/@zzangzzong/React-%EB%8F%99%EC%A0%81%EB%9D%BC%EC%9A%B0%ED%8C%85Dynamic-Routing)

[Velog - 에러 바운더리(Error Boundary)](https://velog.io/@bbaa3218/React-%EC%97%90%EB%9F%AC-%EB%B0%94%EC%9A%B4%EB%8D%94%EB%A6%ACError-Boundary)

[Velog - 리액트 에러관리](https://velog.io/@xun415/%EB%A6%AC%EC%95%A1%ED%8A%B8-%EC%97%90%EB%9F%AC-%EA%B4%80%EB%A6%AC-ErrorBoundary-react-error-boundary)