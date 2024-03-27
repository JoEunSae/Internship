# 3Tire Architecture

![image](https://github.com/JoEunSae/Internship/assets/83803199/a782cf9c-0ed0-4217-8ae9-78a8141fcd7f)

## 1.Azure Database for MySQL Server생성

### Pirvate Endpoint
- 프라이빗 엔드포인트는 가상 네트워크의 개인 IP 주소를 사용하는 네트워크 인터페이스로, Azure Private Link에서 제공하는 서비스에 비공개로 안전하게 연결할 수 있다.

![image](https://github.com/JoEunSae/Internship/assets/83803199/b83b801a-475f-4d46-97be-067a417a775b)

**백엔드에서 프라이빗 엔드포인트를 통해서 연결할 수 있도록 설정**

![image](https://github.com/JoEunSae/Internship/assets/83803199/30d3532b-6f27-44a6-b723-ba500c55a87c)

**프라이빗 엔드포인트 생성**

![image](https://github.com/JoEunSae/Internship/assets/83803199/d6946082-36d7-4716-9983-e854cce0e553)

## 2. Backend AppService생성

![image](https://github.com/JoEunSae/Internship/assets/83803199/5eb201c8-0b10-48bd-af64-5c032f95b169)

![image](https://github.com/JoEunSae/Internship/assets/83803199/67635992-0481-4b0a-9565-3e1b6251a352)

**FrontEnd 정적웹앱 서비스의 요청에 대한 cors허용**

![image](https://github.com/JoEunSae/Internship/assets/83803199/e8814523-41c8-48a5-950c-6d52c26ad5f0)
