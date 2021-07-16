## Pixhawk connection Jetson Nano

![image](https://user-images.githubusercontent.com/57993534/125948480-cfb5cdaa-db1f-405f-ab10-2066e94503bc.png)

companion 컴퓨터를 pixhawk 보드에 연결하는 동일하다. jetson Nano 역시 companion 컴퓨터임으로 동일한 방식을 취한다. piwhawk 직렬 포트 TELEM 2에 연결한다. TELEM2포트는 companion 컴퓨터에 사용된다. 메시지 형식은 MAVLink이다.

USB 포트를 사용하는 것보다 UART (직렬) 연결을 사용하는 것이 좋다. 그 이유는 USB 포트의 드라이버가 훨씬 더 복잡하기 때문에 UART는 비행에 중요한 기능에 대해 훨씬 더 신뢰할 수있는 포트이다. 

## UART

![image](https://user-images.githubusercontent.com/57993534/125948509-05cee25b-4ec3-4521-8fff-bbcee569279c.png)

UARTS (범용 비동기화 송수신기: Universal asynchronous receiver/transmitter)는 병렬 데이터의 형태를 직렬 방식으로 전환하여 데이터를 전송하는 컴퓨터 하드웨어의 일종이다. 통신 데이터는 메모리 또는 레지스터에 들어 있어 이것을 차례대로 읽어 직렬화 하여 통신한다. 최대 8비트가 기본 단위이다. 컴퓨터나 주변 기기의 일종으로 병렬 데이터를 직렬화 하여 통신하는 개별 집적 회로이다. Jetson nano에 2개가 있다.

직렬(Serial) 통신 -> 1개의 입출력 핀을 통해 8개 비트를 한 번에 전송하는 방법. 시리얼 통신을 사용하기 위해서는 보내는 쪽(TX)와 받는 쪽(RX)에서 약속을 정해야 하는데, 이를 프로토콜(Protocol)이라고 한다.

MCU에서는 0과 1의 값만을 처리할 수 있으므로 0은 GND, 1은 VCC로 데이터를 전송하고,받는 쪽에서는 GND와 VCC를 다시 0과 1의 이진값으로 변환하여 사용한다.
보내는 쪽(TX)와 받는 쪽(RX)이 원할하게 데이터를 교류하려면, 데이터를 보내는 속도에 대하여 약속(프로토콜, Protocol)이 정해져 있어야 한다.

### UART 데이터 비트

![image](https://user-images.githubusercontent.com/57993534/125948557-92b44a26-6dfb-4353-ad83-7c3887ed0bda.png)

- 시작 비트 : 통신의 시작을 의미하며 한 비트 시간 길이 만큼 유지한다. 지금 부터 정해진 약속에 따라 통신을 시작한다.
- 데이터 비트 : 5~8비트의 데이터 전송을 한다. 몇 비트를 사용할 것인지는 해당 레지스터 설정에 따라 결정된다.
- 패리티 비트 : 오류 검증을 하기 위한 패리티 값을 생성하여 송신하고 수신쪽에 오류 판단한다. 사용안함, 짝수, 홀수 패리티 등의 세가지 옵션으로 해당 레지스터 설정에 따라 선택할 수 있다. '사용안함'을 선택하면 이 비트가 제거된다.
- 끝 비트 : 통신 종료를 알린다. 세가지의 정해진 비트 만큼 유지해야 한다. 1, 1.5, 2비트로 해당 레지스터 설정에 따라 결정된다.

Nano의 핀아웃은 라즈베리 파이의 핀아웃과 같다. 

YOLO bounding box 좌표를 serial로 전송 - https://pgmrlsh.tistory.com/9

## Pixhawk 설정
직렬포트에서 MAVLink를 활성화한다. TELME2에서 기본 지원 시스템 메시지 스트림을 설정하려면 다음 매개 변수를 설정한다.
- MAV_1_CONFIG = TELEM2

  = > MAVLink를 실행할 직렬 포트를 구성한다. (102: TELEM 2)
  
- MAV_1_MODE = Onboard

  = > MAVLink 모드는 스트리밍 된 메시지 세트 및 전송 속도를 정의한다. (2 : Onboard)
  
- SER_TELE2_BAUD = 921600

  = > TELEM 2 직렬 포트에 대한 전송 속도를 구성한다. GPS와 같은 특정 드라이버는 전송속도를 자동으로 결정할 수 있다. (921600 : 921600 8N1)

### Jetson Nano 설정
MAVLink를 수신하려면 companion 컴퓨터에서 직렬포트와 통신하는 소프트웨어를 실행해야 한다.
- ROS노드와 통신하기 위한 MAVROS
  + 설치 방법 : https://docs.px4.io/master/en/ros/mavros_installation.html
- C/C++ 예제코드 사용자 지정 코드 연결

  = > pixhawk와 오프 보드 컴퓨터 간의 통신을 허용할 수 있는 nix 시스템에 대한 UART 인터페이스에 대한 간단한 예제를 보내 연결을 한다.
  
https://github.com/mavlink/c_uart_interface_example

- MAVLink 라우터 또는 MAVProxy 직렬 및 UDP 간 MAVLink 라우팅

  = > 일반적인 구성은 플라이트 스택 (UART 또는 UDP) 인 "마스터"엔드 포인트 하나와 UDP 또는 TCP 또는 UART 엔드 포인트에있을 수있는 기타 구성 요소를 갖는 것이다. mavlink-router는 주로 mavlink 패킷을 한 엔드 포인트에서 다른 엔드 포인트로 구분하지 않고 라우팅합니다. TCP 서버가 활성화 된 경우 TCP 엔드 포인트가 자동으로 추가되어 클라이언트가 구성을 변경하지 않고 mavlink-router에 간단히 연결할 수 있다.
 
 + 설치 방법 : https://github.com/mavlink-router/mavlink-router

### 하드웨어 설정
모든 Pixhawk 직렬 포트는 3.3v에서 작동하며 5v와도 호환이 된다.
많은 최신 companion 컴퓨터는 UART에서 1.8V 레벨만 지원하며 3.3V 레벨에 의핸 손상 될 수 있음으로 레벨 시프터를 사용해야 한다. 

![image](https://user-images.githubusercontent.com/57993534/125948769-426d5f73-0326-4487-b518-6641b0d1c0e5.png)

위 TTL 케이블로 해당 번호에게 맡게 배선을 연결한다. 

Linux에서 소프트웨어 설정
- https://docs.px4.io/master/en/companion_computer/pixhawk_companion.html
