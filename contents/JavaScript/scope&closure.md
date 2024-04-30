# 📚 Scope & Closure


## 📖 Scope & Closure 란?
- `Scope`란 변수가 유효한 범위
- 자바스크립트 엔진이 코드를 실행하기 전 Lexical Scope 분석
- `Closure`란 함수와 함수가 선언된 Lexical Scope의 조합

</br>

## 🔍 예시코드
```js
function outer(){
  let outerLet = 'I am from outer';

  function inner(){
    console.log(outerLet);
  }
  return inner;
}

let innerFunc = outer();
innerFunc();
```
- inner 함수는 outer 함수의 스코프에 있는 outerLet 변수에 접근 가능
- inner 함수가 outer 함수의 렉시컬 환경을 기억하기 때문

</br>

## 📖 Scope & Closure 란?
### 📍 Scope
- `스코프 체인`이란 변수를 찾기 위해 스코프를 순차적으로 탐색하는 과정
- 내부 스코프에서 변수를 찾지 못하면, 연결된 외부 스코프에서 탐색

![scope-chain](https://velog.velcdn.com/post-images%2Fbathingape%2F4f517250-1384-11ea-af6d-0d4ea8242636%2Fimage.png)

- `실행 컨텍스트`란 코드가 실행되기 위한 환경
- 함수 호출 시 마다 실행 컨텍스트가 생성되며 스코프, 변수 객체, this 바인딩 등 포함

</br> 

## 🔍 예시코드
```js
function first(){
  let a = 'First';
  second();

  function second(){
    let b = 'Second';
    third();
  }
}

function third(){
  let c = 'Third';
  console.log(a + b + c);
}

first();
```

- third 함수는 a와 b 변수에 접근 불가
- 각 함수가 자신만의 실행 컨텍스트를 가지고, 스코프 체인을 통해 변수에 접근하기 때문

</br> 

### 📍 Closure
- 비동기 처리, 이벤트 핸들러, 데이터 은닉 및 캡슐화, 모듈 패턴 등의 상황에서 사용
  - 비동기 처리 : 콜백 함수 내부에서 외부 변수에 접근해야 할 때 유용
  - 데이터 은닉과 캡슐화 : 객체의 속성과 메서드를 외부로부터 보호하는 방법 제공
  - 모듈 패턴 : 공개적 접근 가능한 메서드, 변수 정의 및 외부 접근 불가한 메서드, 변수 구현에 사용

</br> 



## 🗂️ 참고
[F-lab - 클로저와 스코프 : 자바스크립트의 핵심 개념 이해하기](https://f-lab.kr/insight/understanding-closure-and-scope)
[Velog - 스코프와 클로저 이해](https://velog.io/@bathingape/%EC%8A%A4%EC%BD%94%ED%94%84Scope%EC%99%80-%ED%81%B4%EB%A1%9C%EC%A0%80Closure-%EC%9D%B4%ED%95%B4)