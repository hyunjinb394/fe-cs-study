# 📚 Progressive Rendering


## 📖 Progressive Rendering 이란?
- 점진적 렌더링
- 서버에서 중요한 콘텐츠들 렌더링 후, 클라이언트로 스트리밍
- 중요하지 않은 콘텐츠들이 렌더링되면 다시 클라이언트의 웹 페이지로 스트리밍하는 기술
- SSR과 CSR의 장점을 모두 가짐

</br>

## 📖 SSR 과 CSR
### 📍 SSR
![SSR_img](https://miro.medium.com/v2/resize:fit:720/format:webp/1*yD9-0iK2Ul8cAnOvIbwKng.png)
- 웹 사이트가 서버에서 렌더링 되는 것

- 장점
  - CSR 대비 빠른 첫 로딩을 제공할 수 있음
  - SEO 가능
- 단점
  - 페이지를 이동할 때마다 서버를 거쳐야 하므로 로딩 속도 및 성능 저하

</br> 

### 📍 CSR
![CSR_img](https://miro.medium.com/v2/resize:fit:720/format:webp/1*vKrzuL0dy60XAI8GS521pA.png)
- 웹 사이트가 클라이언트에서 렌더링 되는 것

- 장점
  - 브라우저가 렌더링을 담당하므로 서버 트래픽 감소
  - 새로고침이 발생하지 않아 네이티브 앱과 비슷한 사용자 경험
- 단점
  - SSR 대비 많은 초기 다운로드와 추가 렌더링으로 초기 로딩 느림
  - SEO에 대한 추가 보완 작업 필요

</br>

## 🗂️ 참고
[Medium - Progressive Rendering — The Key to Faster Web](https://medium.com/the-thinkmill/progressive-rendering-the-key-to-faster-web-ebfbbece41a4#:%7E:text=Progressive%20Rendering%20is%20the%20technique,the%20whole%20page%20to%20rendered)