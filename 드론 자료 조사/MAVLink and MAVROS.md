## MAVLink
- 소형 무인 장치들 및 자체 내의 서로 다른 내부 컴포넌트와 통신하기 위한 프로토콜
- 데이터 교환을 제공하는 메시징
- 헤더 전용 메시지 마샬링 라이브러리로 설계됨

메시지 구조

![image](https://user-images.githubusercontent.com/57993534/125825470-db8613e0-5be4-4356-9b0a-3308ba33548a.png)

Byte 0 : MAVLink 시작을 알리는 바이트

Byte 1 : 페이로드(메시지) 길이

Byte 2 : 패킷 시퀀스(메시지 순서)

Byte 3 : 시스템 ID

Byte 4 : 컴포넌트 ID

Byte 5 : 메시지 ID

Byte 6 – n+6 : 메시지(데이터)

Byte n+7 ~ 8 : 체크섬(x.25) 바이트

![image](https://user-images.githubusercontent.com/57993534/125825840-aab6ca05-9c31-416f-bd47-a5798d1b5dae.png)

![image](https://user-images.githubusercontent.com/57993534/125825844-b09a50b9-20b9-45c4-82a1-9ddfe20e28fd.png)

-  직렬 통신(serial communication)을 한다.
- 메시지 전송 방식 : 토픽모드, 일대일 모드로 혼합된 형태
- 토픽 모드 
- 수신 시스템 및 컴포넌트 ID 신호 없이 메시지를 발행, 메시지를 수신할 특정 수신자가 없음, 메시지가 어디로 전송되는지 보장할 수 없음. 
- 오버헤드를 생성할 필요가 없고 복수의 구독자가 이 메시지를 모두 수신 할 수 있음
- 일대일 보드
- 수신할 시스템 및 컴포넌트 ID를 사용하는데 재송신 기능을 포함
- 메시지 전송이 보증 됨.
- 무결성 검사 : 패킷 무결점 검사, 데이터 기술의 무결점 검사로 CRC-16-CCITT를 통해 실행

## MAVROS
- MAVLink 프로토콜을 이용하여 ROS에서 동작하는 node를 개발하는 프로젝트
- 탑재된 시스템에 설치되며 FC ↔ Onboard ↔ Ground Station 통신을 담당한다.
- Ground Control Station을 위한 proxy를 포함하고 있다.
- MAVROS 패키지에는 MAVLink 통신 프로토콜로 자동 비행에 필요한 통신 드라이버를 제공한다.
- 추가로 UDP MAVLink bridge를 제공하여 Ground Control Station 과 연결할 수 있다.

#### 디렉토리 구조 
- libmavconn : mavros에서 사용하는 lib를 모아놓은 폴더
- mavros : mavros으 핵심 구현부 mavros node를 구현한 폴더
Flight Control과 통신하기 위해 serial, UDP, TCP 방식을 지원
내부 proxy를 이용해서 ROS-MAVLink translation 지원
Plugin 시스템을 이용해서 ROS-MAVLink translation 지원
Parameter 처리 도구
Waypoint 처리도구
PX4Flow 지원
OffBoard 지원
- mavros_extras : 추가 plugin과 node를 제공하는 폴더
- mavros_msgs : Ros node가 publish하는 message(data 값)를 정의하는 폴더
- test_mavros : Flight Control과 SITL을 통해 테스트 환경을 제공하는 패키지

#### Connection URL
- 연결은 URL로 정의하며, FCU와 GCS가 지원하는 타입을 사용할 수 있음.
- 지원하는 schemas
	Serial : /path/to/serial/device[:baudrate]
	Serial : serial:///path/to/serial/device[:baudrate][/?ids=sysid,compid]
	UDP: udp://[bind_host][:port]@[remote_host][:port][/?ids=sysid,compid]
	TCP client: tcp://[server_host][:port][/?ids=sysid,compid]
	TCP server: tcp-l://[bind_host][:port][/?ids=sysid,compid]
- URL에 있는 ids는 system_id와 component_id 파라미터에서 주어진 ids를 무효화시킨다.
- baudrate의 기본값은 57600 이다.
- bind_host 기본값은 “0.0.0.0”이다.
- remote_host의 기본값은 unknown이다. mavros는 bind_host:port로 data를 기다린다.
- server_host의 기본값은 “localhost”이다.
- port 기본값: UDP bind는 14555, UDP remote는 14550, TCP는 5760이다. discovery stage에는 UDP broadcast가 사용되고 나중에 GCS address로 변경된다.
- 현재 IPv4만 지원

#### 1. 3dr_radio
- 통신을 하기 위해서는 허용된 주파수를 사용해서 통신하는지 확인해야 한다.
#### 2. global_position
- GPS 데이터와 FCU가 융합된 global position정보를 가져옴
- Topic 
  + global(sensor_msgs/NavSatFix) : GPS 고정
  + local(geometry_msgs/PoseWithCovarianceStamped) : UTM 조정
  + gp_vel(geometry_msgs/TwistStamped) : Velocity fused by FCU
  + rel_alt(std_msgs/Float64) : 상대 고도
  + compass_hdg(std_msgs/Float64) : 방향
  + raw/fix(sensor_msgs/NavSatFix) : 장치에서 받아온 GPS 값
  + raw/gps_vel(geometry_msgs/TwistStamped) : GPS 장치에서 출력된 속도
- Parameters
  + frame_id(string, default: fcu)
  + send(bool, default: true)
  + tf/frame_id(string, default:local_origin)
  + tf/cild_id(string, default: fcu_utm)
