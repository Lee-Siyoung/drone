## openTx RC 조종기 설정
### 설정
1. 바인딩 설정

![image](https://user-images.githubusercontent.com/57993534/125949867-e89f0852-b76d-4d64-8c8d-7fce3033e915.png)

2. 수신확인

![image](https://user-images.githubusercontent.com/57993534/125949882-9dd2b3ad-5b90-4d32-9673-28e497ec678f.png)

3. 모드설정 

- position : 자세 유지
- attitutde : 고도 유지
- manual : 제어 x

![image](https://user-images.githubusercontent.com/57993534/125949903-ed803964-cf39-47bc-a6dc-b3469ef9974a.png)






### 드론 파라미터 설정 및 jetson xavier 연결
1. ssh을 이용해 원격으로 PC와 jetson xavier을 연결한다.

![image](https://user-images.githubusercontent.com/57993534/125949976-6d45a569-505e-4b3c-b1ee-2569a839334a.png)

2. ssh 터널링 옵션을 사용하여 터널을 생성
컴퓨터에는 ssh -C -fR 14551:localhost:14551 remote.local을 해주고

3. UDP 패킷은 SSH를 통해 라우팅 될 수 있도록 TCP 패킷으로 변환되어야 한다. 먼저 패킷을 UDP에서 TCP로 변환 한 다음 다른 쪽 끝에서 다시 UDP로 변환합니다.

![image](https://user-images.githubusercontent.com/57993534/125950001-85374ff6-a062-4bca-8ae0-ce77d62837a8.png)

4. lsubs를 통해 Xavier와 연결하고 있는 목록을 확인한다.

![image](https://user-images.githubusercontent.com/57993534/125950019-bc624f28-3bba-4f75-8bfe-02c5f86d0743.png)

5. Linux에서 USB FTDI의 기본 이름은 \dev\ttyUSB0이다. 다른 연결과 혼동을 피하기 위해서 심볼릭 링크를 생성한다. 새 UDEV 규칙을 생성 하여 idVendor 및 idProduct를 귀하의 것으로 변경할 수 있다.

![image](https://user-images.githubusercontent.com/57993534/125950032-117dfa04-c9eb-4a9b-b34d-f68a5d963b38.png)

6. pc에서 지정한 idVendor의 이름을 입력하여 연결한다.

![image](https://user-images.githubusercontent.com/57993534/125950040-729c9b43-48d1-4d64-8266-0fdb3569fa44.png)

- UDEV(userspace device) : 디바이스 연결시 디바이스 드라이버와 연계하여 자동으로 디바이스 노드를 생성/제거하게 Control할 수 있는 기능
