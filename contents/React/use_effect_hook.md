# 📚 useEffect


## 📖 useEffect 란?
- 컴포넌트가 렌더링 될 때 마다 특정 작업을 실행할 수 있도록 해주는 React hook
- mount / unmount / update 되었을 때 특정 작업 처리
- 클래스형 컴포넌트에서 사용 가능했던 `생명주기 메소드`를 함수형 컴포넌트에서 사용 

</br>

![useEffect](https://blog.kakaocdn.net/dn/J6VPG/btreOs3fnFB/J3PD4pk5vQfiHtSw0BKA51/img.png)

</br>

## 🔍 예시코드
### 📍 mount 되었을 때 (기본 형태)
```js
import { useEffect } from 'react';

useEffect(() => {
	console.log('마운트 되었습니다 :)');
},[]); 
```
- `useEffect(function, deps)` 형태로 사용
- deps 자리를 비울 시, 맨 처음 렌더링 그리고 재렌더링 될 때마다 실행
- deps 자리에 빈 배열 넣을 시, 맨 처음 렌더링 시 실행
- deps 자리에 특정 값 넣을 시, 맨 처음 렌더링 시 그리고 해당 값 변경될 때 실행

</br>

### 📍 unmount 될 때 (clean up 함수 반환)
```js
import { useEffect } from 'react';

useEffect(() => {
	console.log('마운트 되었습니다 :)');
	
	return () => {
	console.log('언마운트 되었습니다 :(');
	
	};
},[]); 
```
- 기존 useEffect 함수 내에 `return 함수` 작성
- deps 자리에 빈 배열 넣을 시, 언마운트 될 때 실행
- deps 자리에 특정 값 넣을 시, 언마운트 될 때와 특정 값 업데이트 직전 실행

</br>

### 📍 사용 규칙

- useEffect 안에서 사용하는 상태나 props가 있다면 deps 자리에 기입

</br>


## 🗂️ 참고
[Tistory - React Hooks : useEffect()함수](https://xiubindev.tistory.com/100)
</br>
[벨로퍼트와 함께하는 모던리액트 - 16](https://react.vlpt.us/basic/16-useEffect.html)