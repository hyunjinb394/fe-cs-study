# 📚 useState로 살펴본 컴포넌트 렌더링 원리

## 📖 useState의 역할
- 상태를 정의하고 상태의 저장과 업데이트를 가능하게 해주는 훅
- 그럼 useState의 내부구현은 어떤 식으로 되어있을까? 

</br>

## 📖 useState 내부구현
### 📍 클로저
- 클로저는 함수 내부의 중첩함수로 생성될 시의 환경을 기억하기 때문에 state를 기억하고 setState로 변경된 값을 가져올 수 있음

    ```js 
    const useState = (initValue) ⇒ {

    let state = initValue;

    const getState= () ⇒ state;

    const setState = (newValue) ⇒ {

    state = newValue;

    return [getState, setState]

    }

    const [ record, setRecord ] = useState(””);

    record()

    setRecord(”진짜 졸리다..”)

    record()   // “진짜 졸리다” 

    ```
- state를 쓸때 state()로 함수로 호출하지 않음
- React 모듈로부터 값을 가져오도록 작성
    ```js
    const React = () => {
    let value;

    const useState = (initValue) => {
    const state = value ?? initValue;

    const setState = (newValue) =>{
    value = newValue;
    }
    return [state, setState];
    }

    return { useState }
    }
    ```
- 이렇게 작성하면 React() 함수를 실행해버리면 모든 동작이 끝나고 상태가 휘발됨
- 새롭게 React 모듈을 기억하는 객체를 정의

</br> 

### 📍 즉시 실행함수 패턴
- 아래 코드를 setState에 값을 넣고 React.useState을 실행하면 value 값이 휘발되지 않고 잘 바뀜
```js
const React = (() =>{
    let value;
 
 return (initValue) =>{
     let state = value ?? initValue;
 
 const setState = (newValue) =>{
     value = newValue;
 }
 return [state, setState]; 
 }
})()
```
- 하지만 React에서 setState에 값을 넣고 useState을 실행해 UI를 그려야함 



### 📍 Render 함수 추가
- 즉 상태를 관리하는 useState가 있고 반환된 setter 함수를 사용해 상태가 변경되면 다시 렌더링을 트리거 함
- 컴포넌트를 생성하는 render 함수가 있고, 상태가 변경될 때마다 최신 상태 값을 사용해 UI를 업데이트 함
```js
const React = (() => {
 let value;
 
 const useState = (initValue) => {
 const state = value ?? initValue;
 
 const setState = (newValue) =>{
 value = newValue;
 }
 return [state, setState]; 
 }
 
 const render = () =>{
  const Component = () =>{
 const [count, setCount] = React.useState(0);
 return {
 render:() => console.log(count),
 click: (value) => setCount(value)
 };
}
 return Component;
 }
 
 return { useState, render }
})()
```
- useState 동작 원리를 통해서 컴포넌트가 재렌더링 되는 원리를 이해할 수 있음

</br> 



