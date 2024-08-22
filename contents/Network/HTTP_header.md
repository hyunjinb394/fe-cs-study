# 📚 HTTP Header란? 
클라이언트와 서버가 요청 또는 응답으로 부가적인 정보를 HTTP Header를 통해 전송할 수 있습니다. 
HTTP 헤더는 대소문자를 구분하지 않는 이름과 콜론 ':' 다음에 오는 값(줄 바꿈 없이)으로 이루어져있습니다. 
값 앞에 붙은 빈 문자열은 무시됩니다.


## 📖 HTTP General Header 
- 요청 및 응답 메시지 모두에서 사용 가능한 기본적인 항목
- 요청과 응답 모두에 적용되지만 바디에서 최종적으로 전송되는 데이터와는 관련이 없는 헤더
- Date, Connection, Cache-Control 등이 있음

</br>

## 📖 HTTP Request Header 
fetch될 리소스나 클라이언트 자체에 대한 자세한 정보를 포함하는 헤더

### 📍 주요 항목
- Host : 요청하는 호스트에 대한 호스트명 및 포트번호가 필수로 들어감
- User-Agent : 클라이언트 소프트웨어 명칭 및 유저정보
- From
    - 클라이언트 사용자 메일 주소
    - 주로 검색엔진 웹 로봇의 연락처 메일주소를 나타냄
- Cookie : 서버에 의해 Set-Cookie로 클라이언트에게 설정된 쿠키 정보
- Authorization
    - 인증 토큰을 서버로 보낼때 사용하는 헤더
    - 토큰의 종류(Bearer 등) + 실제 토큰문자를 합쳐서 전송
- Origin
    - 서버로 POST 요청을 보낼 때, 요청이 어느 주소에서 시작되었는지 나타냄
    - 요청을 보낸 주소와 서버의 받는 주소가 다르면 CORS 에러가 발생
    - 응답 헤더의 Access-Cotrol-Allow-Origin


</br> 

## 📖 HTTP Response Header
위치 또는 서버 자체에 대한 정보(이름, 버전 등)와 같이 응답에 대한 부가적인 정보를 갖는 헤더 
### 📍 주요 항목
- Server : 서버 소프트웨어 정보
- Set-Cookie : 서버 측에서 세션 쿠키 정보를 설정
- Expires : 응답 컨텐츠가 언제 만료되는지 나타냄
- Age : max-age 시간 내에 얼마나 흘렀는지 초 단위로 알려줌
- ETag : HTTP 컨텐츠가 바뀌었는지 검사할 수 있는 태그
- Access-Cotrol-Allow-Origin
    - 요청을 보내는 주소와 받는 주소가 다르면 CORS 에러가 발생
    - 서버에서는 헤더에 프론트 Origin을 작성해줘야 CORS 에러가 나지 않음
    - 프로토콜, 호스트, 도메인, 포트 중 하나만 달라도 다른 Origin으로 인식됨


</br> 

## 📖 HTTP Entity header
콘텐츠 길이나 MIME 타입과 같이 메시지 바디에 대한 자세한 정보를 포함하는 헤더

### 📍 주요 항목
- Content-Encoding : 미디어 타입을 압축하기 위해서 사용
- Content-Type : 본문의 미디어 타입
- Content-Length : 본문의 길이
- Content-Language : 본문이 대상으로 하는 언어
- Content-Location : 컨텐츠에 접근할 수 있는 위치
- Allow : 리소스가 지원하는 메소드의 집합

</br>

## 🗂️ 참고
