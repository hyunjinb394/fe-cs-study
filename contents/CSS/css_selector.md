# 📚 CSS Selector

## 📖 CSS Selector의 동작 원리

### 📍 CSS selector란?

- 선택을 해주는 요소
- ID, Class, Tag, Universal(\*) 등

### 📍 동작 원리

- 키 selector(오른쪽)로부터 왼쪽으로 이동
- 요소가 규칙에 적합한지 확인
- 적합하지 않으면 멈춤

</br>

## 📖 선택자 우선순위

### 📍 CSS 원천 소스(Original Source)

- 제작자(author) 원천 소스 : 웹 사이트 제작자가 지정하는 자신의 페이지 스타일
- 사용자(user) 원천 소스 : 사용자가 직접 정하는 자신이 사용할 스타일
- 사용자 도구(user agent) 원천 소스: 웹 브라우저 자체에 지정된 기본 스타일
- 원천 소스 우선 순위: !important사용자 > !important 제작자 > 제작자 > 사용자 ? 사용자도구

### 📍 CSS 명시도(Specificity) 계산법

- !important > id[100] > class[10] > tag[1] > \*[0]
- 선택자 갯수당 각 점수 합연산, 점수가 높을수록 우선시 됨
- 가상 엘리먼트는 무시
- (예시) li#selector1{} => li(tag) 1점 + #selector(Id) 100점 = 101점

### 📍 마지막에 지정된 스타일을 우선 적용

- 스타일 우선순위가 같거나, 계산 방법이 없는 경우
- (예시) 자손선택자 vs 자식 선택자

</br>

## 🔍 예시코드

```CSS
/* 전체 선택자 */
/* <CSS> */
* { margin: 0; text-decoration: none; }


/* 태그 선택자 */
/* CSS */
p { background: yellowgreen; color: darkgreen; }

<!-- HTML -->
<p>태그 선택자(Type Selector)</p>
<div>태그 선택자(Type Selector)</div>


/* 클래스 선택자 */
/* CSS */
.class1 { background: yellowgreen; color: darkgreen; }
div.class2 { background: darkgreen; color: yellowgreen; }

<!-- HTML -->
<p class="class1">클래스 선택자(Class Selector)</p>
<p class="class2">클래스 선택자(Class Selector)</p>
<div class="class2">클래스 선택자(Class Selector)</div>


/* ID 선택자 */
/* CSS */
#id1 { background: yellowgreen; color: darkgreen; }
div#id2 { background: darkgreen; color: yellowgreen; }

<!-- HTML -->
<p id="id1">ID 선택자(ID Selector)</p>
<p id="id2">ID 선택자(ID Selector)</p>
<div id="id2">ID 선택자(ID Selector)</div>


/* 복합 선택자 */
/* CSS */
/* 하위 선택자 */
section ul { border: 1px dotted black; }

/* 자식 선택자 */
section>ul { border: 1px dotted black; }

/* 인접 형제 선택자 */
h1+ul { background: yellowgreen; color: darkgreen; }

/* 일반 형제 선택자 */
h1~ul { background: darkgreen; color: yellowgreen; }


/* 속성 선택자 */
/* CSS */
/* E[attr]형식 */
a[href] { background: yellowgreen; color: black; }

/* E[attr="val"]형식 */
input[type="text"] { width: 150px; border: 1px solid #000; }

/* E[attr$="val"]형식 */
a[href$=".xls"] { background: darkgreen; }

<!-- HTML -->
<a href="one.html">E[attr]형식</a>
<input type="text" name="name">
<a href="one.xls">E[attr$="val"]형식</a>


/* 가상 클래스 선택자 */

/* 그 외의 선택자
언어선택자
부정선택자
목적선택자
UI요소 상태 선택자
가상 엘리먼트 선택자 ... */
```

</br>

## 🗂️ 참고
