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
- 사용자의 컴퓨터나 네트워크에 위치한 DNS 클라이언트

### 동작박식

![image](https://github.com/JoEunSae/Internship/assets/83803199/0ac46806-f085-46fd-b814-a9c4c5f60928)

1. 브라우저 -> DNS Resolver
- 사용자가 웹 브라우저에 도메인 이름을 이력하면, DNS Resolver는 우선 자신의 캐시에 해당 도메인 이름에 대한 IP 주소가 저장되어 있는지 확인한다.
- 캐시에 저장된 IP 주소가 있다면, DNS Resolver는 바로 해당 IP 주소를 반환한다.
- 하지만 캐시에 저장된 IP 주소가 없거나, 캐시에 저장된 IP 주소가 만료되었다면, DNS Resolver는 DSN 서버에 요청한다.

2. DNS Resolver -> Root DNS Server -> DNS Resolver
- 먼저 DNS Resolver는 Root DNS Server에 요청한다.
- Root DNS Server는 TLD DNS Server에 대한 정보를 가지고 있으며, 해당 TLD DNS Server의 IP 주소를 DNS Resolver에게 전달한다.

3. DNS Resolver -> TLD DNS Server -> DNS Resolver
- TLD DNS Server는 해당 도메인 이름의 Authoritative DNS Server의 IP 주소를 DNS Resolver에게 반환

4. DNS Resolver -> Authoritative DNS Server -> DNS Resolver -> 브라우저
- Authoritative DNS Server는 해당 도메인 이름에 대한 IP 주소를 가지고 있으며, 이를 DNS Resolver에게 반환
- DNS Resolver는 이제 해당 IP 주소를 캐시에 저장하고, 이후 동일한 도메인 이름에 대한 질의가 들어올 때 캐시에 저장된 IP 주소를 사용

![image](https://github.com/JoEunSae/Internship/assets/83803199/954f503d-b511-4ea2-ad26-f18fbdcccc94)

**Reculsive Query를 통해서 클라이언트에게 응답한다.**

#### DNS Query란?
- 사용자가 도메인 이름을 입력하고 IP 주소를 얻기 위해 DNS 서버에 보내는 요청을 말한다. 이 요청은 DNS Resolver가 사용자 컴퓨터에서 생성하고 DNS 서버에 전송한다.

### DNS 레코드

1. A 레코드
- IP주소와 도메인 주소를 매핑할 때 사용하는 레코드로써 하나의 도메인에 여러 개의 IP 주소를 등록할 수 있다.

2. AAAA
- A의 확장형으로 도메인에 IPv6주소가 매핑되어 있는 레코드

3. CNAME
- 도메인 별명 레코드라고 부르며 Alias라고 하여 기존 도메인에 별명을 붙인 레코드
- ex) **goodbird.azure.com**이 도메인이라고 했을 때 이 도메인의 CNAME이 **badbird.azure.com**이라고 한다면
badbird.azure.com을 입력했을때 goodbird.azure.com으로 접근할 수 있다.

4. MX
- 메일 서버 레코드이며, 해당 도메인과 연동되어있는 메일서버를 확인하는데 사용하는 레코드

5. NS
- 네임서버 레코드로 도메인에 대한 네임서버의 권한을 가지고 있는지 알려주는 레코드

6. PTR
- IP 주소에 대한 도메인 주소를 확인할 수 있는 레코드

7. SOA
- 마스터 네임서버, 존 관리자 연락처, 존 데티어 동기화 시간 등 도메인의 정보를 가지고 있는 레코드

8. TXT
- 텍스트를 입력할 수 있는 레코드

9. CAA
- 도메인 인증기관에 관련된 레코드

**nslookup -query=[A,CNAME,MX] example.com**을 통해 레코드를 확인할 수 있다.

ref)<br>
https://m.blog.naver.com/wnrjsxo/221253031733<br>
https://velog.io/@zinukk/9kpyzbdt<br>
https://goldsony.tistory.com/148<br>
