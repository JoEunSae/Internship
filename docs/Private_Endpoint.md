# Private Endpoint를 통해 Azure SQL서버에 연결하기

![image](https://github.com/JoEunSae/Internship/assets/83803199/f5a64105-10af-482d-859f-92118caf7159)
![image](https://github.com/JoEunSae/Internship/assets/83803199/3102a344-b3d5-43b2-80da-75dd97dc7174)

## 1. 가상 네트워크 및 Azure Bastion 호스트 만들기

### Azure Bastion이란?
- 개인 IP 주소를 통해 가상 머신에 안전하게 연결하기 위해 프로비전하는 완젼 관리형 PaaS 서비스
- Azure Portal의 TLS를 통해 직접 또는 로컬 컴퓨터에 이미 설치된 네이티브 SSH 또는 RDP 클라이언트를 통해 가상 머신에 안전하고 원할한 RDP/SSH 연결을 제공
- 외부 환경에는 RDP/SSH 포트가 노출되지 않게 가상 머신을 보호할 수 있다.

**가상 네트워크 생성 시 Bastion 사용 선택**
![image](https://github.com/JoEunSae/Internship/assets/83803199/32a7f889-0a4b-47e6-9663-7c6d5ec8c3e2)

**Subnet은 아래 구성과 같이 진행**
![image](https://github.com/JoEunSae/Internship/assets/83803199/a76bee08-cc3b-47a0-9b99-92e67fb2938e)

## 2. VM 생성

![image](https://github.com/JoEunSae/Internship/assets/83803199/1465806a-b4a6-4c96-a579-ebd14bc3bede)

## 3. Azure SQL 서버 및 프라이빗 엔드포인트 만들기

### Private Endpoint란?
- 가상 네트워크의 개인 IP 주소를 사용하는 네트워크 인터페이스
- Azure Private Link에서 제공하는 서비스에 비공개로 안전하게 연결

#### PaaS 서비스 private하게 접근 가능하게 쓰고 싶을 때

1. service endpoint를 사용하여 특정 subsnet에서의 접근만 허용
2. private endpoint를 사용하여 vnet 안에 nic를 통해 private ip를 부여하여, private ip를 통해서만 접근 허용

**두 방법의 차이점은 Private IP 유무**
```
private endpoint는 private ip가 주어지기에, 해당 private ip를 통해 접근이된다.
하지만, service endpoint는 특정 서브넷 또는, 특정 ip에서만 접근 가능하게 한다.
```

**SQL 데이터베이스 만들기**
![image](https://github.com/JoEunSae/Internship/assets/83803199/50f0a647-731c-4802-998f-c53475afc83f)

**SQL 데이터베이스 서버 생성**
![image](https://github.com/JoEunSae/Internship/assets/83803199/bd16500c-703d-4e08-89c4-a056cee68fee)

**프라이빗 엔드포인트 생성**
![image](https://github.com/JoEunSae/Internship/assets/83803199/5d308c06-c6d1-427b-b0c1-43b47c3bb0cb)

## 4. 프라이빗 엔드포인트에 연결 테스트

**Bastion을 통해 VM에 연결**

![image](https://github.com/JoEunSae/Internship/assets/83803199/f201610e-aff1-4c5f-b327-1089ee81464b)

**Private Endpoint와 통합된 Private DNS주소를 nslookup을 통해 Private IP확인**
![image](https://github.com/JoEunSae/Internship/assets/83803199/742efd0b-0bf1-403a-8529-1b00fde9079d)

![image](https://github.com/JoEunSae/Internship/assets/83803199/92ba8d12-e14d-42b5-823d-91c201cbf655)

### SQL Server 명령줄 도구 sqlcmd 밒 bcp를 설치하여 SQL Server에 연결
https://learn.microsoft.com/ko-kr/azure/private-link/tutorial-private-endpoint-sql-portal

![image](https://github.com/JoEunSae/Internship/assets/83803199/d5a5fe29-0342-4d48-98f5-580e25b00d84)
`sqlcmd -S 'PrivateEndpoint와 통합한 Private DNS주소' -U '관리자 이름' -P '비밀번호`

ref)<br>
https://learn.microsoft.com/ko-kr/azure/private-link/tutorial-private-endpoint-sql-portal<br>
https://learn.microsoft.com/ko-kr/azure/bastion/bastion-overview<br>
https://learn.microsoft.com/ko-kr/azure/private-link/private-endpoint-overview<br>
https://learn.microsoft.com/ko-kr/sql/linux/sql-server-linux-setup-tools?view=sql-server-ver16&tabs=ubuntu-install<br>
https://velog.io/@pwcasdf/Azure-private-endpoint-%EC%99%80-service-endpoint-%EB%9E%80
