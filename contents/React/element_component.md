# 📚 Element & Component


## 📖 전통적인 UI 모델에서의 인스턴스 관리
- 컴포넌트를 생성하기 위해 클래스를 만들어 선언
- 컴포넌트의 여러 인스턴스가 스크린에 표시
- 각각의 인스턴스는 프로퍼티와 로컬 상태를 지님
- 새로운 정보(그 DOM 노드와 자식 컴포넌트의 인스턴스에 대한 참조)의 수동 업데이트 불편함

## 🔍 예시코드
```js
class Form extends TraditionalObjectOrientedView {
  render() {
    // Read some data passed to the view
    const { isSubmitted, buttonText } = this.attrs;

    if (!isSubmitted && !this.button) {
      // Form is not yet submitted. Create the button!
      this.button = new Button({
        children: buttonText,
        color: 'blue'
      });
      this.el.appendChild(this.button.el);
    }

    if (this.button) {
      // The button is visible. Update its text!
      this.button.attrs.children = buttonText;
      this.button.render();
    }

    if (isSubmitted && this.button) {
      // Form was submitted. Destroy the button!
      this.el.removeChild(this.button.el);
      this.button.destroy();
    }

    if (isSubmitted && !this.message) {
      // Form was submitted. Show the success message!
      this.message = new Message({ text: 'Success!' });
      this.el.appendChild(this.message.el);
    }
  }
}
```

</br>

## 📖 리액트 요소(Element)란?
- 전통적인 UI 모델에서의 문제를 해결하기 위해 등장
- 실제 인스턴스가 아니며, 스크린에서 보고자 하는 것을 리액트에 알리는 방식
- 리액트 애플리케이션의 가장 작은 단위로, 화면에 표시되는 내용을 기술
- JSX 문법으로 작성한 요소는 결국 자바스크립트 객체로 변환
</br>

## 🔍 예시코드
```js
import ReactDOM from 'react-dom/client';

const element = <h1>안녕 리액트</h1>;
console.log(element);

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(element);
```
- element 변수는 리액트 엘리먼트로 ReactDOM.render 함수의 argument로 전달

</br>

## 📖 리액트 컴포넌트(Component)란?
- 리액트 엘리먼트들을 조합하고 재사용 가능한 코드 블록을 형성
- 리액트 엘리먼트를 함수 형태로 만들어내면 JSX 문법 작성 시, 커스텀 태그 처럼 활용 가능
</br>

## 🔍 예시코드
```js
import ReactDOM from 'react-dom/client';

function Hello() {
	return <h1>Hi React!</h1>;
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
	<>
		<Hello />
		<Hello />
		<Hello />
	</>
);
```
- 화면 구성이나 목적에 따른 코드 세분화
- 반복적인 개발 감소
- 유지 보수 및 오류 수정 용이


</br>


## 🗂️ 참고
[Velog - 엘리먼트와 컴포넌트](https://velog.io/@aksen5240/%EC%97%98%EB%A6%AC%EB%A8%BC%ED%8A%B8Element%EC%99%80-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8Component-%EB%A6%AC%EC%95%A1%ED%8A%B8-%EC%82%AC%EC%9A%A9%EC%9D%84-%EC%9C%84%ED%95%9C-%ED%95%B5%EC%8B%AC-%EA%B0%9C%EB%85%90)
