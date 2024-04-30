# 📚 비동기 처리

## 📖 Callback 함수

### 📍 개념

- 함수의 매개변수를 통해 다른 함수의 내부로 전달되는 함수
- 비동기처리나 배열 고차 함수에서 사용

### 📍 주의점

- 콜백지옥: 가독성 저하, 유지보수 어려워짐
- 보완방법: Promise, Async/Await 사용

</br>

## 📖 Promise

### 📍 개념

- 비동기 처리 상태와 처리 결과를 관리하는 객체
- 프로미스 체이닝을 통한 비동기 후속처리

### 📍 주의점

- 콜백패턴을 사용함 -> 가독성 문제 발생
- 보완방법: Async/Await 사용

### 📍 동작 방식

- 비동기 처리를 수행할 콜백 함수를 인수로 전달받음
- 이 콜백함수는 resolve와 reject함수를 인수로 전달받음
- 생성 직후: Pending 상태
- 비동기 처리 성공: 결과를 resolve 함수에 인수로 전달 & 호출, fulfilled 상태
- 비동기 처리 실패: 에러를 reject 함수에 인수로 전달 & 호출, rejected 상태

### 📍 Promise의 후속 처리 메서드

- then: 성공처리, 실패처리 두 개의 콜백 함수를 인수로 전달받음
- catch: 한 개의 콜백함수를 인수로 전달받음, promise가 rejected 상태인 경우에만 호출
- finally: 한 개의 콜백함수를 인수로 전달받음, promise의 성공/실패와 무관하게 무조건 한 번 호출

### 📍 Promise의 정적 메서드

- resolve: 이미 존재하는 값을 래핑, promise 생성
- reject: 이미 존재하는 값을 래핑, promise 생성
- all: 여러 개의 비동기 처리를 모두 병렬 처리
- race: 가장 먼저 fulfilled 상태가 된 promise의 처리 결과를 resolve 하는 새로운 promise 반환
- allSettled: 전달받은 promise가 모두 settled 상태가 되면 처리 결과를 배열로 반환

</br>

## 📖 Async & Await

### 📍 개념

- promise의 후속 처리 메서드 없이, 비동기 처리를 동기처리처럼 동작하도록 구현
- Async: 암묵적으로 반환값을 resolve하는 promise 반환
- Await: promise가 settled 상태가 되면 promise가 resolve한 처리 결과 반환

## 🔍 예시코드

```js
// <JavaScript>
// 기본예시
function findName(name) {
  console.log("what is your name?"); //--- (1)
  console.log("...finding"); //--- (2)
  setTimeout(() => {
    console.log("your name is " + name); //--- (3)
  }, 3000);
  console.log("right?"); //--- (4)
}

findName("홍길동");

// callback 사용예시
function findName(name) {
  if (!name) return console.log("Sorry, I don't know you");
  console.log("your name is " + name); //--- (3)
  console.log("right?"); //--- (4)
}

function delay(id, cb) {
  console.log("what is your name?"); //--- (1)
  console.log("...finding"); //--- (2)
  setTimeout(() => {
    const data = { 1: "홍길동", 2: "스펀지밥" };
    cb(data[id]);
  }, 3000);
}

delay(1, findName);

// promise 사용예시
const findName = (id) =>
  new Promise((resolve, reject) => {
    console.log("what is your name?"); //--- (1)
    console.log("...finding"); //--- (2)
    setTimeout(() => {
      const data = { 1: "홍길동", 2: "스펀지밥" };
      if (typeof id !== "number")
        return reject(new Error("Id type is number!"));
      --ㄱ;
      if (!data[id]) return reject("Sorry, I don't know you");
      resolve("your name is " + data[id]);
    }, 3000);
  })
    .then((data) => {
      console.log(data);
      console.log("right?");
    }, console.log)
    .catch(console.log);

// promise와 async/await 사용예시
const promise = function (id) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = { 1: "홍길동", 2: "스펀지밥" };
      if (typeof id !== "number")
        return reject(new Error("Id type is number!")); //--- (3)
      if (!data[id]) return reject("Sorry, I don't know you"); //---(3)
      resolve("your name is " + data[id]); //---(3)
    }, 3000);
  });
};

async function findName(id) {
  try {
    console.log("what is your name?"); //--- (1)
    console.log("...finding"); //--- (2)
    const finded = await promise(id);
    console.log(finded); //---(3)
  } catch (err) {
    console.log(err); //---(3)
  }
}
```

</br>

## 🗂️ 참고
