# 1장 로봇 소프트웨어 플랫폼
### 1.1 플랫폼의 구성요소
PC(Personal Computer), PP(Personal Phone의 공통점

→ 누구나 하나쯤 보유하고 있는 대중화 제품

→ 다양한 하드웨어의 결합이 가능한 하드웨어 모듈

→ 운영체제(Operating System) + 애플리케이션(App)

하드웨어 모듈 + 운영체제 + 앱(서비스) + 유저

→ 보이지 않는 생태계 속의 분업

로봇 개발의 경우 혼자다해야 함

### 1.2 로봇 소프트웨어 플랫폼
소프트웨어 플랫폼이 가져온 변화
- 하드웨어 인터페이스 통합
- 하드웨어 추상화, 규격화, 모듈화
- 가격 낮춰짐, 성능은 높아짐
- 하드웨어, 운영체제, 애플리케이션 분리
- 사용자 수요에 맞는 서비스에 집중!
- 유저 증가! 구매와 피드백, 새로운 생태계 선환 구조 형성

#### 로봇 운영체제
- RT
- OPROS - Galapagos
- NAOqi - Closed source
- URBI
- ROS - Opensource

### 1.3 로봇 소프트웨어 플랫폼이 가져올 미래
- 하드웨어 플랫폼과의 소프트웨어 플랫폼 간의 인터페이스 확립
- 모듈형 하드웨어 플랫폼 확산
- 하드웨어에 대한 지식이 없어도 응요프로그램 작성가능(있다면 더 좋고)
- 더 많은 소프트웨어 인력들이 로보틱스 분야로 진입, 로봇 제품에 참여가능
- 유저에게 제공할 서비스에 집중
- 실수요가 있는 서비스 제공으로 유저계층 형성 및 피드백
- 로봇 개발이 급속도로 발전할 수 있는 계기

# 2장 로봇 운영체제 ROS
### 2.1 ROS 소개
- Open-Source
- Meta-Operating System
- personal robot을 위한 운영체제

#### 소프트웨어 프레임워크
: ROS의 특징

: ROS = Plumbing + Tools + Capabilities + Ecosystem

- 노드 간에 메시지 교환 방법으로 복잡한 프로그램을 잘게 나눠 고동 개발이 가능
- 명령어 도구, 시각화 도구 Rviz, GUI 도구 모음 rqt, 3차원 시뮬레이터 Gazebo지원
- 로보틱스에서 많이 사용되는 모델링, 센싱, 인식, 네비게이션 매니 퓰레이션 기능 지원
- 로보틱스 생태계 생성! - ROS의 진정한 목적

### 2.2 메타 운영체제
- 정확히 정의된 용어는 아님
- 전통적인 운영체제 아님
- 전통적인 운영체제(리눅스, 윈도우즈, OS-X, 안드로이드)를 이용
- 로봇 응용 소프트 웨어 개발을 위한 필수 기능을 라이브러리 형태로 제공
- 로봇 소프트 웨어 프레임워크

### 2.3 ROS의 목적
- 로보틱스 소프트웨어 개발을 전 세계 레벨에서 공동 작업이 가능하도록 하는 환경을 구축하는 것
- 분산 프로세스
- 패키지 단위 관리
- API 형태
- 복수의 프로그래밍 언어 지원

### 2.4 ROS의 구성
- 다양한 프로그래밍 언어를 지원하기 위한 클라이언트 라이브러리
- 하드웨어 제어를 위한 하드웨어 인터페이스
- 데이터 통신을 위한 커뮤니케이션
- 다양한 로보틱스 응용 프로그램의 작성을 돕는 로보틱스 애플리케이션 프레임워크
- 서비스용 응용프로그램인 로보틱스 애플리케이션
- 가상 공간에서 로봇을 제어해 볼 수 있는 시뮬레이션
- 소프트웨어 개발 툴

### 2.5 ROS의 생태계
- 로봇, 센서 : 90 종류 이상의 로봇, 80 종류 이상의 센서 지원
- ROS : 애플리케이션, 시뮬레이터, 지능모듈, 라이브러리, 디바이스드라이버, 디버그 툴, 메시지통신, 실행 툴, 컴파일 툴, 파일 시스템, 설치 툴, 프로그래밍언어
- APP : 5,000개 이상의 패키지, 2,818개의 공식패키지 제공, 113,345 다운로드(Unique IP, July 2016), 17,058 Wiki페이지(July 2016)

### 2.6 ROS의 역사
- 2007년 5월 미국의 스탠퍼드 대학 인공지능 연구소가 진행하던 STAIR 프로젝트를 위해 모건 퀴클리 박사가 개발한 Switchyard 시스템에서 시작됨
- 2007년 11월 윌로우 개러지가 이어받아 ROS를 개발하기 시작
- 2010년 1월 22일 ROS 1.0 이 배포
- 2010년 3월 1일 ROS Box Turtle로 첫 릴리즈

### 2.7 ROS 버전
- ROS 릴리즈 스케줄과 버전 선택!
  + 5년지원 약속된 최신 LTS버전의 우분투 선택
→ 2년마다 LTS버전 릴리즈, 매년 4월에 나온 것
  + 우분투 릴리즈된 후 3개월 후
  + 최신 LTS 지원 ROS버전
  + 단, ROS는 릴리즈된 후 3개월 후 (일반적인 경우)
  + Gazebo "gazebosim.org" 정보 확인 후 사용

# 3장 ROS 개발환경 구축
### 3.1 ROS 설치
NTP 설정
```
$ sudo apt-get install –y chrony ntpdate
$ sudo ntpdate -q ntp.ubuntu.com
```
소스리스트 추가
```
$ sudo sh –c ‘echo “deb http://packages.ros.org/ros/ubuntu $(lsb_realease –sc) main” > /etc/apt/sources/list.d/ros-latest.list’
$ sudo sh –c ‘echo “deb http://packages.ros.org/ros/ubuntu xenial main” > /etc/apt/sources.list.d/ros-latest.list’
```
키설정
```
$ sudo apt-key adv —keyserver hkp:/ha.pool.sks-keyservers.net:80 —recv-key
 421C365BD9FF1F717815A3895523BAEEB01FA116
```
패키지 인데스 업데이트
```
$ sudo apt-get update && sudo apt-get upgrade -y
```
ROS Kinetic Kame 설치
```
$ sudo apt-get install ros-kinetic-desktop-full
$ sudo apt-get install ros-kinetic-rqt*
```
rosdep 초기화
```
$ sudo rosdep init
$ rosdep update
```
rosinstall 설치
```
$ sudo apt-get install python-rosintall
```
환경설정 파일 불러오기
```
$ source /opt/ros/kinetic/setup.bash
```
작업 폴더 생성 및 초기화
```
$ mkdir –p ~/catkin_ws/src
$ cd ~/catkin_ws/src
$ catkin_init_workspace

$ cd ~/catkin_ws/
$ catkin_make
```
```
$ ls
build
devel
src
```
```
catkin 빌드 시스템과 관련된 환경 파일 불러오기
$ source ~/catkin_ws/devel/setup.bash
```
테스트
```
$ roscore
```

간단 설치 방법
```
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/intall_
ros_kinetic.sh
$ chmod 755 ./install_ros_kinetic.sh
$ bash ./install_ros_kinetic.sh
```
### 3.2 ROS 개발환경
ROS 환경설정
```
$ source /opt/ros/kinetic/setup.bash
$ source ~/catkin_ws/devel/setup.bash

$ getdit ~/.bashrc
```
```
~/.bashrc 내용

#Set ROS Kinetic
source /opt/ros/kinetic/setup.bash
source ~/catkin_ws/devel/setup.bash

# Set ROS Network 
export ROS_HOSTNAME=xxx.xxx.xxx.xxx
export ROS_MASTER_URI=http://${ROS_HOSTNAME}`

#Set ROS alias command
alias cw=‘cd ~/catkin_ws’
alias cs=’cd ~/catkin_ws/src’
alias cm=’cd ~/catkin_ws && catkin_make’
```
```
$ source ~/.bashrc
```
ROS 환경설정 불러오기
```
# Set ROS Kinetic
source /opt/ros/kinetic/setup.bash
source ~/catkin_ws/devel/setup.bash
```
ROS 네트워크 설정
```
# Set ROS Network
export ROS_HOSTNAME=192.168.1.100
export ROS_MASTER_URI=http://${ROS_HOSTNAME}:11311
```
```
# Set ROS Network
export ROS_HOSTNAME=localhost
export ROS_MASTER_URI=http://localhost:11311
```

QtCreator 설치
```
$ sudo apt-get install qtcreator
```
QtCreator 구동
```
$ qtcreator
```

# 4장 ROS의 중요 콘셉트
### 4.1 ROS 용어 정리
- ROS : 로봇 소프트웨어 플랫폼
- 마스터 : 노드와 노드 사잉의 연결과 메시지 통신을 위한 네임 서버와 같은 역할
- 노드 : ROS에서 실행되는 최소 단위의 프로세서를 지칭
- 패키지 : ROS를 구성하는 기본 단위, ROS의 응용 프로그램음 패키지 단위로 개발
- 매타패키지 : 공통된 목적을 지닌 패키지들의 집합
- 메시지 : integer, gloating point, boolean과 같은 변수 형태
- 토픽 
- 퍼블리시 : 토픽의 내용에 해당하는 메시지 형태의 데이터를 송신하는 것
- 퍼블리셔 : 퍼블리시를 수행하기 위하여 토픽을 포함한 자신의 정보들을 마스터에 등록
- 서브스크라이브 : 토픽의 내용에 해당하는 메시지 형태의 데이터를 수신하는 것
- 서브스크라이버 서브스크라이브를 수행하기 위하여 토픽을 포함한 자신의 정보들을 마스터에 등록, 구독하고자하는 토픽을 퍼블리시하는 퍼블리셔 노드의 정보를 마스터로 받음
- 서비스 : 특정 목적의 작업에 해당되는 서비스를 요청
- 서비스 서버 : 요청을 입력받고, 응답을 출력으로 하는 서비스 메시지 통신의 서버 역할
- 서비스 클라이언트 : 요청을 출력하고, 응답을 입력으로 받는 서비스 메시지 통신의 클라이언트 역할
- 액션 : 서비스처럼 양방향을 요구하나 요청 처리 후 응답까지 오랜 시간이 걸리고 중간 결괏값이 필요한 경우 사용되는 메시지 통신 방식
- 액션 서버 : 액션 클라이언트로부터 목표를 입력 받고 결과 및 피드백 값을 출력하는 메시지 통신의 서버 역할
-  액션 클라이언트 : 목표를 출력하고, 액션 서버로부터 결과 및 피드백 값을 입력으로 받는메시지 통신의 클라이언터 역할
- 파라미터 : 노드에서 사용되는 파라미터
- 파라미터 서버 : 각 파라미ㅓ를 등록하는 서버
- 캐킨： ROS의 빌드 시스템
- ROS 빌드 : catkin 빌드 시스템 이전에 사용되었던 빌드 시스템
- roscore : ROS 마스터를 구동하는 명령어
- rosrun : ROS의 기본 실행 명령어
- roslaunch : 여러 노드를 실행하는 명령어
- bag : 메시지의 데이터를 저장할 수 있는데 이때 사용되는 파일 포맷
- ROS Wiki : ROS의 기본적인 설명은 물론 ROS에서 제공하는 각 패키지와 기능들을 설명하는 위키 기반의 페이지
- 리포지토리 : 각 패키지의 위키에 리포지토리를 명시하고 있음
- 그래프 : 노드, 토픽, 퍼블리셔, 서브스크라이버 의 관계를 그래프를 통해 시각적으로 나타낸 것
- 네임 : 노드, 파라미터, 토픽, 서비스의 이름
- 클라이언트 라이브러리 : ROS의 사용되는 언어의 의존성을 낮추기 위한 것
- URI : 인터넷에 있는 자원을 나태내는 유일한 주소
- MD5 : 128bit 암호화 해시 함수
- RPC : 컴퓨터 프로그램이 다른 주소 공간에서 원격 제어를 위한 프로그래머의 세세한 코딩 없이 함수나 프로시저의 실행을 허용하는 기술
- XML : 다목적 마크업 언어
- XMLRPC : 
- TCP/IP : 전송제어 프로토콜
- CMakeLists.txt : 빌드 환경이 기술되어 있는 문서
- package.xml : 패키지의 이름, 저작자, 라이선스, 의존성 패키지 등을 기술하고 있는 XML 파일

# 5장 ROS 명령어 정리
### 5.1 ROS 명령어 정리

#### ROS 쉘 명령어
명령어 | 명령어 풀이 | 세부 설명 |
---- | ---- | ---- |
roscd | ros + cd | 지정한 ROS 패키지의 디렉터리로 이동 |
rosls | ros + ls | ROS 패키지의 파일 목록 확인 |
rosed | ros + ed | ROS 패키지의 파일 편집 |
roscp | ros + cp | ROS 패키지의 파일 복사 |
rospd | ros + pushd | ROS 디렉터리 인덱스에 디렉터리 추가 |
rosd | ros + d | ROS 디렉터리 인덱스 확인 |

#### ROS 실행 명령어
명령어 | 명령어 풀이 | 세부 설명 |
---- | ---- | ---- |
roscore | ros + core | master(ROS 네임 서비스), rosout(로그 기록), parameter server(파라미터 관리) |
rosrun | ros + run | 노드 실행 |
roslaunch | ros + launch | 노드를 여러개 실행 및 실행 옵션 설정 |
rosclean | ros + clean | ROS 로그 파일을 검사하거나 삭제 |

#### ROS 정보 명령어
명령어 | 명령어 풀이 | 세부 설명 |
---- | ---- | ---- |
rostopic | ros + topic | ROS 토픽 정보 확인 |
rosservice | ros + service | ROS 서비스 정보 확인 |
rosnode | ros + node | ROS 노드 정보 확인 |
rosparam | ros + param | ROS 파라미터 정보 확인, 수정 |
rosbag | ros + pag | ROS 메시지 기록, 재생 |
rosmsg | ros + msg | ROS 메시지 정보 확인 |
rossrv | ros + srv | ROS 서비스 정보 확인 |
rosversion | ros + version | ROS 패키지 및 배포 릴리즈 버전 정보 확인 |
roswtf | ros + wtf | ROS 시스템 검사 |

#### ROS 캐킨 명렁어
명령어 | 세부 설명 |
---- | ---- |
catkin_create_pkg | 캐킨 빌드 시스템으로 패키지 자동생성 |
catkin_make | 캐킨 빌드 시스템에 기반을 둔 빌드 |
catkin_eclipse | 캐킨 빌드 시스템으로 생성한 패키지를 이클립스에서 사용할 수 있게 변경 |
catkin_prepare_release | 릴리즈할 때 사용되는 로그 정리 및 버전 태깅 |
catkin_generate_changelog | 릴리즈할 때 CHANGELOG.rst 파일 생성 또는 업데이트 |
catkin_init_worksplace | 캐킨 빌드 시스템의 작업 폴더 초기화 |
catkin_find | 캐킨 검색 |

#### ROS 패키지 명령어
명령어 | 명령어 풀이 | 세부 설명 |
---- | ---- | ---- |
rospack | ros + pack | ROS 패키지와 관련된 정보보기 |
rosinstall | ros + install | ROS 추가 패키지 설치 |
rosdep | ros + dep | 해당 패키지의 의존성 파일 설치 |
roslocate | ros + locate | ROS 패키지 정보 관련 명령어 |
roscreate-pkg | ros + create-pkg | ROS 패키지 자동 생성 |
rosmake | ros + make | ROS 패키지 빌드 |

# 7장 ROS 기본 프로그래밍
### 7.1 ROS 프로그래밍 전에 알아둬야 할 사항

#### 표준 단위
Quantity | Unit |
---- | ---- |
length | meter |
mass | kilogram |
time | second |
current | ampere |

Quantity | Unit |
---- | ---- |
angle | radian |
frequency | hertz |
force | newton |
power | watt |
voltage | volt |
temperature | celsius |

#### 좌표 표현 방식
- x : forward, y : left, z : up
- 오른손 법칙

![image](https://user-images.githubusercontent.com/57993534/125946909-9722f41b-6a73-4185-ad5a-d3d9ac92f0e3.png)

#### 프로그래밍 규칙
대상 | 명명 규칙 | 예제 |
---- | ---- | ---- |
패키지 | under_scored | first_ros_package |
토픽, 서비스 | under_scored | raw_image |
파일 | under_scored | turtlebot3_fake.cpp |
네임스페이스 | under_scored | ros_awesome_package |
변수 | under_scored | string table_name; |
타입 | CamelCased | typedef int32_t PropertiesNumber; |
클래스 | CamelCased | class UrlTable |
구조체 | CamelCased | struct UrlTableProperties |
열거형 | CamelCased | enum ChoiceNumber |
함수 | CamelCased | addTableEntry(); |
메소드 | CamelCased | void setNumEntries(int32_t num_entries) |
상수 | ALL_CAPITALS | const uint8_t DAYS_IN_A_WEEK = 7; |
매크로 | ALL_CAPITALS | #define PI_ROUNDED 3.0 |

### 7.2 퍼블리셔와 서브 스크라이버 노드 작성 및 실행

#### 패키지 생성
```
$ cd ~/catkin_ws/src
$ catkin_create_pkg ros_tutorials_topic message_generation std_msgs roscpp
```
```
$ cd ros_tutorials_topic
$ ls
```

#### 패키지 설정 파일
```
$ getdit package.xml
<?xml version=“1.0”?>
<package>
<name>ros_tutorials_topic</name>
<description>ROS tutorial package to learn the topic</description>
<license>Apache License 2.0</license>
<author email=“pyo@robotis.com”>name</author>
<maintainer email=“po@robotis.com”>name</maintainer>
<url type=“bugtracker”>https://github.com/ROBOTIS-GIT/ros_tutorials/issues
</url>
<url type=“bugtracker”>https://github.com/ros_tutorials.git</url>
<buildtool_depend>catkin</buildtool_depend>
<build_depend>roscpp</build_depend>
<build_depend>std_msgs</build_depend>
<build_depend>message_generation</build_depend>
<run_depend>roscpp</run_depend>
<run_depend>std_msgs</run_depend>
<run_depend>message_runtime</run_depend>
<export></export>
</pakage>
```

#### 빌드 설정파일
```
$ gedit CMakeLists.txt
```

#### 메시지 파일 설정
```
add_message_files(FILES MsgTutorial.msg)
```
```
$ roscd ros_tutorials_topic
$ mkdir msg
$ cd msg
$ gedit MsgTutorial.msg
```
```
time stamp
int 32 data
```

#### 퍼블리셔 노드 작성
```
add_executable(topic_publisher src/topic_publisher.cpp)
```
```
$ roscd ros_tutorials_topic/src
$ gedit topic_publisher.cpp
```

#### 서브스크라이버 노드 작성
```
add_executable(topic_subscriber src/topic_subscriber.cpp)
```
```
$ roscd ros_tutorials_topic/src
$ gedit topic_subscriber
```
```
$ cd ~/catkin_ws
$ catkin_make
```

#### 노드 빌드

#### 퍼블리셔 실행
```
$ roscore
$ rosrun ros_tutorials_topic topic_publisher
```
```
$ rostopic list
/ros_tutorial_msg
/rosout
/rosout_agg
```
```
/rostopic echo /ros_tutorial_msg
```

#### 서브스크라이버 실행
```
$ rosrun ros_tutorials_topic topic_subscriber
```

#### 실행된 노드들의 통신 상태 확인
```
$ rqt_graph 또는 $ rqt
```

### 7.3 서비스 서버와 클라이언트 노드 작성 및 실행

#### 패키지 생성
```
$ cd ~catkin_ws/src
$ catkin_create_pkg ros_tutorials_service message_generation std_msgs roscpp
```

#### 패키지 설정 파일 수정
```
$ gedit package.xml
```

#### 패키지 설정 파일 수정
```
$ gedit CMakeList.txt
```

#### 서비스 파일 작성
```
add_service_files(FILES SrvTutorial.srv)
```
```
$ roscd ros_tutorilas_service
$ mkdir srv
$ cd srv
$ gedit SrvTutorial.srv

int64 a
int64 b
---
int64 result
```

#### 서비스 서버 노드 작성
```
add_executable(service_server src/service_server.cpp)
```
```
$ roscd ros_tutorials_service/src
$ gedit service_server.cpp
```
```
#include “ros/ros.h”
#include “ros_tutorials_service/SrvTutorial.h”

// 서비스 요청이 있을 경우, 아래의 처리를 수행한다.
// 서비스 요청은 req, 서비스 응답은 res로 설정하였다.
bool clculation(ros_tutorials_service::SrvTutorial::Request &req,
		ros_tutorials_service::SrvTutorial::Response &res){중략}
int main(int argc, char **argv)
{ 중략 }
```

#### 서비스 클라이언트 노드 작성
```
add_executable(service_clinet src/service_client.cpp)

$roscd ros_tutorials_service/src
$gedit service_client.cpp
```

#### 노드 빌드
```
$ cd ~/catkin_ws && catkin_make
```

#### 서비스 서버 실행
```
$ rosrun ros_tutorials_service service_server
[INFO] [149526541.26862964]: ready srv server!
```

#### 서비스 클라이언트 실행
```
$ rosrun ros_tutorials_service service_client 2 3
[INFO] [1495726543.277216401]: send srv, srv.Request.a and b: 2, 3
[INFO] [1495726543.277258018]: receive srv, srv.Response.result: 5
```

#### rosservice call 명령어 사용방법
```
$ rosservice call /ros_tutorial_srv 10 2
result: 12

int64 a
int64 b
---
int64 result
```

#### GUI 도구인 Service Caller 사용 방법
```
$ rqt
```
```
$ cd ~/catkin_ws/src
$ git clone https://github.com/ROBOTIS-GIT/ros_tutorials.git
$ cd ~/catkin_ws
$ catkin_make
```
```
$ rosrun ros_tutorials_service service_server
$ rosrun ros_tutorials_service service_client 2 3
```

### 7.4 액션 서버와 클라이언트 노드 작성 및 실행

#### 패키지 생성
```
$ cd ~/catkin_ws/src
$ catkin_create_pkg ros_tutorials_action message_generation std_msgs actionlib_
msgs actionlib roscpp
```

#### 패키지 설정 파일 수정
```
$ roscd ros_tutorials_action
$ gedit package.xml
```

#### 빌드 설정 파일 수정
```
$ gedit CMakeLists.txt
```

#### 액션 파일 작성
```
add_action_files(FILES Fibonacci.action)
```
```
$ roscd ros_tutorials_action
$ mkdir action
$ cd action
$ gedit Fibonacci.action
```

#### 액션 서버 노드 작성
```
add_executable(action_server src/action_server.cpp)
```
```
$ roscd ros_tutorials_action/src
$ gedit action_server.cpp
```

#### 액션 클라이언트 노드 작성
```
add_executable(action_client src/action_client.cpp)
```
```
$ roscd ros_tutorials_action/src
$ gedit action_client.cpp
```

#### 노드 빌드
```
$ cd ~/catkin_ws && catkin_make
```

#### 액션 서버 실행
```
$ rosrun ros_tutorials_action action_server
```
```
$ rostopic list
/ros_tutorial_action/cancel
/ros_tutorial_action/feedback
/ros_tutorial_action/goal
/ros_tutorial_action/result
/ros_tutorial_action/status
/rosout
/rosout_agg
```
```
$ rostopic list –v
Publicshed topics:
* /ros_tutorial_action/feedback [ros_tutorials_action/FibonacciActionFeedback] 1 publisher
* /ros_tutorial_action/status [actionlib_msgs/GoalStatusArray] 1 publisher
* /rosout [rosgraph_msgs/Log] 1 publisher
* /ros_tutorial_action/result [ros_tutorials_action/FibonacciActionResult] 1 
publisher
* /rosout_agg [rosgraph_msgs/Log] 1 publisher

Subscribed topics:
* /ros_tutorial_action/goal [ros_tutorials_action/FibonacciActionGoal] 1 subscri
ber
* /rosout [rosgraph_msgs/Log] 1 subscriber
* /ros_tutorial_action/cancel [actionlib_msgs/GoalID] 1 subscriber
```
```
$ rqt_graph
```

#### 액션 클라이언트 실행
```
$ rosrun ros_tutorials_action action_client
```
```
$ rosrun ros_tutorials_action action_server
$ rosrun ros_tutorials_action action_client
```
```
$ rostopic echo /ros_tutorial_action/feedback
```
```
$ cd ~/catkin_ws/src
$ git clone https://github.com/ROBOTIS-GIT/ros_tutorials.git
$ cd ~/catkin_ws
$ catkin_make
```
```
$ rosrun ros_tutorials_action action_server
$ rosrun ros_tutorials_action action_client
```

### 7.5 파라미터 사용법

#### 파라미터를 활용한 노드 작성
```
$ roscd ros_tutorials_service/src
$ gedit service_server.cpp
```

#### 파라미터 설정
```
nh.setParam(“calculation_method”, PLUS);
```

#### 파라미터 읽기
```
nh.getParam(“calculation_method”, g_operatior);
```

#### 노드 빌드 및 실행
```
$ cd ~/catkin_ws && catkin_make
```
```
$ rosrun ros_tutorials_service service_service
[INFO] [1495767130.149512649]: ready srv server!
```

#### 파라미터 목록 보기
```
$ rosparam list
/calculation_method
/rosdistro
/rosversion
/run_id
```

### 7.6 roslaunch 사용법

#### roslaunch의 활용
```
$ roscd ros_tutorials_topic
$ mkdir launch
$ cd launch
$ gedit union.launch
```
```
$ roslaunch ros_tutorial_topic union.launch --screen
```
```
$ rosnode list
/rosout
/topic_publisher1
/topic_publisher2
/topic_subscriber1
/topic_subscriber2
```

#### union.launch 파일 수정
```
$ roscd ros_tutorials_topic/launch
$ gedit union.launch
```

#### Launch 태그
태그 | 설명 |
---- | ---- |
launch | roslaunch 구문의 시작과 끝을 가리킨다. |
node | 노드 실행에 대한 태그이다. 패키지, 노드명, 실행명을 변경할 수 있다. |
machine | 노드를 실행하는 PC의 이름, address, ros-root, ros-package-path 등을 설정할 수 있다. |
include | 다른 패키지나 같은 패키지에 속해 있는 다른 launch를 불러와 하나의 launch 파일처럼 실행할 수 있다. |
remap | 노드 이름, 토픽 이름 등의 노드에서 사용 중인 ROS 변수의 이름을 변경할 수 있다. |
<env | 경로, IP 등의 환경변수를 설정한다. |
param | 파라미터 이름, 타입, 값 등을 설정한다. |
rosparam | rosparam 명령어처럼 load, dump, delete 등 파라미터 정보의 확인 및 수정한다. |
group | 실행되는 노드를 그룹화할 때 사용한다. |
test | 노드를 테스트할 때 사용한다. <node>와 비슷하지만 테스트에 사용할 수 있는 옵션들이 추가되어 있다. |
avg | launch 파일 내에 변수를 정의할 수 있어서 다음과 같이 실행할 때 파라미터를 변경시킬 수도 있다. |

```
<launch>
	<arg name=“update_period” default=“10” />
	<param name=“timing” value=“$(arg update_period)”/>
</launch>
```
```
$ roslaunch my_package my_package.launch update_period:=30
```

# 8장 로봇, 센서, 모터

### 8.1 로봇 패키지
- 대표적인 예 : 터틀봇

### 8.2 센서 패키지
- 센서의 종류
  + LDS (Laser Distance Sensor)
  + LIDAR(Light Detection And Ranging)
  + LRF(Laser Range Finders)
  + 리얼센스
  + 키텍트
  + 액션
  + 컬러 카메라
  + 관성 센서
  + 마이크로폰
  + 토크 제어

- 센서 패키지의 분류
  + 1D Ranger Finders : 저가 로봇을 만들 때 사용할만한 적외선 방식의 직선거리 센서
  + 2D Ranger Finders : 2차 평면상의 거리를 계측할 수 있는 센서로 주로 내비게이션에 많이 사용되는 센서
  + 3D Sensors : Intel 사의 RealSense, Microsoft 사의 Kinect, ASUS 사의 Xtion과 같은 3차원 거리 측정에 사용되는 센서
  + Audio/Speech Recongnition : 현재 음성인식 관련 부분 센서
  + Cameras : 물체 인식, 얼굴인식, 문자판독 등에 많이 사용되는 카메라의 드라이버, 각종 으용 패키지
  + Sensor Interfaces : USB 및 웹 프로토콜을 지원하는 센서는 적다. 아직까지도 많은 센서들은 마이크로프로세서에서 정보를 쉽게 얻을 수 있는 센서가 많다.

### 8.3 카메라
- USB 카메라 관련 패키지
  + libuvc-camera : UVC 표준을 사용하는 카메라들을 사용하기 위한 인터페이스 패키지
  + uvc-camera : 비교적 상세한 카메라 설정 변경이 있어 매우 편리함. 더욱이 카메라 두 대를 이용하여 스테레오 카메라를 이용할 수 있어서 스테레오 카메라를 생각하고 있다면 적절한 패키지
  + usb-cam : Bosch에서 사용하는 매우 간단한 카메라 드라이버
  +  freenect-camera, openni-camera, openni2-camera : kinect나 Xtion과 같은 심도 카메라를 위한 패키지
  + camera1394 : IEEE 1394규격인 FireWire를 이용하는 카메라를 위한 드라이버
  + prosilica-camera : 연구용으로 많이 사용되는 AVT사의 prosilica 카메라에 사용됨
  + pointgrey-camera-driver : 연구용으로 많이 사용되는 Point Grey Research 사의 Point Grey 카메라를 위한 드라이버
  + camera-calibration : James Bowman, Patrick Mihelich가 개발한 카메라 캘리브레이션 관련 패키지로 OpenCV 캘리브래이션 기능을 응용한 패키지

-USB 카메라 테스트
  + lsusb : 접속 확인
  + sudo apt-get install ros-kinetic-uvc-camera : uvc camera 패키지 설치
  + sudo apt-get install ros-kinetic-image-* : image 관련 패키지 설치
  + sudo apt-get install ros-kinetic-rqt-image-view
  + ros run uvc_vamera uvc_camera_node : uvc_camera 노드 실행
  + rostopic list : 토픽 메시지 확인

- 이미지 정보확인
  + rosrun image_view image_view image:=/image_raw : image_view 노드로 확인
  + rqt_image_view image:=/image_raw : rqt_image_view 노드로 확인
  + rviz : RViz로 확인

- 원격으로 이미지 전송
  + gedit ~/.bashrc : bashrc 파일 열기
  + rosrun uvc_camera uvc_camera node : uvc_camera_node 실행

- 카메라 캘리브레이션
  + sudo apt-get install ros-kinetic-camera-calibration :카메라 캘리브레이션 패키지 설치
  + rosrun uvc_camera uvc_camera_node
  + tar –xvzf calibrationdata.tar.gz : 카메라 파라미터 파일 생성

### 8.4 심도 카메라
- Depth Camera의 종류
  + ToF(Time of Flight)
  + 구조광(Structured Light)
  + 스테레오(Stereo)

- Depth Camera 테스트
  + sudo apt-get install ros-kinetic-librealsense ros-kinetic-relsense-camera : RealSense 관련 패키지 실행
  + roslaunch realsense_camera r200_nodelet_default.launch : r200_nodelet_default 런치 파일 실행

- Point Cloud Data의 시각화

- Point Cloud Data관련 라이브러리
  + Point Cloud Library
  + OpenNI

### 8.5 레이저 거리 센서
- LDS 센서의 거리 측정 원리
  + 레이저 광원이 물체에 반사되었을 때 발생하는 파장을 이용
  + 주의해야 할 점 :눈이 손상될 수 있음, 레이저가 반사되지 않는 물체는 측정 불가

- LDS 테스트
  + sudo apt-get install ros-kinetic-his-lfcd-lds-driver : his_lfcd_lds_driver 패키지 설치
  + sudo chmod a+rw /dev/ttyUSB0 : LDS 연결 및 사용 권한 변경
  + roslaunch his_lfcd_lds_driver hlds_laser.launch : hlds_laser 런치 파일 실행
  + rostopic echo /scan : scan 데이터 확인

- LDS 거릿값의 시각화 
  + rviz
  + roslauch hls_lfcd_lds_driver view_hlds_laser.launch

- LDS 활용
  + SLAM

### 8.6 모터 패키지
- 다이나믹 셀
  + 데이지 체인 방식
  + 제어명령 : U2D2
  + 직접제어 : OpenCR

- 공개 패키지 사용법
	
http://rosindex.github.io/stats/
	
http://www.ros.org/browse/list.php
	
- 패키지 검색
  + 검색 키워드를 검색하면 됨.

- 의존성 패키지 설치
  + 예 : find_object_2d
  + rospack list : 패키지 설치 확인

- 패키지 설치
  + sudo apt-get install ros-kinetic-find-object-2d : 바이너리 설치
  + cd ~/catkin_ws/src : 소스 설치

- 패키지 실행
  + roscore
  + rosrun uvc_camera uvc_camera_node
  + rosrun find_object_2d find_object_2d image:=image_raw
  + rostopic echo /object
  + rosrun find_object_2d print_objects_detected

# 9장 임베디드 시스템

### 9.1 OpenCR(Open-source Control for ROS)
- ROS를 지원하는 임베디드 보드
- 터틀봇3에서 메인 제어기

- 특징
  + 고성능
  + 아두이노 연산
  + 다양한 인터페이스
  + IMU 센서
  + 전원출력
  + 전원 핫스왑 : SMPS(Switched-Mode Poser Supply), 전원을 연결하면 자동으로 보드 전원은 배터리 전원에서 SMPS로 전환됨
  + 오픈 소스 : https://github.com/ROBOTIS_GIT/OpenCR

- 보드 사양
  + 하드웨어 사양
	
![image](https://user-images.githubusercontent.com/57993534/125944394-06a89344-06ba-49af-a915-ac6bcaa5d418.png)

- 플래시 메모리 앱
  + 1MB
  + 부트영역 + EEPROM을 에뮬레이션하는 영역 + 펌웨어 영역
  + 섹터 2개 사용 : 메모리 수명을 늘리기 위해서
  + IMU 센서
- MPU9250 자이로/가속도/지자계 센서
	
![image](https://user-images.githubusercontent.com/57993534/125944585-8cd0987d-6e0e-46f6-a32e-51730704efc9.png)

- 개발환경 구축
  + USB 포트 권한 설정
```
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/99-opencr-cdc.rules
$ sudo cp ./99-opencr-cdc.rules /etc/udev/rules.d
$ sudo ubdevadm control —reload-rules
$ sudo udevadam trigger

ATTRS{idVendor}==“0483” AATRS{idProduct}==“5740”, ENV{ID_MM_DEVICE_IGNOR E}=“1”, MODE:=“0666”
```

- 컴파일러 환경 설정
```
$ sudo apt-get install libncurses5-dev:i386
```
- 아두이노 IDE 설치
```
$ cd ~/tools/arduino-1.82
$ ./install.sh

$gedit ~/.bashc

export PATH=$PATH:$HOME/tools/arduino-1.8.2

$ source ~/.bashrc
```
- 아두이노 IDE 실행
```
$ arduino
```
- OpenCR 설정
```
https://raw.githubsercontent.com/ROBOTIS-GIT/OpenCR/master/arduino/opencr_release/
	
package_opencr_index.json
```
- 펨웨어 다운로드 확인
- 펌웨어 복구모드
- 부트로더 업데이트

### 9.2 rosserial

- ROS의 메시지, 토픽 그리고 서비스들을 시리얼 통신 기반으로 사용할 수 있도록 변환해주는 패키지
- 마이크로컨트롤러와 ROS를 사용하는 컴퓨터 간의 메시지 통신을 위한 중계자 역할
	
![image](https://user-images.githubusercontent.com/57993534/125944959-74ab77d0-2087-4dd0-bd0d-7d3d56c0008d.png)

- rosserial server
  + rosserial_python : Python 언어로 구현, 매우 많이 사용됨
  + rosserial_server : C++ 언어 사용, rosserial_python 보다는 기능이 제약적
  + rosserial_java : java 언어, 안드로이드 SDK와 함께 사용할 때

- rosserial clinet
  + rosserial_arduino : 아두이노 보드(UNO, Leonardo) 지원, OpencCR은 수정하여 사용 중
  + rosserial_embeddedlinux : 임베디드용 리눅스에서 사용가능한 라이브러리
  + rosserial_windows : 윈도우 운영체제를 지원하고 윈도우의 응용프로그램과 통신 지원
  + rosserial_mbed : ARM사의 mbed 지원
  + rosserial_tivac : TI사의 Launchpad보드에서 지원

- rosserial 프로토콜
- 패킷구성 
	
![image](https://user-images.githubusercontent.com/57993534/125945118-76a94b6a-c5a5-4e38-ad2d-5b6ffb819562.png)

  + Sync Flag 패킷의 시작 위치를 알기 위한 헤더로 항상 0xFF
  + Sync Flag / Protocol version : ROS Groovy는 0xFF, ROS Hydro,Indigo, Jade, Kinetic OxFE
  +  Messafe Length : 패킷을 통해 전송되는 메시지의 데이터 길이 헤더, 2byte, Low → Hight 순으로 전송
  + Checksum over message length : 메시지 유효성 검증
```
255 - (Message Length Low Byte + Message Length High Byte)%256
```
  + Topic ID : 메시지의 형태를 구분하기 위한 ID
  + Serialized Message Data : 송/수신 메시지를 시리얼 형태로 전송하기 위한 데이터
  + Checksum over topic ID and Message Data : Topic ID의 유효성 검증
```
255 - ((Topic ID Low Byte + Topic ID High Byte + data byte values) % 256)
```
  + 쿼리 패킷 : rosserial sever가 시작되면 client로 토픽 이름 토픽 타입 등의 정보를 요청하는 것, Topic ID 0, 데이터 사이즈 0
```
unit16 topic_id
string topic_name
string message_type
string md5sum
int32 buffer_size
```

- rosserial 제약사항
  + 메모리 : 퍼블리셔, 서브스크라이버 개수 및 송신, 수신 버퍼의 크기를 미리 정의해야 함
  + Float64 : 마이크로컨트롤러는 64비트 실수 연산을 지원하지 않아 32비트형으로 변경함
  + Strings : 문자열 데이터 String메시지 안에 저장하지 않고 외부에서 정의한 문자열 데이터의 포인터 값만 메시지에 저장함
  + Arrays : 메모리 제약사항으로 배열의 키기를 지정해서 사용
  + 통신 속도 : UART 같은 경우 115200bps와 같은 속도로는 메시지의 개수가 많아지면 응답 및 처리속도가 느려짐

- rosserial 설치
  + 패키지 설치
```
$ sudo apt-get install ros-kinetic-rosserial ros-kinetic-rosserial-server ros-kinet ic-rosserial-arduino
```
  + 라이브러리 생성
```
$ cd ~/Arduino/libraries/
$ rm –rf ros_lib
$ rosrun rosserail_arduino make_libraries.py
```
  + 통신포트 변경

#### 9.3 터틀봇 3 펌웨어
- 터틀봇 3 버거 펌웨어
  + IDE에서 File → Examples → turtlebot3 → turtlebot3_burger → turtlebot3_core에서 upload
- 터틀봇3 와플과 와플 파이 펌웨어
  + File → Example → turtlebot3 → turtlebot3_waffle → turtlebot3_core

- 터틀봇3 설정 펌웨어
  + 설정 펌웨어 다운로드
  + turtlebot3_setup → turtlebot3_setup_motor
  + 다이나믹 셀 설정 변경
  + 다이나믹 셀 테스트

# 10장 모바일 로봇

### 10.1 ROS 지원로봇
- http://robots.ros.org/ 에서 확인 가능
- 180여 가지
- 터틀봇을 중심으로 다룸

### 10.2 터틀봇 시리즈
- ROS 표준 플랫폼 로봇
- 전 세계 수 많은 연구소, 학교, DIY에서 사용 중
- SLAM, Navigation, Gazebo, RViz 서포트(http://wiki.ros.org/Robots/TurtleBot)

### 10.3 터틀봇3 하드웨어
- TurtleBot3 Burger
- 360 LiDAR for SLAM & Navigation
- Scalable Structure
- Single Board Computer(Raspberry Pi)
- OpenCR(32-bit ARM Cortex-M7)
- DYNAMIXEL x 2 for Wheels
- Sproket Wheels for Tire and Caterpillar
- Li-Po Battery
- TurtleBot3 Waffle
- 60 LiDAR for SLAM & Navigation
- Single Board Computer(Intel Joule)
- Scalable Structure
- Intel RealSense for 3D Perception
- OpenCR(32-bit ARM Cortex-M7)
- DYNAMIXEL x 2 for Wheels
- Sproket Wheels for Tire and Caterpillar
- Li-Po Battery

### 10.4 터틀봇3 소프트웨어
- 터틀봇3 ROS 패키지
- turtlebot3
- turtlebot3_msgs
- turtlebot3_simulations
- turtlebot3_applications
- turtlebot3 패키지
- 로봇모델
- SLAM 및 내비게이션 패키지
- 원격제어 패키지
- 구동관련 bringup 패키지

### 10.5 터틀봇3 개발환경
	
![image](https://user-images.githubusercontent.com/57993534/125945490-a5e47cd9-bebd-4893-afac-9fdf21078283.png)

- Remote PC설치
```
$ cd ~/catkin_ws/src/
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make
```
- TurtleBot 설치
```
$ cd ~/catkin_ws/arc
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
$ git clone https://github.com/ROBOTIS-GIT/hls_lfcd_lds_driver.git
$ cd ~/catkin_ws $$ catkin_make
```
- Remote PC의 IP 값 확인 : ifconfig로 확인
- Remote PC의 ROS_HOSTNAME 및 ROS_MASTER_URI 설정
```
export ROS_HOSTNAME=192.168.7.100
export ROS_MASTER_URI=http://${ROS_HOSTNAME}:11311
```
- TurtleBot의 IP 값 확인
- TurtleBot3 SBC의 ROS_HOSNAME 및 ROS_MASTER_URI 설정
```
export ROS_HOSTNAME=192.168.7.200
export ROS_MASTER_URI=http://192.168.7.100:11311
```

### 10.6 터틀봇3 원격 제어

- 터틀봇3 조종하기
  + ros구동 : roscore
  + turtlebot3_robot.launch 런치파일 실행 
```
$ roslaunch turtlebot3_bringup turtlebot3_robot.launch --screen
```
  + turtlebot3_teleop_key.launch 런치파일 실행
```
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch —screen

$ sudo apt-ge isntall ros-kinetic-joy ros-kinetic-joystick-drivers ros-kinetic- teleop-twist-joy
$ roslaunch teleop_twist_joy teleop.launch --screen
```

- 터틀봇3 시각화
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_bringup turtlebot3_model.launch

$ ssh turtlebot@192.168.7.200
```

### 10.7 터틀봇3 토픽
```
$ roslaunch rurtlebot3_bringup turtlebot3_robot.launch —screen

$ rostopic list
/cmd_vel
/cmd_vel_rc100
/diagnostics
/imu
/joint_states
/odom
/rosout
/rosout_agg
/rpms
/scan
/sensor_state
/tf

$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch —screen

$rqt_graph
```

- 서브스크라이브 토픽
이름 | 형태 | 기능 |
---- | ---- | ---- |
motor_power | std_msgs/Boot | 다이나믹셀 모터 On/Off |
reset | std_msgs/Empty | 리셋(odometry 및 IMU) |
sound | turtlebot3_msgs/Sound | 비프음 소리 출력 |
cmd | geometry_msgs/Twist | 모바일 로봇의 병진 및 회전속도 제어, 단위는 m/s, rad/s 이용(실질적인 로봇 구동 제어) |

- 서브스크라이브 토픽으로 로봇 제어
  + rostopic pub으로 모터 정지
```
$ rostopic pub /motor_power std_msgs/Bool “data: 0”
```

  + 속도 제어
```
$ rostopic pub /cmd_vel geometry_msgs/Twist “linear:
x: 0.0
y: 0.0
z: 0.0
angular:
x: 0.0
y: 0.0
z: 1.0“
```

- 퍼블리시 토픽
이름 | 형태 | 기능 |
---- | ---- | ---- |
sensor_state | turtlebot3_msgs/SensorState | 터틀봇3에 실장된 센서들의 값을 확인할 수 있는 토픽 |
battery_state | sensor_msgs/BatterySTate | 배터리의 전압 등의 상태 값을 얻을 수 있음 |
scan | sensor_msgs/LaserScan | 터틀봇3에 탑재된 LDS로부터 스캔 값을 확인할 수 있는 토픽 |
imu | sensor_msgs/imu | 가속도 센서와 자이로 센서값을 기반으로 로봇의 방향값을 포함하는 토픽 |
odom | nav_msgs/Odometry | 엔코더와 IMU 정보를 기반으로 터틀봇3의 오도메트리 정보를 얻을 수 있음 |
tf | tf2_msgs/TFMessafe | 터틀봇3의 base_footprint, odom와 같은 좌표 변환 값을 가짐 |
joint_states | sensor_msgs/JointState | 좌/우측 바퀴를 조인트로 여겼을 때의 위치, 속도, 힘 등을 확인 가능함, 각 단위는 위치 : m, 속도 : m/s, 힘 : Nm |
diagnostics | diagnostic_msgs/DiagnosticArray | 자기 진단 정보를 얻을 수 있음 |
version_info | turtlebot3_msgs/VersionInfo | 터틀봇3의 하드웨어, 펌웨어, 소프트웨어의 등의 정보를 얻을 수 있음 |
cmd_vel_rc100 | geometry_msgs/Twist | 블루투스 기반의 조종기인 RC100을 이용했을 경우에 사용되는 토픽으로 모바일 로봇의 속도 제어에 사용되고 서브스크라이브하게 됨. 단위는 m/s, rad/s를 이용 |

- 퍼블리시 토픽으로 로봇 상태 파악
  + sensor_state : OpenCR에 연결된 아날로그 정보를 얻어옴.
```
$ rostopic echo /sensor_state
stamp:
secs 14000378811
nsecs: 475322065
bumper: 0
cliff: 0
left_encoder: 3570
right_encoder: 108553
battery: 12.0799999237
---
```

### 10.8 RViz를 이용한 터틀봇3 시뮬레이션
- 시뮬레이션
  + turtlebot3_simulations 메타패키지 이용

- 가상로봇실행
```
$ export TURTLEBOT3_MODEL=burger
$roslaunch turtlebot3_fake turtlebot3_fake.launch

$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.aluch
```
명령어 | 명령어 풀이 |
---- | ---- |
w | 전진 |
x | 후진 |
a | 시계 반대방향으로 회전 |
d | 시계 방향으로 회전 |
spacebar or s | 병진속도 및 회전속도 초기화 |
Ctrl + c | 종료 |

- Odometry와 TF
```
$ rosrun rqt_tf_tree rqt_tf_tree
```

### 10.9 Gazebo를 이용한 터틀봇3 시뮬레이션 

- 시뮬레이터 Gazebo
  + Gazebo특징
  + 동역학 시뮬레이션
  + 3차원 크래픽
  + 센서와 노이즈 지원
  + 플러그인 추가 기능
  + 로봇 모델
  + TCP/IP 데이터 전송
  + 클라우드 시뮬레이션
  + 명령줄 도구

- 가상로봇실행
```
$ export TURTLEBOT3_MODEL=waffle

$ roslaunch turtlebot3_gazebo turtlebot3_empty-world.launch

$ roslaunch turtlebot3_gazebo turtlebot3world.launch

$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_simulation.launch

$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_gazebo_rviz.launch
```

- 가상 SLAM과 내비게이션
  + 가상 SLAM 실행 순서
  + Gazebo 실행
```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
  + SLAM 실행
```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_slam turtlebot3_slam.launch
```
  + RViz 실행
```
$ export TURTLEBOT3_MODEL=waffle
$ rosrun rviz rviz –d ‘rospack find turtlebot3_slam’/rviz/turtlebot3_slam.rviz
```
  + 터틀봇 원격조종
```
$roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
  + 지도 출력
```
$ rosrun map-server map_server –f ~/map
```

  + 가상 내비게이션 실행 순서
  + Gazevbo 실행
```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
  + 내비게이션 실행
```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$
HOME/map.yml
```
  + RViz 실행 및 목적지 설정
```
$ export TURTLEBOT3_MODEL=waffle
$ rosrun rviz rviz –d ‘rospack find turtlebot3_navigation’ rviz/turtlebot3_nav .rviz
```
