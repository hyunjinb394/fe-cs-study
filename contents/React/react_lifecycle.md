# 📚 React의 Life cycle

- 컴포넌트의 수명 주기를 의미
- 레이지에서 렌더링 되기 전인 준비 과정부터 페이지에서 사라질 때 까지를 의미

## 📖 Life cycle이 있는 이유

- 메모리 비우기
- 컴퓨터의 자원은 한정적: 역할이 끝나면 메모리를 반환 해야, 메모리 누수를 막고 좋은 성능 발휘 가능

## 📖 Life cycle의 세 가지 유형

### 📍 생성(마운팅)

- DOM이 생성되고, 웹 브라우저 상에서 나타나는 것
- Method: 클래스 생성자, static getDerivedStateFromProp, shouldComponentUpdate, render, componentDidMount

### 📍 업데이트(업데이팅)

- Props나 State가 바뀔 때 / 부모 컴포넌트가 리랜더링 될 때 / this.forceUpdate로 강제로 렌더링 trigger하는 경우
- Method: componentWillTeceiceProps, shouldComponentUpdate, getSnapShotBeforeUpdate, componentWillUpdate, componentDidUpdate

### 📍 제거(언마운팅)

- 컴포넌트가 DOM에서 제거되는 것
- Method: componentWillUnmount
  </br>

## 🔍 참고 이미지

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fq9wy0%2FbtrXHXekPhE%2FijbyePnjK9xXigUkDQPSUK%2Fimg.png)
</br>

## 🗂️ 참고

[리액트 라이프 사이클]
https://velog.io/@remon/React-%EB%A6%AC%EC%95%A1%ED%8A%B8-%EB%9D%BC%EC%9D%B4%ED%94%84-%EC%82%AC%EC%9D%B4%ED%81%B4

[React 컴포넌트의 생명 주기(Life Cycle)]
https://shape-coding.tistory.com/entry/React-React-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%EC%9D%98-%EC%83%9D%EB%AA%85-%EC%A3%BC%EA%B8%B0-Life-Cycle
