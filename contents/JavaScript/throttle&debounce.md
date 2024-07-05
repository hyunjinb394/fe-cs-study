# 📚 Throttle과 Debounce

## 📖 정의

- DOM 이벤트를 기반으로 실행하는 JS의 성능을 고려하여 이벤트를 제어 & 제한하는 방법
- 과도한 이벤트 횟수의 실행으로 인한 리소스 절약 & 사용자 경험 저하를 방지
  </br>

## 📖 Throttle

- 마지막 함수가 호출된 후 일정 시간이 지나기 전에 다시 호출되지 않도록 함
- (ex) 설정시간 1초 -> 해당 이벤트는 1초동안 최대 한 번만 발생
  </br>

## 📖 Debounce

- 연이어 호출되는 함수들 중 마지막(혹은 제일 처음) 함수만 호출
- (ex) 설정시간 1초 -> 1초동안 아무런 이벤트도 발생하지 않았을 때 마지막 이벤트 실행

## 🔍 예시코드

```js
// <JavaScript>
// 1. nothing
function handleEvent(event) {
  console.log("Input event:", event.target.value);
}

const input = document.createElement("input");
input.type = "text";
input.placeholder = "Type something...";
input.addEventListener("input", handleEvent);

document.body.appendChild(input);

// 2. Throttle
function throttle(func, limit) {
  let lastFunc;
  let lastRan;
  return function (...args) {
    const context = this;
    if (!lastRan) {
      func.apply(context, args);
      lastRan = Date.now();
    } else {
      clearTimeout(lastFunc);
      lastFunc = setTimeout(function () {
        if (Date.now() - lastRan >= limit) {
          func.apply(context, args);
          lastRan = Date.now();
        }
      }, limit - (Date.now() - lastRan));
    }
  };
}

function handleThrottledEvent(event) {
  console.log("Throttled input event:", event.target.value);
}

const inputThrottle = document.createElement("input");
inputThrottle.type = "text";
inputThrottle.placeholder = "Type something...";
inputThrottle.addEventListener("input", throttle(handleThrottledEvent, 1000));

document.body.appendChild(inputThrottle);

// 3. Debounce
function debounce(func, delay) {
  let timeout;
  return function (...args) {
    const context = this;
    clearTimeout(timeout);
    timeout = setTimeout(() => func.apply(context, args), delay);
  };
}

function handleDebouncedEvent(event) {
  console.log("Debounced input event:", event.target.value);
}

const inputDebounce = document.createElement("input");
inputDebounce.type = "text";
inputDebounce.placeholder = "Type something...";
inputDebounce.addEventListener("input", debounce(handleDebouncedEvent, 1000));

document.body.appendChild(inputDebounce);
```

</br>

## 🗂️ 참고

[디바운스와 스로틀 그리고 차이점]
https://webclub.tistory.com/607
