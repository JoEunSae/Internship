# Hub & Spoke 네트워크

## Hub & Spoke 란?

![image](https://github.com/JoEunSae/Internship/assets/83803199/df29492e-f433-4f9d-9291-ad1a13011889)

**각 지점에서 발생되는 물량들을 중심이 되는 한 거점(Hub)에 집중시킨 후, 각각의 지점(Spoke)으로 다시 분류하여 이동시키는 시스템**

## Azure Hub & Spoke 네트워크 포톨로지 구축

![image](https://github.com/JoEunSae/Internship/assets/83803199/883a96dd-0f42-46a1-9dc0-3d7bac5b4fb9)

1. 네트워크 설계

![image](https://github.com/JoEunSae/Internship/assets/83803199/b26ece82-d03e-4253-86ec-6cea3b791f2e)

2. VPN Gateway
- VPN Gateway란?
  - Microsoft 네트워크를 통해 Azure 가상 네트워크 간에 암호화된 트래픽을 보낼 수도 있다.
  - 공용 인터넷을 통해 Azure 가상 네트워크와 온-프레미스 위치 간에 암호화된 트래픽을 보내는 데 사용할 수 있다.

- VPN Gateway를 사용하는 이유?
  - Azure 가상 네트워크와 온-프레미스
    - S2S : VPN 게이트웨이와 온-프레미스 VPN 디바이스 간의 크로스-프레미스 IPsec/IKE VPN 터널 연결
    - P2S : OpenVPN, IKEv2 또는 SSTP를 통해 VPN. 이러한 유형의 연결을 사용하면 회의나 집 등 원격 위치에서 가상 네트워크에 연결할 수 있다. 
  - 가상 네트워크 간
    - VNet 간: VPN 게이트웨이와 VNet 간 연결 유형을 사용하는 다른 Azure VPN 게이트웨이 간의 IPsec/IKE VPN 터널 연결
    - S2S: VPN Gateway와 다른 Azure VPN Gateway 간의 IPsec/IKE VPN 터널 연결입니다. 이 유형의 연결은 VNet 간 아키텍처에서 사용되는 경우 VPN 게이트웨이 간의 연결 외에도 게이트웨이에 대한 크로스-프레미스 연결을 허용하는 IPsec(사이트 간) 연결 형식을 사용합니다.

3. Peering이란?
- 가상 네트워크 피어링을 사용하면 Azure에서 두 개 이상의 가상 네트워크를 원활하게 연결할 수 있다.
- 피어링된 가상 네트워크에 있는 가상 머신 간의 트래픽은 Microsoft 백본 인프라를 사용한다.

4. VNet 간 Peering과 VNet 간 VPN Gateway 차이
- Peering
  - 




![image](https://github.com/JoEunSae/Internship/assets/83803199/d22f9cf0-4b68-4c82-87a2-d6b466f36edf)
![image](https://github.com/JoEunSae/Internship/assets/83803199/9ff22cc4-0864-4708-b81c-5a42363fda46)


ref) <br>
https://learn.microsoft.com/en-us/azure/architecture/networking/architecture/hub-spoke?tabs=cli <Br>
https://learn.microsoft.com/ko-kr/azure/cloud-adoption-framework/ready/azure-best-practices/hub-spoke-network-topology <Br>
https://learn.microsoft.com/ko-kr/azure/architecture/networking/guide/private-link-hub-spoke-network
