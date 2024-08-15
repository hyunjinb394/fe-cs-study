# 📚 OSI 7 LAYER

## 📖 OSI 모델이란?

- 네트워크 프로토콜의 통신 구조를 7단계로 나눈 모델
- 네트워크 통신 과정을 단계 별로 파악할 수 있게 해줌

## 📖 OSI 모델의 유용성

- 통신의 흐름을 한 눈에 알아보기 쉬움
- 사람들이 이해하기에 쉬움
- 특정 단계에 이상 발생 시, 해당 단계만 고치면 되어 용이

## 📖 OSI 계층 별 특징

![image.png](https://cf-assets.www.cloudflare.com/slt3lc6tev37/6ZH2Etm3LlFHTgmkjLmkxp/59ff240fb3ebdc7794ffaa6e1d69b7c2/osi_model_7_layers.png)

<br/>

### 📍 1계층 - 물리 계층 (Physical Layer)

![image.png](https://cf-assets.www.cloudflare.com/slt3lc6tev37/1HQ1W5P4XAinIdM37DTu4U/900ccdceda346baf03ce8b9f977d2974/osi_model_physical_layer_1.png)

- 전기적, 기계적, 기능적 특성 이용해 통신 케이블로 `데이터 전송`
- 사용되는 통신 단위는 `비트` (1과 0, 전기적으로 On, Off 상태)
- 데이터를 전달만 할 뿐, 데이터의 정보에 대해 신경쓰지 않음
- **통신 케이블, 리피터, 허브**가 대표적 장비

<br/>


### 📍 2계층 - 데이터 링크 계층 (Data Link Layer)

![image.png](https://cf-assets.www.cloudflare.com/slt3lc6tev37/3TLHavXiotb9ayyZFKECf3/9456d1c431cd71ceea7f4b407f076f11/data_link_layer_osi_model.png)

- 물리 계층을 통해 송수신되는 정보의 `에러검출, 재전송, 흐름제어`
- `MAC 주소`를 통해 통신
- 사용되는 통신 단위는 `프레임`
- **브리지, 스위치** 등이 대표적 장비

<br/>

### 📍 3계층 - 네트워크 계층 (Network Layer)

![image.png](https://cf-assets.www.cloudflare.com/slt3lc6tev37/3g2Hv0frHsql5SFauJL5EG/d8cede7b6a780e63413bd86de9eee7f9/osi_model_network_layer_3.png)

- `경로 설정(라우팅)`, `주소 부여(IP)`, 경로에 따른 `패킷 전달`
- 대표적인 장비는 **라우터**, 2계층의 장비 중 스위치에 라우팅 기능을 장착한 **Layer 3 스위치**도 존재

<br/>

### 📍 4계층 - 전송 계층 (Transport Layer)

![image.png](https://cf-assets.www.cloudflare.com/slt3lc6tev37/3OlO75NcADGL3SmEADFDqd/723b8c7639c4e2e6b4febcbe7fd36e0e/osi_model_transport_layer_4.png)

- `패킷 오류검출 및 복구, 흐름제어, 중복검사, 재전송`
- `TCP/UDP 프로토콜` 사용

- **TCP 프로토콜**
    - 신뢰성 제공 (Reliable) : 패킷 손실, 중복, 순서변경 등이 없도록 보장
    - 연결지향적 (Connection-oriented) : 연결성 회선을 통해 통신
- **UDP 프로토콜**
    - 비연결성, 신뢰성 낮은, 순서화되지 않은 Datagram 서비스 제공
    - 실시간 응용 및 멀티캐스팅 가능
    - TCP 대비 단순한 헤더

<br/>

### 📍 5계층 - 세션 계층 (Session Layer)

![image.png](https://cf-assets.www.cloudflare.com/slt3lc6tev37/29mRrgK22AqJVlg2MMlD86/34d8f4071b6cc0d3b03c93f55e4d89b7/osi_model_session_layer_5.png)

- 양 끝단의 응용 프로세스가 통신을 관리하기 위한 방법 제공
- **동시 송수신 방식(duplex), 반이중 방식(half-duplex), 전이중 방식(full-duplex) 통신**
- 통신을 위한 `세션 확립, 유지, 중단` (운영체제가 수행)

<br/>

### 📍 6계층 - 표현 계층 (Presentation Layer)

![image.png](https://cf-assets.www.cloudflare.com/slt3lc6tev37/19L86neKKT8srUkOSe4rf7/ff4c91c94a1790651df7b48433913f59/osi_model_presentation_layer_6.png)

- 데이터 표현이 상이한 응용 프로세스의 독립성 제공, `암호화`
- `사용자의 명령어를 완성 및 결과 표현, 압축`

<br/>

### 📍 7계층 - 응용 계층 (Application Layer)

![image.png](https://cf-assets.www.cloudflare.com/slt3lc6tev37/2rcDKpr4WLqoyAZ7GDKkyJ/7cab96402de7ac5465b86e617da3da4e/osi_model_application_layer_7.png)

- 최종 목적지로서 **HTTP, FTP, SMTP, POP3, IMAP, Talnet과 같은 프로토콜 존재**
- 응용 프로세스와 직접 관계하여 일반적인 응용 서비스 수행
- `네트워크 소프트웨어 UI 부분, 사용자의 입출력(I/O) 부분`

- **HTTP 프로토콜**
    - 웹 상에서 웹 서버 및 웹 브라우저 상호 간의 데이터 전송을 위한 응용 계층 프로토콜
    - 하이퍼텍스트 형태의 문서를 전달, 이미지, 비디오, 음성 등 모든 형식의 데이터 전송 가능
    - 요청 및 응답의 구조 (클라이언트/서버 모델로 동작)
    - 메세지 교환 형태의 프로토콜 (HTTP 메세지를 주고받으며 통신)
    - 트랜잭션 중심의 비연결성 프로토콜 (Connectionless, Stateless)
    - 전송 계층 프로토콜 및 사용 포트 번호 (TCP , 80번 포트 사용)

    
- **HTTP 트랜잭션**
    - 웹 클라이언트와 웹 서버 간의 단일 요청과 그에 대한 응답으로 이루어진 통신 단위
    - HTTP 트랜잭션은 클라이언트가 서버에 요청을 보내고, 서버가 그 요청에 대해 응답을 반환하는 한 쌍의 작업으로 구성
    - HTTP 트랜잭션은 독립적이며, 각 트랜잭션이 완료되면 다음 트랜잭션과는 별도로 처리
    - HTTP 자체는 상태를 유지하지 않는 연결이 없는(connectionless) 프로토콜이기 때문에, 각 응답 쌍은 서로 간에 의존적이지 않음
    - 주로 웹 페이지의 요소(HTML, 이미지, CSS, JS 등)를 가져오거나 서버와 데이터를 주고받기 위한 통신 단위로 사용
    
<br/>

## 🗂️ 참고

[CLOUDFLARE - OSI 모델이란?](https://www.cloudflare.com/ko-kr/learning/ddos/glossary/open-systems-interconnection-model-osi/)

[Tistory - OSI 7 계층이란?, OSI 7 계층을 나눈 이유](https://shlee0882.tistory.com/110)