# 📚 리액트의 렌더링 성능 향상을 위해 어떻게 해야 하나요? 


## 📖 리렌더링 성능 분석
- React Developer Tools의 profiler 또는 React의 <Profiler>를 성능측정이 필요한 트리를 감싸서 컴포넌트의 성능을 측정
- 기본적으로 React 18버전은 Automatic Batching으로 렌더링을 최적화
- 비싼 연산이 반복되고 있다면 먼저 로직을 개선하고, 개선이 어렵다면 메모이제이션 기법으로 브라우저에 캐싱해두는 방법 사용

</br>

## 📖 메모이제이션
- 메모리 힙에 데이터를 저장, 가비지 컬렉터가 이를 무시하기 때문에 쓰이지 않는 데이터라도 일정 기간 동안 메모리에 남아 있음
- 트레이드 오프가 있으니, 메모이징은 비용을 따져 최소한으로 사용   


### 📍 react.memo
- 고차컴포넌트로 래핑되어 있음
- props 변화를 인식하기
- state나 context이 변하면 재렌더링
- 복잡하게 중접된 객체로 된 props를 넘기면 얕은 비교를 수행하기 때문에 객체 내부의 변경사항을 감지할 수 없음
- react.memo의 두 번째 인자로 깊은 비교를 수행하는 함수를 넘길 수 있음. 다만, 예상치 못한 오버헤드가 발생할 수 있어서 리액트 공식 문서에도 추천하지 않음


### 📍 useMemo
- **계산한 값**을 메모리에 저장, 
- 인자로는 1. 콜백함수 2. 의존성 배열을 받음
- 콜백함수는 메모할 값을 반환하는 함수
- 의존성 배열은 배열의 값이 변경되는지 판단하여 변경되었으면 콜백함수를 다시 호출해 메모이징된 값을 업데이트

</br> 

### 📍 useCallback
- react.memo의 경우에 콜백함수를 인자로 넘기면 props가 바뀐 것으로 판단
- useCallback은 props로 전달되는 **콜백 함수**를 메모이징
- 인자로는 1. 콜백함수 2. 의존성 배열
- 의존성 배열이 변경되지 않는 이상 콜백함수는 초기화되지 않음


