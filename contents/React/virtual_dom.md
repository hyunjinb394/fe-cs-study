# 📚 Virtual DOM


## 📖 리액트의 렌더링 방식
- state가 변경되면 UI가 새로운 state에 맞게 전체적으로 재렌더링
- state의 변경에 영향 받지 않는 요소들 재렌더링
- 모든 변경 사항을 실제 DOM에 적용 시 성능 문제 발생 
→ `Virtual DOM` 사용

</br>

## 📖 Virtual DOM이란?
- 기본적으로 HTML 요소들은 DOM 트리라는 자료구조로 저장
- 리액트 내부에서는 DOM 트리를 본 떠 만든 `Virtual DOM` 자료구조 사용
- Virtual Dom은 실제 DOM을 추상화 한 것, 실제 DOM과 별개로 메모리에 유지


</br>

![Virtual-DOM](https://velog.velcdn.com/images/aksen5240/post/a0a7c08d-115d-4bc7-b184-4def33fc357b/image.png)

- element가 렌더링될 때, Virtual DOM에 우선 적용
- state 변경 전과 후의 Virtual DOM을 비교한 후 바뀐 부분만 실제 DOM에 반영
- 불필요한 DOM 조작 최소화 및 브라우저 렌더링 성능 최적화


</br> 


## 🗂️ 참고
[Velog - React의 똑똑한 렌더링 방법](https://velog.io/@aksen5240/React의-똑똑한-렌더링-방법-VirtualDOM)