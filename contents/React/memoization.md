# 📚 Memoization


## 📖 메모이제이션이란?
- 컴퓨터 프로그램이 동일한 계산을 반복적으로 해야할 때, 이전에 계산한 값을 메모리에 저장
- 중복적인 계산을 제거하여 전체적인 실행 속도를 빠르게 해주는 기법
- 동적계획법 (DP: Dynamic Programming)의 핵심이 되는 기술

</br>

## 📖 리액트에서의 활용법
### 📍 useMemo
- 의존성 배열 안에 있는 값이 변경 될 때만 콜백 함수를 다시 호출하여 메모리에 저장된 값 업데이트
- 의존성 배열이 비어있는 경우 마운트 될 때만 계산하고 메모이제이션 된 값 불러옴
- 함수의 연산량이 많을 때, 이전 결과 값을 재사용하는 목적
</br>

## 🔍 예시코드
```js
const memorizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

</br>

### 📍 React.memo
- 컴포넌트의 props가 바뀌지 않았다면, 리렌더링하지 않도록 설정

## 🔍 예시코드
```js
const Component = React.memo((props) => {
	return (/* 컴포넌트 렌더링 코드 */)}
);
```

</br>

### 📍 useCallback
- 컴포넌트가 렌더링 될 때마다 내부적으로 사용된 함수가 새롭게 생성되는 경우 사용
- 함수가 재생성되는 것을 방지하기 위한 목적

## 🔍 예시코드
```js
const [name, setName] = useState('');
const [age, setAge] = useState(0);
const onSave = useCallback(() => saveToServer(name, age), [name, age]);
```

</br>


## 🗂️ 참고
[Velog - 메모이제이션](https://velog.io/@hsk10271/TIL-30)