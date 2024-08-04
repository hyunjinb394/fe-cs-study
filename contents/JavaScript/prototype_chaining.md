# 📚 Protoytpe & Prototype Chaining


## 📖 Prototype 이란?
- 자바스크립트 객체가 서로 속성을 상속받는 메커니즘
- 자바스크립트에서 어떤 객체는 반드시 부모 객체를 가지는데 이 객체가 `프로토 타입`
- 자식 객체는 `__proto__` 접근자를 통해 자신의 프로토 타입에 접근
- 자식 객체는 부모 객체의 모든 속성을 사용 가능

</br>

## 📖 Prototype Chaining
- 자식 객체에 없는 속성이나 메서드 호출 시, `부모 객체에서 탐색`
- 부모 객체에도 존재하지 않는다면 해당 과정 반복
- 모든 객체의 최상위 객체는 Object.prototype, 이 객체의 부모는 `null`

</br> 

## 🔍 예시 코드
```js
const obj = {
  a : 1,
  b : function () {}
}

console.log(obj.__proto__=== Object.prototype); // true
console.log(Object.prototype.__proto__ === null); // true
```

</br> 

![prototype1](https://blog.kakaocdn.net/dn/44Htf/btrB7Ojbi1b/lj5wk0vY36VEridj1FVAV0/img.png)

- [[Prototype]]은 모든 객체에 존재하는 내부 슬롯
- 프로토타입 체인 무한 루프 방지 위해 직접 접근 X

</br>

## 🗂️ 참고
[Tistory - [JavaScript] 프로토타입(Prototype)](https://charles098.tistory.com/170)