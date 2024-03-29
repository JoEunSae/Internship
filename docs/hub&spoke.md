# Hub & Spoke 네트워크

## Hub & Spoke 란?

![image](https://github.com/JoEunSae/Internship/assets/83803199/df29492e-f433-4f9d-9291-ad1a13011889)

**각 지점에서 발생되는 물량들을 중심이 되는 한 거점(Hub)에 집중시킨 후, 각각의 지점(Spoke)으로 다시 분류하여 이동시키는 시스템**

## Azure Hub & Spoke 네트워크 포톨로지 구축

![image](https://github.com/JoEunSae/Internship/assets/83803199/883a96dd-0f42-46a1-9dc0-3d7bac5b4fb9)

### 1. 네트워크 설계

![image](https://github.com/JoEunSae/Internship/assets/83803199/b26ece82-d03e-4253-86ec-6cea3b791f2e)

### 2. VPN Gateway
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

### 3. Peering이란?
- 가상 네트워크 피어링을 사용하면 Azure에서 두 개 이상의 가상 네트워크를 원활하게 연결할 수 있다.
- 피어링된 가상 네트워크에 있는 가상 머신 간의 트래픽은 Microsoft 백본 인프라를 사용한다.

### 4. VNet 간 Peering과 VNet 간 VPN Gateway 차이
- Peering
  - 두 가상 네트워크 간의 간단한 통신을 설정하며, 트래픽은 Azure의 내부를 통해 라우팅. VPN과 달리 추가 비용이 발생하지 않는다.
  
![image](https://github.com/JoEunSae/Internship/assets/83803199/0c343a70-260c-424c-8aa9-5f558cc68b86)

- VPN Gateway
  - 주로 안전한 터널을 통한 네트워크 간의 연결을 지원합니다. 데이터는 암호화되어 전송되므로 보안이 강화된다.
  - Azure VNet과 On-Premise 네트워크 간의 연결을 지원한다.
 
![image](https://github.com/JoEunSae/Internship/assets/83803199/5b5d87a9-ae3a-45c4-b120-ede92710683e)

**주소 대역이 겹치지 않게 설계해야 한다.**

### 5. VPN Gateway 생성

![image](https://github.com/JoEunSae/Internship/assets/83803199/0768a4e2-89ce-4676-b0b2-2b550c354155)

- Active-Active 모드 : 여러 리전 간에 VPN Gateway를 활용하여 고가용성 및 부하 분산을 달성하는 모드
- BGP (Border Gateway Protocol) : 가상 네트워크와 온프레미스 네트워크 간의 동적 경로 교환을 지원한다. BGP는 다양한 네트워크 구성에서 라우팅 정보를 효율적으로 교환하는 데 사용되는 프로토콜

**On-Premise와 VNet간의 연결에서는 Public IP 사용이 일반적**

### 6. Local Network Gateway 생성

- Local Network Gateway
  - 라우팅 목적으로 온-프레미스 위치(사이트)를 나타내는 특정 개체이다.
  -  Azure가 참조할 수 있는 사이트 이름을 지정한 다음, 연결을 만들 온-프레미스 VPN 디바이스의 IP 주소를 지정한다.

**Vnet1과 Vnet2에 각각 VPN Gateway와 Local Network Gateway가 필요**

![image](https://github.com/JoEunSae/Internship/assets/83803199/88f0cb14-3e24-4c85-9628-0ac43c61ceae)

- Vnet1의 **VPNGateway의 공용 IP**와 **Vnet1의 주소공간**을 담은 Local Network Gateway와 Vnet2의 VPN Gateway연결
- Vnet2의 **VPNGateway의 공용 IP**와 **Vnet2의 주소공간**을 담은 Local Network Gateway와 Vnet1의 VPN Gateway연결

![image](https://github.com/JoEunSae/Internship/assets/83803199/a677d7a2-2c68-4375-b32f-2d71c9ae6a20)

**Vnet2의 정보를 담는 LocalGateway에는 Vnet3의 주소 대역도 함께 담아야 한다.**

### 7. Vnet2와 Vnet3 Peering

![image](https://github.com/JoEunSae/Internship/assets/83803199/5ab1ece3-018c-4805-b9fd-fc73706afef6)

![image](https://github.com/JoEunSae/Internship/assets/83803199/7e81c1ab-9ecc-42d8-a744-349e5ecc6569)

**Peering생성시 반드시 Vnet2에서 Vnet3로 Vnet3에서 Vnet2로 트래픽이 전달될 수 있도록 설정해주어야 한다.**

### 8. Firewall 생성

![image](https://github.com/JoEunSae/Internship/assets/83803199/cd11647d-a61f-480d-85af-b46a0d750b78)

**해당 Vnet에 반드시 AzureFirewallSubnet이 존재해야한다.**

#### Firewall의 네트워크 규칙 컬렉션 설정

![image](https://github.com/JoEunSae/Internship/assets/83803199/0ad3a106-1224-415b-bc60-50bf476dc0ea)

- Source : 출발지 네트워크 대역
- 대상 주소 : 목적지 네트워크 대역


### 9. Routing Table 생성
- Routing Table생성 후 **Subnet에 연**결하고 **경로** 생성

![image](https://github.com/JoEunSae/Internship/assets/83803199/7273d66f-da0a-4a63-bc22-b002a0b4e4bc)

- 대상 IP 주소 : 목적지의 주소 공간
- 다음 홉 주소 : Firewall의 **사설 IP**

**Vnet2와 Vnet3모두 Routing Table생성**



### 10. Ping Test

**Vnet1의 VM에서 Vnet3의 VM으로 Ping**

![image](https://github.com/JoEunSae/Internship/assets/83803199/67c94dcb-730c-4375-954e-e403c5e4bafb)

**Vnet3의 VM에서 Vnet1의 VM으로 Ping**

![image](https://github.com/JoEunSae/Internship/assets/83803199/eed42383-a603-41d6-984a-a12ff76bd871)



ref) <br>
https://learn.microsoft.com/en-us/azure/architecture/networking/architecture/hub-spoke?tabs=cli <Br>
https://learn.microsoft.com/ko-kr/azure/cloud-adoption-framework/ready/azure-best-practices/hub-spoke-network-topology <Br>
https://learn.microsoft.com/ko-kr/azure/architecture/networking/guide/private-link-hub-spoke-network <br>
https://azure.microsoft.com/en-us/blog/vnet-peering-and-vpn-gateways/ <br>
https://learn.microsoft.com/ko-kr/azure/virtual-network/manage-route-table <br>
https://learn.microsoft.com/ko-kr/azure/vpn-gateway/tutorial-site-to-site-portal <br>
https://learn.microsoft.com/ko-kr/azure/firewall/firewall-multi-hub-spoke
