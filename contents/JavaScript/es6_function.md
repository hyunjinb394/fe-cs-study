# 📚 ES6에서 추가된 기능
- let & const
- Arrow Function
- Default Parameters
- Class Syntax
- Import/Export
- Promises
- Rest Parameters & Spread Operator
- for .. of 
- map & set object
- Conditional operator
- Template literal

## 📖 let & const
### 📍 var를 안써야하는 이유
- var는 함수 레벨의 스코프를 가짐
- 함수 외부에서는 참조할 수 없음
- 함수 밖에 var로 선언된 변수는 전역변수  
- 재선언이 가능해서 의도치 않게 변수가 바뀔 수 있음

</br> 

### 📍 let & const 특징
- `블록 레벨 스코프`를 가짐
- 같은 함수 내에서도 블록 단위로 유효범위를 가지기 때문에 변수가 의도치 않게 사용되는 것을 막을 수 있음
- let과 const는 **선언 단계와 초기화 단계가 동시에 이루어지지 않음**
- 변수가 선언되었지만 할당되지 않은 그 사이의 지점을 `TDZ 영역`이라고 함
- TDZ(Temporal Dead Zone) 영역에 있는 할당되지 않은 변수에 접근할때 `ReferenceError` 발생
- 코드의 안정성을 높힐 수 있고 예측 가능한 결과를 얻을 수 있음

</br> 

### 📍 TDZ에 영향을 받는 구문
     ❗ 순서에 유의하면 사용
- const
- let 
- class

</br> 


### 📍 TDZ에 영향을 받지 않는 구문
- var
- function
- import


</br>

## 📖 Arrow Function
### 📍 간결한 표현
```js

let sum = function(a, b) {
  return a + b;
};

let sum = (a, b) => a + b;

```

- 내용
- 내용

</br> 

### 📍 This 바인딩
- 내용
- 내용

</br> 


## 📖 Arrow Function





</br>

## 🗂️ 참고
