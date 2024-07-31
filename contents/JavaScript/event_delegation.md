# 📚 Event Delegation


## 📖 Event Delegation 이란?
- 비슷한 방식으로 여러 요소를 다뤄야 할 때 사용
- 요소마다 핸들러를 할당하지 않고, 공통 조상 하나에만 할당

- 장점
  - 초기화가 단순해지고, 메모리 절약
  - 요소 추가 / 제거 시 핸들러 추가 / 제거 필요 없어 코드 간결
  - innerHTML 등의 기능으로 DOM 수정 용이 
- 단점
  - 사용하려면 반드시 이벤트 버블링 전제
  - 낮은 레벨에 할당된 핸들러에는 event.stopPropagation() 사용 불가능
  - 모든 하위 요소에서 이벤트에 응답해야 하므로 CPU 작업 부하 증가 가능성

</br>

## 📖 Event Bubbling & Capturing
### 📍 표준 DOM 이벤트 흐름
1. 캡쳐링 단계 : 이벤트가 하위 요소로 전파되는 단계
2. 타깃 단계 : 이벤트가 실제 타깃 요소에 전달되는 단계
3. 버블링 단계 : 이벤트가 상위 요소로 전파되는 단계

![Event Bubbling & Capturing](https://velog.velcdn.com/images/line_jeong32/post/37a48b42-b14a-45c6-842e-3510b72b9dd3/image.png)


### 📍 Bubbling
- 최하위 요소부터 부모 요소를 거슬러 올라가며 발생하는 모습이 거품과 닮아 `버블링`
- 타깃 이벤트부터 <html> 요소를 거쳐 document 객체까지 각 노드에서 발생
- 몇몇 객체는 window 객체까지 거슬러 올라감
- 버블링 중단 명령은 event.stopPropagation() 메서드 이용
- 상기 메서드 사용 시 분석이 되지 않는 `dead zone` 형성되므로 주의

</br> 

### 📍 Capturing
- 최상위 요소부터 하위 요소를 거슬러 내려가며 발생
- 확인 위해 addEventListner() capture 옵션 true 설정

</br> 

## 🗂️ 참고
[JAVASCRIPT INFO - 버블링과 캡쳐링](https://ko.javascript.info/bubbling-and-capturing)