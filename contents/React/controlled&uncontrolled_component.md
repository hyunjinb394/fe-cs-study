# 📚 제어 컴포넌트와 비제어 컴포넌트

## 📖 제어컴포넌트

- React에 의해, 즉 state를 통해 값이 제어되는 입력 폼 엘리먼트
- 다양한 기능 제공: 즉각적인 필드 검증 / 조건부로 제출 버튼 비활성화 / 입력 형식 적용 / 하나의 데이터에 대한 여러 입력 / 동적 입력 가능
- React, real DOM, 사용자가 보는 화면을 동기화 해 줘야 하는 번거로움 존재

## 🔍 예시 코드

```js
import React, { useState } from "react";

function MyInput() {
  const [inputValue, setInputValue] = useState(null);

  const handleChange = (e) => {
    setInputValue(e.target.value);
  };

  return <input onChange={(e) => handleChange(e)} value={inputValue} />;
}
```

## 📖 비제어 컴포넌트

- DOM 자체에서 다루어지는 폼 데이터
- DOM에 신뢰 가능한 출처를 유지: react 코드와 non react 코드 통합 시 쉬울 수 있음
- 빠르고 간편, 적은 코드량
- 값이 업데이트 될 때마다 리렌더링 되는 것이 아님: 성능상의 이점

## 🔍 예시 코드

```js
import React, { useRef } from "react";

function Test() {
  return <MyInput />;
}

function MyInput() {
  const inputNode = useRef(null);

  return <input ref={inputNode} />;
}

export default MyInput;
```

### 📍 React Hook Form

- 유연성과 확장성이 높고(커스텀 컴포넌트와의 통합이 간단 & 다른 상태관리 라이브러리와 함께 사용 가능 등), 유효성 검사 기능을 제공하는 리액트 라이브러리
- API가 쉽고 직관적이며, 컴포넌트 상태 관리를 간단하게 도와줌
- 비제어 컴포넌트 기반(ref 사용)이면서 제어 컴포넌트에 대한 지원도 됨

### 🔍 예시 코드

```js
import React from "react";
import { useForm } from "react-hook-form";

export default function App() {
  const { register, handleSubmit } = useForm();
  const onSubmit = (data) => console.log(data);

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input name="firstName" ref={register} />
      <input name="LastName" ref={register} />
      <input type="submit" />
    </form>
  );
}
```

  </br>

## 🗂️ 참고

[React - 폼]
https://ko.legacy.reactjs.org/docs/forms.html#controlled-components

[제어 컴포넌트 vs 비제어 컴포넌트]
https://velog.io/@thumb_hyeok/%EC%A0%9C%EC%96%B4-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-vs-%EB%B9%84%EC%A0%9C%EC%96%B4-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8

[React: 제어 컴포넌트와 비제어 컴포넌트의 차이점]
https://velog.io/@yukyung/React-%EC%A0%9C%EC%96%B4-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%EC%99%80-%EB%B9%84%EC%A0%9C%EC%96%B4-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90-%ED%86%BA%EC%95%84%EB%B3%B4%EA%B8%B0

[react hook form 이란?]
https://developer-alle.tistory.com/421

[React-Hook-Form 이란?]
https://hyebeen2658.tistory.com/71
