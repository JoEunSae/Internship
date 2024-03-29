# Network

## OSI 7 Layer
![image](https://github.com/JoEunSae/Internship/assets/83803199/f4e96cd8-7fe7-430b-85fb-6c6f5dd396a9)

### OSI 7 Layer란?
- 국제표준화기구(ISO)에서 개발한 모델로, 컴퓨터 네트워크 프로토콜 디자인과 통신을 계층으로 나누어 설명한 것.
- 각 계층은 하위 계층의 기능만을 이용하고, 상위 계층에게 기능을 제공한다.

#### Application Layer(7 Layer)
- 사용자가 UI로 접하는 응용 프로그램과 관련된 계층으로 HTTP,FTP,DHCP,SMTP,DNS 등이 있다. 여기에 속한 프로토콜들은 어떠한 방법으로든 사용자와 직접 접하게 된다.
- (Data + HTTP Header)

#### Transport Layer(4 Layer)
- 송신자와 수신자의 논리적 연결을 담당하는 부분으로, 신뢰성 있는 연결을 유지할 수 있도록 도와준다.
- Endpoint(사용지) 간의 연결을 생성하고 데이터를 얼마나 보냈는지 얼마나 받았는지, 제대로 받았는지 등을 확인한다. TCP와 UDP가 대표적
- (Data + HTTP Header + TCP Header)

#### Network Layer(3 Layer)
- IP(Internet Protocol)이 활용되는 부분으로, 한 Endpoint가 다른 Endpoint로 가조가 할 경우, 경로와 목적지를 찾아준다. 이를 Routing이라고 하며 대역이 다른
IP들이 목적지를 향해 제대로 찾아갈 수 있도록 돕는 역할을 합니다.

#### DataLink Layer(2 Layer)
- 같은 네트워크 대역을 사용하는 단말들에 대해 신뢰성 있는 전송을 보장한다.
- 즉 'MAC adress'를 활용하여 같은 구간 내의 Endpoint 혹은 Switching

## NAT

### NAT란?
- 사설망에서 공인망으로, 공인망에서 사설망으로 통신하고자 할 때 공인망/사설망에서 사용하는 IP로 변환
- IP 주소뿐만 아니라 Port까지 변환시켜 사용
- NAT수행 장비 : 라우터, 방화벽, 공유기, NAT장비
  
![image](https://github.com/JoEunSae/Internship/assets/83803199/cf1a897c-89b1-4274-b928-6f883b8dfb7b)
- 사용자 1이 가지고 있는 사설 IP로는 Server와의 통신이 불가능하다 그래서 NAT 장비를 통해서 사설 IP를 공인 IP로 변환하여 외부의 Server와 통신하는 것이다.

![image](https://github.com/JoEunSae/Internship/assets/83803199/179e98de-af50-42f6-8326-bf6edc263f1a)

#### SNAT
- 출발지 IP를 다른 IP로 변경하여 통신을 가능케 한다.

![image](https://github.com/JoEunSae/Internship/assets/83803199/e16b14a0-50bd-462f-b279-66b3460b3d1d)
- 내부 사용자들은 외부 인터넷으로 나아갈 떄 52.15.77.39 IP를 Source IP로 장착하고 나간다. 다시 말해 Outgoing Interface IP가
공인 IP이기 때문에 NAT 이후엔 사용자들이 사설 IP 또한 자동으로 공인 IP로 변경되는 것이다.

#### DNAT
- 목적지 IP를 변경하여 통신을 원할하게 한다.
- SNAT와 다르게 NAT Device의 인터페이스 IP를 거의 사용하지 않는다. 다시 말해 이미 정해둔 IP 리스트를 보유한 상태에서 해당 IP로 변환을 실시
- 목적지 IP를 변환하는 만큼 Destination IP를 변환하는 대상을 명확히 구분해야 한다.
**SNAT와 다르게 변환 대상 IP를 중복하여 써서는 안된다**

![image](https://github.com/JoEunSae/Internship/assets/83803199/dd0fb97a-fc40-40f0-b817-df565ad22b04)

#### Stateful
- 클라이언트-서버 관계에서 서버가 클라이언트의 상태를 보존함을 의미한다.
- 클라이언트의 이전 요청이 서버에 잘 전달되었을 때, 클라이언트의 다음 요청이 이전 요청과 관계가 이어지는 것을 의미한다.

#### Stateless
- 클라이언트-서버 관계에서 서버가 클라이언트의 상태를 보존하지 않음을 의미한다.
- Stateless 구조에서 server는 단순히 요청이 오면 응답을 보내는 역할만 수행하며, 세션 관리는 클라이언트에게 책임이 있다.

## Switch / Router

### Switch란?
- 여러 장치 간에 데이터를 전달하고 네트워크 트래픽을 관리하는 역할
- 주로 로컬 에어리어 네트워크(LAN)에서 사용되며, 스위치는 네트워크에 연결된 컴퓨터, 서버, 프린터 등의 장치들 간에 데이터를 전달

#### Switch동작
- 데이터가 스위치로 들어오면, 스위치는 해당 데이터의 목적지를 확인하여 해당하는 포트로 데이터를 전달

** 허브와는 다르게 데이터가 전송될 목적지를 미리 확인하여 해당 목적지로만 데이터를 전달하기 때문에, 네트워크의 대역폭을 효율적으로 활용할 수 있다.**

#### Hub
- Hub는 Hub로 들어오는 데이터를 네트워크에 연결된 모든 장치로 전송한다.

### Router란?
- Router는 IP 주소 등 Layer 3에 있는 주소를 참조하여 목적지와  연결되는 포트로 패킷을 전송한다.
- 서브넷이 다른 IP 주소를 가진 장비간에 통신이 이루어지려면 반드시 Layer 3 장비를 거쳐야만 한다.
- 주로 인터넷과 로컬 네트워크 간의 트래픽을 관리하고, 네트워크를 분리하거나 통합하는 역할

![image](https://github.com/JoEunSae/Internship/assets/83803199/0ec35515-fb52-45d9-9c1c-53d046ada53e)


## L4/L7 로드밸런서

### L4 로드밸런서
- 전송 계층(Transport Layer, Layer 4) 에서 작동하는 로드 밸런서로, 주로 TCP 및 UDP 프로토콜을 기반으로 클라이언트와 서버 간의 트래픽을 분산시킨다.
- 패킷의 헤더 정보만을 이용하기 때문에 빠른 응답 시간을 제공
- 애플리케이션 계층의 정보를 활용하지 못해 기능 및 유연성이 제한적
- ex) 온라인 게임, 스트리밍 서비스 등 실시간 트래픽 처리가 중요한 서비스에 적합
  
### L7 로드밸런서
- 애플리케이션 계층(Application Layer, Layer 7) 에서 작동하는 로드 밸런서로, 주로 HTTP 및 HTTPS 프로토콜을 기반으로 클라이언트와 서버 간의 트래픽을 분산시
- 요청 내용을 분석하여 특정 요청을 특정 서버로 전달하거나, 캐싱 및 압축 등의 다양한 기능을 구현할 수 있다.
- 패킷의 애플리케이션 계층 정보를 분석해야 하기 때문에 L4 로드 밸런서보다 처리 시간이 더 걸린다.
- ex) 웹 서비스, API 게이트웨이, 콘텐츠 전송 네트워크(CDN)

**상위 계층을 활용할 수 있는 장비들은 모두 하위 계층 또한 이해하고 활용할 줄 알아야 한다.**





ref)<br>
https://aws-hyoh.tistory.com/145<br>
https://aws-hyoh.tistory.com/166<br>
https://aws-hyoh.tistory.com/167<br>
