## 통신
![image](https://user-images.githubusercontent.com/57993534/125950379-b8ae09ba-8a82-41a0-886c-9e9439809b10.png)

### 1. Jetson Xavier TX2에 MAVROS 설치
- MAVLink 프로토콜을 이용하여 ROS에서 동작하는 node를 개발하는 프로젝트
- 탑재된 시스템에 설치되며 FC ↔ Onboard ↔ Ground Station 통신을 담당한다.
- Ground Control Station을 위한 proxy를 포함하고 있다.
- MAVROS 패키지에는 MAVLink 통신 프로토콜로 자동 비행에 필요한 통신 드라이버를 제공한다.
- 추가로 UDP MAVLink bridge를 제공하여 Ground Control Station 과 연결할 수 있다.

ssh로 jetson 원격 쉘 

![image](https://user-images.githubusercontent.com/57993534/125950427-cd97ea09-1d50-4199-9885-819602bafc53.png)

- mavros 설치
- sudo apt-get update
- sudo apt-get install ros-kinetic-mavros ros-kinetic-mavros-extras 

### 2. Wi-Fi를 통해 QGroundControl 사용
- Wi-Fi를 통해 QGroundControl을 사용하여 쿼드 콥터의 비행 컨트롤러를 모니터링, 제어, 보정 및 구성 할 수 있습니다. 

1. QGC에서 UDP를 설정
- 그런 다음 QGroundControl 프로그램에서 애플리케이션 설정> 통신 링크> 추가를 선택합니다. 다음 설정으로 연결을 만듭니다.

![image](https://user-images.githubusercontent.com/57993534/125950575-313cddd2-a654-4e4b-8399-23174c78df8d.png)

- 그런 다음 연결 목록에서 생성 된 연결을 선택하고 "연결"을 클릭

  + PX4 UDP PORT 번호 
    + port 기본값: UDP bind는 14555, UDP remote는 14550, TCP는 5760이다.

![image](https://user-images.githubusercontent.com/57993534/125950600-6ca8bfe4-feb2-4d0f-a816-5d1bfe0b2e05.png)

2. roscore 실행시킨다

![image](https://user-images.githubusercontent.com/57993534/125950620-21a8bb73-8c12-4fc8-8b77-75c38d3f328b.png)

3. 연결은 URL로 정의하며, FCU와 GCS가 지원하는 타입을 사용할 수 있음. 
- UDP: udp://[bind_host][:port]@[remote_host][:port][/?ids=sysid,compid]
- mavros_node 기본 통신 노드를 실행시킨다.

![image](https://user-images.githubusercontent.com/57993534/125950630-ba96572f-cff1-4532-92c8-8c18fc457474.png)


- 메인 노드이며, 빈 URL을 설정하여 GCS 프록시 비활성화를 허용한다.
- fcu_url : ![image](https://user-images.githubusercontent.com/57993534/125950646-45b8e318-3c65-4ebf-b30d-06f547da51e8.png)
- gcs_url : ![image](https://user-images.githubusercontent.com/57993534/125950651-0bf20ba0-0f44-4756-82a2-3e27447187a5.png)

### 3. rqt

![image](https://user-images.githubusercontent.com/57993534/125951072-43b6cac7-2f86-44a9-8ec2-f4d2c0c9aae9.png)

- Mavros를 통해 받아온 픽스호크의 데이터를 확인해본다. topic monitor에서 각각의 토픽을 통해서 데이터가 오는 것을 확인할 수 있다.

### 4. 연결확인

![image](https://user-images.githubusercontent.com/57993534/125951114-d4e1d7cd-2e87-4841-83cb-f7fe87554f8d.png)

- PC에서 ARM 확인
