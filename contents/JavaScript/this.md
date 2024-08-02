# 📚 This와 Call, Apply, Bind

## 📖 This가 가지는 값
1. 전역 객체
- 일반함수로 호출된 경우 this는 전역 객체를 가리킴
- 웹 브라우저에서 이 전역객체 this는 window를 가리킴
``` js
function globalThisFn() {
  console.log(this); // window 
}

globalThisFn(); // window 
```

2. 그 메서드를 호출한 객체
- this는 그 메서드를 호출한 객체
```js
const study = {
  name: "ppu-jak",
  greet: function() {
    console.log(`${this.name} 환영해!`); // "ppu-jak 환영해!" 출력
  },
};

study.greet(); // "ppu-jak 환영해!" 출력

```

3. apply, call 또는 bind 메소드를 사용해 호출
- 함수에 첫번째로 전달된 인자값
- 아래 각각의 메소드 설명에 **예시 추가**
4. 생성자 함수에서 this
- new 키워드로 함수 호출 시 함수는 생성자 함수로 동작
- 이때 this는 새로 생성된 객체를 가리킴
```js
class Study {
    constructor(question) {
        this.question = question;
    }
    answer() {
        console.log(`${this.quesiton}에 대한 답은 다음과 같습니다.`);
    }
}

const thisMethod = new Study("this method")
thisMethod.answer(); // "this method에 대한 답은 다음과 같습니다."
```
</br>


**⭐ this가 binding 되는 객체를 변경하고 싶을 때 call, apply, bind를 사용**

</br>

## 📖 Call
### 📍 소주제
- call 메소드는 함수를 호출 / 실행할때 사용
- this로 사용할 객체와 필요한 인자들을 개별적으로 전달
- 함수 첫번째 인자로 a를 호출하면 함수 내부에서 this는 a를 가리킴
- 이후의 인자는 함수의 매개변수로 전달

</br> 

### 📍 Apply
- 함수를 즉시 실행하는 메서드
- 두번째 인자로 배열을 전달 받음


</br> 

### 📍 Bind
- bind 메소드는 특히 이벤트 핸들러나 객체를 this로 지정할때 유용
- 함수 즉시 실행하지 않고 넘겨받은 인수를 바탕으로 새로운 함수를 반환


</br> 

