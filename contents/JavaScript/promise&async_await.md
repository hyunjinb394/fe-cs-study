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
- 'try-catch' 블록을 사용으로 보다 직관적인 에러 처리 -> 오류 추적 및 디버깅 용이

## 🔍 예시코드

```js
// <JavaScript>
// callback 사용예시
function fetchData(callback) {
  setTimeout(() => {
    const data = { id: 1, name: "John Doe" };
    callback(null, data);
  }, 1000);
}

function processData(error, data) {
  if (error) {
    console.error("Error:", error);
    return;
  }
  console.log("Data:", data);
}

// fetchData 함수를 호출하고 콜백으로 processData 함수를 전달합니다.
fetchData(processData);

// promise 사용예시
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = { id: 1, name: "John Doe" };
      resolve(data);
    }, 1000);
  });
}

function processData(data) {
  console.log("Data:", data);
}

// fetchData 함수는 Promise를 반환합니다.
fetchData()
  .then(processData)
  .catch((error) => console.error("Error:", error));

// promise와 async/await 사용예시
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = { id: 1, name: "John Doe" };
      resolve(data);
    }, 1000);
  });
}

async function processData() {
  try {
    const data = await fetchData();
    console.log("Data:", data);
  } catch (error) {
    console.error("Error:", error);
  }
}

// processData 함수 호출
processData();
```

</br>

## 🗂️ 참고

[모던 자바스크립트 Deep Dive 42, 46장]
https://velog.io/@rekoding/JavaScript-%EB%AA%A8%EB%8D%98-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-Deep-Dive-46%EC%9E%A5-%EC%A0%9C%EB%84%88%EB%A0%88%EC%9D%B4%ED%84%B0%EC%99%80-asyncawait
https://velog.io/@zivivle/%EB%AA%A8%EB%8D%98-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EB%94%A5%EB%8B%A4%EC%9D%B4%EB%B8%8C-42%EC%9E%A5-%EB%B9%84%EB%8F%99%EA%B8%B0-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D
