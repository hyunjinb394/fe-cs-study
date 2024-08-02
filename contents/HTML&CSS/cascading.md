# 📚 Cascading
 

## 📖 Cascading 이란?
- css는 `cascading style sheet`의 약자
- 위에서 아래로 떨어지는 이라는 사전적 의미
- `스타일 우선순위`, `스타일 상속`의 두 가지 원칙을 통해 적용 요소 결정

</br>

## 📖 스타일 우선순위
### 📍 중요도 (Importance)
- 선언된 위치에 따라 우선순위 매김
- `작성자 스타일 시트 > 사용자 스타일 시트 > 사용자 도구 스타일 시트` 순 중요도 높음
- `!important` 키워드 사용하여 의도적으로 중요도 높일 수 있음

</br> 

### 📍 명시도 (Specificity)
- 셀렉터가 가리키는 것의 구체성에 따라 우선순위 매김
- `인라인 > id > class > 태그` 순 명시도 높음
- 즉, 지정하는 범위가 좁을수록 명시도가 높음

</br> 

### 📍 코드 순서 (Source Order)
- 코드를 작성한 순서에 따라 우선순위 매김
- `가장 마지막에 작성된 속성을 최우선`으로 적용

</br> 

## 📖 스타일 상속
- 태그들이 어떻게 포함되었는지에 따라 스타일 적용 결정
- 상속 요소는 `부모 요소의 스타일을 자식 요소가 따라가는 것`

</br> 


## 🗂️ 참고
[MDN - Cascade & Inheritance](https://developer.mozilla.org/ko/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance)