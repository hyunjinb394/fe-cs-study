# 📚 script 태그에서 Async와 Defer의 차이
Script 태그의 Async, Defer 속성이 필요한 이유와 속성 간의 차이

## 📖 DOM이 Script 태그를 만나면?
- DOM이 생성될때 Script 태그를 만나면 DOM 생성을 멈추고 Script를 실행
- Script를 받고 실행할때까지 아래에 선언된 `DOM 요소는 대기`
- DOM 요소들이 대기하게 되면 해당 DOM 요소에 접근 할 수 없고 페이지가 Block되어 버림
- UX 향상을 위해서 Script를 다운로드 할때 DOM 생성을 막지 않는 async와 defer 속성이 필요함

</br>

## 📖 async와 defer
### 📍 async
- Script를 백그라운드에서 다운로드
- Script 다운로드 되는 과정에서는 DOM 렌더를 차단하지 않도록 보장
- 하지만 Script를 실행할때는 DOM 실행을 멈춤
- Script 해석에 걸리는 시간은 Script의 오버헤드에 달려있음
- 즉, async는 `선언된 순서와 실행 순서가 다름`
- DOM이 모두 로드된 경우 발생하는 DOMContentLoaded 이벤트 콜백으로 로드를 보장할 수 없음
- async 속성은 Script가 독립적인 역할을 하는 Goolge Analytics 같은 서드 파티 Script 등을 통합할때 유용
- DOM에 직접 접근하지 않는 Script일때 async가 효과적
- async Script는 다른 스크립트에 `의존적이지 않은 스크립트를 독립적으로 실행`할때 효과적

</br> 

### 📍 defer
- Script를 백그라운드에서 다운로드
- Script의 다운로드가 끝나더라도 DOM 생성이 완료 된 이후 Script 실행
- Script가 모두 실행되면 DOMContentLoaded 이벤트 발생
- Script 무게에 상관없이 `순서를 지키며 실행`됨 
- Script 파일끼리 의존성이 있는 경우에도 사용

</br> 


</br>

## 🗂️ 참고
[스크립트의 실행 시점을 조절하는 Async와 Defer 속성](https://wormwlrm.github.io/2021/03/01/Async-Defer-Attributes-of-Script-Tag.html)   

[script 태그의 async , defer 속성] (https://shorturl.at/iqzLY)   

