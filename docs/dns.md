# DNS

## DNS(Domain Name Service)란?
- 도메인 네임 서비스는 호스트의 도메인 이름을 호스트의 네트워크 주소로 바꾸거나 혹은 그 반대로 변환을 하기 위해 개발되었다

## DNS 구성요소

### 도메인 네임 스페이스 : DNS가 저장 관리하는 계층적 구조
- 도메인 이름 저장을 분산한다.

![image](https://github.com/JoEunSae/Internship/assets/83803199/5632bf04-a34e-47bc-9ef1-b7e12747aa14)

### Fully Qualified Domain Name(FQDN)
- 도메인의 전체 이름을 표기하는 방식
- ex) www.goodbird.kr이라면
  - 도메인 이름 : goodbird.kr
  - 호스트 이름 : www
  - FQDN : www.goodbird.kr
 
### 네임 서버(Name Server = DNS Server)
- 문자열로 표현된 도메인 이름을 실제 컴퓨터가 통신할 때 사용하는 IP 주소로 변환
- 일반적으로 데이터베이스 역할, 찾아주는 역할, 요청 처리 응답 구현의 역할 수행.

#### Root DNS Server
- DNS 서버의 최상위 네임서버로 DNS 해석부터 발생한 DNS 요청에 대하여 적절한 TLD 네임서버 정보를 반환한다.

#### Top-Level Domain(TLD) DNS Server
- 도메인 등록 기관이 관리하는 서버로 Authoritative DNS 서버의 주소를 저장하고 안내하는 역할을 한다.

#### Second-Level Domain(SLD) DNS Server (Authoritative DNS Server)
- 실제 개인 도메인과 IP 주소의 관계가 기록되는 서버다.

#### Anauthoritative DNS Server
- 권한이 없는 DNS 서버로 리졸버 서버, 리컬시브 서버, 리커서가 있다.
### 리졸버
- DNS 클라이언트 요청을 네임 서버로 전달하고 찾은 정보를 클라이언트에게 제공하는 기능을 수행


ref)<br>
https://m.blog.naver.com/wnrjsxo/221253031733<br>
https://velog.io/@zinukk/9kpyzbdt<br>
