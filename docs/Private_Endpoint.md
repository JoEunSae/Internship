![image](https://github.com/JoEunSae/Internship/assets/83803199/37a34c85-38cc-43ae-a32e-23d59cf68f56)# Private Endpoint를 통해 Azure SQL서버에 연결하기

![image](https://github.com/JoEunSae/Internship/assets/83803199/f5a64105-10af-482d-859f-92118caf7159)
![image](https://github.com/JoEunSae/Internship/assets/83803199/3102a344-b3d5-43b2-80da-75dd97dc7174)

## 1. 가상 네트워크 및 Azure Bastion 호스트 만들기

### Azure Bastion이란?

**가상 네트워크 생성 시 Bastion 사용 선택**
![image](https://github.com/JoEunSae/Internship/assets/83803199/32a7f889-0a4b-47e6-9663-7c6d5ec8c3e2)

**Subnet은 아래 구성과 같이 진행**
![image](https://github.com/JoEunSae/Internship/assets/83803199/a76bee08-cc3b-47a0-9b99-92e67fb2938e)

## 2. VM 생성

![image](https://github.com/JoEunSae/Internship/assets/83803199/1465806a-b4a6-4c96-a579-ebd14bc3bede)

## 3. Azure SQL 서버 및 프라이빗 엔드포인트 만들기

### Private Endpoint란?

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




ref)<br>
https://learn.microsoft.com/ko-kr/azure/private-link/tutorial-private-endpoint-sql-portal<br>
https://learn.microsoft.com/ko-kr/azure/bastion/bastion-overview<br>
https://learn.microsoft.com/ko-kr/azure/private-link/private-endpoint-overview<br>
