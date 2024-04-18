![image](https://github.com/JoEunSae/Internship/assets/83803199/25094656-40bc-44ad-8a5d-9879ea1395f2)![image](https://github.com/JoEunSae/Internship/assets/83803199/3f4bf4e9-9dab-456b-828d-f8fc99e6ba61)# IP

## IP 주소

**Layer 2 : MAC 주소(물리주소)**
**Layer 3 : IP 주소(논리 주소)**

- 사용자가 변경 가능한 논리 주소
- 주소에 레벨(Class)이 존재 - 그룹을 의미하는 **네트워크 주소** 와 **호스트 주소**로 나뉨

## IP 주소 체계

### IPv4

![image](https://github.com/JoEunSae/Internship/assets/83803199/f108bf08-b19c-4e32-979e-c418e571e203)

**32비트로 이루어 져 있으며 4개의 옥텟(Octect)으로 8비트 단위로 나눈다.**

- 네트워크 주소 : 호스트들을 모은 네트워크를 지칭하는 주소
- 호스트 주소 : 하나의 네트워크 내에 존재하는 호스트를 구분하기 위한 주소

**필요한 호스트 IP의 갯수에 따라 네트워크의 크기를 다르게 할당할 수 있는 클래스 개념 도입**
#### 클래스는 하나의 IP 주소에서 네트워크 영역과 호트스 영역을 나누는 방법

### A Class

![image](https://github.com/JoEunSae/Internship/assets/83803199/15808f49-d060-48a1-8a5d-94c1e7021f98)

**1.0.0.0 ~ 127.0.0.0의 주소를 가질 수 있다.**
**네트워크 주소를 표현하는 부분이 1개의 옥텟, 호스트 주소를 나타낼 수 있는 부분이 3개의 옥텟으로 구성**

### B Class

![image](https://github.com/JoEunSae/Internship/assets/83803199/c7836314-53f0-4d22-b707-7e7584879f66)

**128.0.0.0 ~ 191.255.255.255의 주소를 가질 수 있다.**
**네트워크 주소를 표현하는 부분이 2개의 옥텟, 호스트 주소를 나타낼 수 있는 부분이 2개의 옥텟으로 구성**

### C Class

![image](https://github.com/JoEunSae/Internship/assets/83803199/bbdf6b53-0f10-4a65-8c30-06dde500a037)

**192.0.0.0 ~ 223.255.255.255의 주소를 가질 수 있다.**
**네트워크 주소를 표현하는 부분이 3개의 옥텟, 호스트 주소를 나타낼 수 있는 부분이 1개의 옥텟으로 구성**

### Classful 과 CIDR

