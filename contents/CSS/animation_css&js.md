# 📚 CSS 애니메이션

## 📖 CSS 애니메이션의 특징

### 📍 장점

- 좋은 성능: GPU를 활용해 렌더링 되므로, 복잡한 애니메이션에서도 좋은 성능 제공
- 요소에 직접 애니메이션을 지정하기 때문에 알아보기 쉬움
- 외부 라이브러리를 필요로 하지 않음
- 효율적: 메인스레드가 아닌, Compositor Thread에서 그려짐

### 📍 단점

- 제한적인 기능: CSS는 프로그래밍 언어가 아니라, 복잡한 상호작용이나 로직을 다루기 어려움
- 복잡한 애니메이션을 구현하려면 코드가 복잡하고 관리가 어려워짐

</br>

## 📖 JS 애니메이션의 특징

### 📍 장점

- 브라우저 호환성이 좋음
- 세밀한 구성: 요소의 스타일이 변하는 순간마다 제어 가능
- GPU를 통한 하드웨어 가속 제어 가능
- RAF(RequestAnimationFrame)API를 통해 60fps 유지 가능

### 📍 단점

- 계속해서 요소의 위치를 재계산하기 때문에, 60fps가 유지되지 않음
- 복잡성: CSS에 비해 애니메이션을 작성하고 이해하는 데 더 많은 시간과 노력이 들 수 있음
  </br>

## 📖 브라우저 렌더링 원리

### 📍 브라우저 렌더링 과정

- Layout(Reflow): 브라우저가 요소의 위치와 크기를 계산
- Paint(Repaint): 브라우저가 요소의 색상, 텍스트, 이미지 등을 그림
- Composite: 브라우저가 각 요소를 올바른 순서로 쌓아 최종 화면을 만듦

### 📍 웹페이지의 성능에 영향을 미치는 부분

- Reflow: 요소의 크기나 위치가 변경될 때 브라우저가 레이아웃을 다시 계산하는 것.
- Repaint: 요소의 색상이나 텍스트가 변경될 때 브라우저가 요소를 다시 그리는 것.

</br>

## 🔍 예시코드

```CSS
/* <CSS> */
@keyframes move {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(100px);
  }
}

.myElement {
  animation: move 2s infinite;
}
```

```JS
// <JavaScript>
let start;
const element = document.getElementById("MyElement");

function step(timestamp) {
  if (start === undefined)
    start = timestamp;
  const elapsed = timestamp - start;

  element.style.transform = 'translateX(' + Math.min(0.1 * elapsed, 100) + 'px)';

  if (elapsed < 2000) {
    window.requestAnimationFrame(step);
  }
}

window.requestAnimationFrame(step);
```

</br>

## 🗂️ 참고
