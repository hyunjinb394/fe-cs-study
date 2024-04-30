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
var inside1 = $(".inside-1");
var thing1 = $(".thing-1");
var count1 = $(".count-1");
inside1.on("scroll", function () {
  thing1.css("top", inside1[0].scrollTop);
  count1.html(parseInt(count1.html()) + 1);
});

// 2. Throttle
var inside2 = $(".inside-2");
var thing2 = $(".thing-2");
var count2 = $(".count-2");
inside2.on(
  "scroll",
  _.throttle(function () {
    thing2.css("top", inside2[0].scrollTop);
    count2.html(parseInt(count2.html()) + 1);
  }, 150)
);

// 3. Debounce
var inside3 = $(".inside-3");
var thing3 = $(".thing-3");
var count3 = $(".count-3");
inside3.on(
  "scroll",
  _.debounce(function () {
    thing3.css("top", inside3[0].scrollTop);
    count3.html(parseInt(count3.html()) + 1);
  }, 100)
);
```

</br>

## 🗂️ 참고

https://webclub.tistory.com/607
