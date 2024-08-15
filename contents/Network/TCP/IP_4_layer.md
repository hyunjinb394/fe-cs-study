# 📚 TCP/IP 4 LAYER

## 📖 TCP/IP 모델이란?

- TCP 프로토콜과 IP 프로토콜은 오늘날 인터넷 통신의 기반
- 이 주요 프로토콜들과 주로 함께 활용되는 프로토콜의 묶음으로써 만들어진 네트워크 참조 모델
- OSI 모델에 비해 좀 더 실무적이며 단순화 된 모델

## 📖 TCP/IP 계층 별 특징

### 📍 1계층 - 네트워크 액세스 계층 (Network Access Layer)

- OSI 모델의 **데이터링크 계층**과 유사
- **같은 네트워크 안**에서 물리적인 데이터 전송을 담당
- 데이터 단위는 `Frame`, 전송 주소는 `MAC`
- 노드 간의 신뢰성 있는 데이터 전송 및 기본적인 에러 검출
- 대표적인 예시는 **Ethernet**으로 LAN이나 패킷망 등에 사용됨

### 📍 2계층 - 인터넷 계층 (Internet Layer)

- OSI 모델의 **네트워크 계층**과 유사
- **서로 다른 네트워크 간**의 통신 수행
- 데이터 단위는 `패킷`, 전송주소는 `IP`
- 라우터의 라우팅 테이블을 통해 데이터 전송을 위한 최적의 경로를 찾아 전송
- 대표적인 프로토콜로는 **IP, ARP, RARP**가 있음

### 📍 3계층 - 전송 계층 (Transport Layer)

- OSI 모델의 **전송 계층**과 유사
- **통신 노드 간**의 연결을 제어
- 데이터 단위는 `세그먼트`, 전송 주소는 `port`
- 신뢰성 있는 데이터 전송을 담당
- 대표적인 프로토콜로는 **TCP, UDP**가 있음

### 📍 4계층 - 응용 계층 (Application Layer)

- OSI 모델의 **세션, 표현, 응용 계층을 합친 것**과 유사
- **응용 프로그램들 간**에 데이터를 교환
- 데이터 단위는 `data` 혹은 `message`
- 대표적인 프로토콜로는 **HTTP, FTP, SSH**가 있음

</br>

## 🗂️ 참고

[혼자 공부하는 네트워크 – 네트워크 참조 모델
https://www.youtube.com/watch?v=H1Z4tnzs-HA&list=PLVsNizTWUw7HfOCgvlfHIDPPo3TE-2iQM&index=9]

[TCP/IP 4계층에 대하여]
https://velog.io/@dyunge_100/Network-TCPIP-4%EA%B3%84%EC%B8%B5%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC

[TCP/IP 4계층(TCP/IP 4 Layer)]
https://hahahoho5915.tistory.com/15
