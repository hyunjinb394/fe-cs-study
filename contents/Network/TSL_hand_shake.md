# 📚 TLS HandShake 진행 과정
웹 서버에 데이터를 전송할때 암호화해서 정보의 기밀성을 확보하기 위해서 HTTPS 프로토콜이 만들어짐    
HTTPS는 SSL/TLS 구조로 구현됨


## 📖 SSL / TLS 란?
- 통신을 암호화해서 제삼자가 통신 내용을 훔쳐보거나 조작할 수 없게하는 기술
- 현재 사용되는 기술은 SSL이아닌 **TLS**, 명칭이 변경됨
- SSL인증서를 발급해야 HTTPS 웹사이트를 이용 가능
- SSL을 사용해 데이터를 암호화하고 도메인 소유를 증명할 수 있음

</br>

## 📖 TLS 서비스
### 📍 암호화
- 데이터를 타인이 알아보 수 없도록 만듦
- TLS 핸드셰이크 방식에서 **공개키 암호화**를 사용
- 서로에 대한 정보 없이도 비밀키를 협상하거나, 암호화 되지 않은 채널에서 이 절차를 수행 가능

</br> 

### 📍 인증
- 제공된 식별 정보의 진위 여부 확인
- 핸드셰이크를 진행할때 커넥션 피어는 자신의 식별정보를 인증
- 클라이언트에게 서버의 정체를 확인 시켜줌으로써 서버의 이름과 IP주소를 도용 및 사칭하는 Spoofing을 막음
- 서버 또한 클라이언트의 정체를 확인 가능

</br> 

### 📍 무결성
- 메시지가 무단으로 변경, 위조되었는지 확인
- 자체적으로 모든 메시지에 인증코드(MAC)을 부여
- 수신자는 MAC 값을 통해서 메시지의 무결성을 확인

</br> 


## 📖 TLS Hand Shake
### 📍 과정
1. **암호화 터널 형성** : 클라이언트와 서버는 TLS 프로토콜의 버전과 암호 방식을 합의, 필요한 경우 인증서 확인
2. **TCP의 3-Way 핸드셰이크 완료**
3. **Client Hello** : TCP 연결 완료시 클라이언트의 TLS 프로토콜의 버전, 암호화 방식, Session ID 등을 일반 텍스트로 전송
4. **Server Hello -> Server Certificate -> Hello Done**
    - Client Hello에 대한 응답
    - 클라이언트가 제시한 TLS 버전, 암호화 방식을 선택 후 정보를 인증서에 첨부해 클라이언트에게 전송
    - 서버의 인증서를 클라이언트에게 보내고 클라이언트는 서버의 인증서가 무결한지 검증
5. **Client Key Exchange**
    - 새 대칭키를 만들어 서버의 공개키로 암호화
    - 클라이언트는 키 교환에 필요한 정보를 서버에 제공
    - 난수를 조합해 생성한 pre-master secret 값을 공개키로 암호화해서 전송
    - 서버는 개인키로 난수를 복호화 가능
    - 이 값을 통해서 세션에 사용될 키를 생성
6. **Server & Client : Change Cipher Spec**
    - 이제부터는 모든 패킷은 협상된 알고리즘과 키를 통해서 암호화한다는 것을 알리는 메시지
7. **Server & Client : Finished**
    - 핸드셰이크를 성공적으로 마치고 종료

</br>

### 📍 TLS 세션
- 매번 연결시 마다 핸드셰이크 과정을 진행하는 것은 비효율적
- TLS 핸드셰이크는 추가 레이턴시와 연산처리 비용 증가와 같은 성능저하를 일으킴
- 문제 해결을 위해 TLS는 최초 핸드셰이크 과정 진행 후 Session ID를 가지고 패킷 전송을 진행
- 서버에서 받은 Session ID가 유효하다면 동일한 Session ID를 다시 전송
- Session ID를 통해서 왕복 시간을 줄이고, 공개키 협상 시 발생하는 오버헤드를 없앨 수 있음
- 다만 서버가 모든 클라이언트마다 세션 캐시를 생성하고 관리해야함


</br>

## 🗂️ 참고
[네트워킹과 웹 성능 최적화 기법 - 4장 전송 계층 보안](https://www.yes24.com/Product/Goods/22884121)

[TLS-HandShake는 어떻게 진행되는가?](https://sunrise-min.tistory.com/entry/TLS-Handshake%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%A7%84%ED%96%89%EB%90%98%EB%8A%94%EA%B0%80)