# 📚 ES6에서 추가된 기능 (1)
- let & const ✅
- Promises ✅
- async / await ✅
- Arrow Function
- Default Parameters
- Rest Parameters & Spread Operator
- Conditional operator
- for .. of 
- Import/Export
- Class Syntax
- map & set object
- Template literal

## 📖 let & const
### 📍 var를 지양해야하는 이유
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
     ❗ 순서에 유의하며 사용
- const
- let 
- class

</br> 


### 📍 TDZ에 영향을 받지 않는 구문
- var
- function
- import


</br>

## 📖 Promise
### 📍 Promise가 뭐죠?
- 자바스크립트의 비동기 처리에 사용되는 객체
- 서버에서 데이터를 받아오는 작업 같은 비동기 작업이 완료되지 않아도 다른 코드를 실행시킬 수 있음

### 📍 Promise 사용법
- Promise 생성 : new Promise() // pending 상태
- 생성 시 콜백함수 선언 : new Promise(function(resolve, reject){}); 
- 콜백함수의 인자로 받은 resolve를 실행 // fulfilled 상태
```js
new Promise(function(resolve, reject) {
  resolve();
}) 
```

- fullfilled가 되면 then()을 이용해 결과 값을 받을 수 있음
- reject() 호출 시 rejected 상태가 되고, 이후 처리 결과 값을 catch()로 받을 수 있음
``` js
function getData(){
  return new Promise(function(resolve, reject){
    reject(new Error("삐빅- 요청 실패"))
  });
}

getData().then().catch(function(err){
  console.log(err)  // Error: 삐빅- 요청 실패
})
```
- settled란, fulfilled or rejected된 상태를 나타내고 한번 상태가 결정되고 값을 가진 Promise는 다른 값으로 변경되지 않음

</br> 

### 📍 Promise methods
- then(a, b)  
a : promise가 성공적으로 fulfilled되었을 때 실행할 콜백함수  
b : promise가 rejected 되었을 때 실행할 콜백 함수  

- catch() : rejected 되었을때 실행되는 method
- finally() : 결과에 상관없이 비동기 작업이 완료된 뒤 실행되는 method
- all() : iterable한 객체를 매개변수로 받음, 배열에 있는 프로미스를 동시에 trigger하고 배열에는 리턴된 순서 대로 담김 
- race() : iterable한 객체를 매개변수로 받음, 결과값에 상관없이 가장 먼저 완료된 Promise의 결과를 resolve 

</br> 

### 📍 실무에서는 어떻게 사용할까?
- Promise Chaning을 통해서 여러 개의 프로미스를 호출할 수 있음  
- 로직의 실행순서를 제어할 수 있음   
``` js
getData(userInfo)
  .then(parseValue)
  .then(auth)
  .then(display);
```
- then()의 두번째 인자로도 에러를 처리할 수 있지만, then의 첫 번째 인자에 들어간 콜백함수에서 에러가 발생하면 에러를 잡아내지 못함  
- 효과적인 에러처리를 위해서 catch() 사용하자!


</br> 

## 📖 async & await

</br>


## 🗂️ 참고
[갓틴판교 - 자바스크립트 Promise 쉽게 이해하기 ]("https://joshua1988.github.io/web-development/javascript/promise-for-beginners/")

