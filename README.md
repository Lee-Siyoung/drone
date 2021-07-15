유해조수 순찰드론
==========
4학년 졸업작품

참여자
----------
이시영
이종국
윤영운

# 기본 구성
## 1. 당위성

### 필요성
- 환경부에 따르면 2010년부터 2018년까지 야생동물에 의한 농작물 피해액은 1103억5500만원으로 한해 평균 120억여원에 달한다
- 농가들은 피해를 줄이고자 철조망과 그물망을 치고 감시를 늘리는 등 온갖 묘수를 짜내지만 별 소용이 없다고 호소한다.
- 환경부는 농작물 피해 예방 종합 대책을 만들어 피해 예방 시설 설치비를 지원하고 피해 방지단을 설치, 운영하기 시작했다.
- 하지만 효과가 큰 예방시설은 농가 자부담이 커 엄두를 못 내는 경우가 많으며, 농작물 피해 보상도 한도액이 턱없이 낮고 조건도 까다롭다.

![image](https://user-images.githubusercontent.com/57993534/125783870-4a519efa-a17b-4840-8168-1fb21b1c4f97.png)

<야생동물 피해보상액 지급 건수>


![image](https://user-images.githubusercontent.com/57993534/125784015-c4cb32dd-a744-472c-bf4a-d8057d8254da.png)


-  유해야생동물에 의한 농작물 및 인명피해 예방이 이루어지고 있지만 동물보호단체나 환경운동단체의 입장과 상반된다. 퇴치되어야 할 대상이지만 자연을 생각할 때는 없어서는 안될 존재이기 때문이다.


   
## 2. 시나리오
1) 드론 지정된 구역을 정기적으로 순찰한다.
2) 순찰간 움직이는 객체가 있으면 무엇인지 식별한다.
3) 유해조수 식별 시, 소음을 통하여 지정된 구역을 벗어 날 때까지 추적한다.
4) 유해조수가 지정된 구역을 벗어날 경우, 다시 지정된 구역으로 돌아가 순찰을 지속한다.

## 3. 기대효과
- 드론만 있으면 되기 때문에 울타리 설치는 시설물 설치가 따로 필요하지 않다.
- 유해동물을 포획하는 과정에서 존재하는 위험이 감소한다.
- 유해동물로부터 농작물을 보호함과 동시에 유해동물을 포획하지 않아도 된다.
- 직접 드론을 조종하는 것이 아니기 때문에, 언제든지 사용할 수 있다.
- 유해조수 뿐만 아니라 사람에 의한 범죄도 차단할 수 있다.

## 4. 문제점
- 소음 – 규모가 큰 농작지를 대상으로 하기 때문에 주에 민가가 있는 경우가 드물다.

## 5. 기술
### 1. 드론 구역 주행
  - 지정 구역 주행 - 자율비행
    + waypoint를 지정하여 지정된 구역에서 드론이 주행을 한다.

    ![image](https://user-images.githubusercontent.com/57993534/125784160-9e13a4fd-41a8-4edf-874c-0ff71ef0c21f.png)
    
    + https://github.com/eduardorasgado/ParrotDrone_moving_square
    + GeoFence(비행 구역지정)
      + 드론이 이동할 수 있는 위치를 정의하는 가상의 경계이다. GeoFence를 통해 순찰이 필요한 일정구역을 지정한다.
      + PX4는 포함(내부비행) 또는 제외(외부비행) 여역으로 정의될 수 있는 여러 원형 및 다각형 영역으로 구성된 GeoFence 경계를 지원한다.
      + GeoFence는 미션 및 랠리 포인트와 함께 QGroundControl에서 계획된다.
      
      ![image](https://user-images.githubusercontent.com/57993534/125784574-d86c86b5-a314-4b69-b85d-032e8e940160.png) 
      
  - Fly View
    + 비행 시 차량을 명령하고 모니터링을 하는 데 사용된다.
    + 자동화된 비행 전 체크리스트를 실행한다.
    + arm/disarm/emargency stop, take off/land, chage altitude, go to, or orbit 등을 지정할 수 있다.
    + 현재 차량에 대한 비디오, 임무, 원격 측정 및 기타 정보를 표시하고 연결된 차량 간에 전환할 수 있다.
    
    ![image](https://user-images.githubusercontent.com/57993534/125787088-08650508-5922-49a1-9558-973cd93621ad.png)

  - PX4 (자율 비행 프로그램)
    + 픽스호크는 원격조종 드론 및 자동 조종 장치는 무인 및 자율 항공기를 지향하는 오픈 소스 자동 조종 시스템이다.
    + 개발자 가이드
      + https://docs.px4.io/master/en/
    + QGroundControl
      + ArduPilot 또는 PX4 Pro 구동 차량에 대한 완전한 비행 제어 및 구성을 제공한다.
      + 기능
        + px4 pro 및 ArduPilot 펌웨어를 실행하는 차량에 대한 전체 구성 지원
        + 자율 비행을 위한 임무 계획
        + 차량 위치,비행 트랙, 웨이 포인트 및 차량 계기를 보여주는 비행지도 디스플레이
        + 모든 MAVLink 기능 차량에 대한 비행 지원

### 2. 객체 인식
  - CNN(Convolutional Neural Network)
  
    ![image](https://user-images.githubusercontent.com/57993534/125787741-7bc797e3-4038-4e11-95f1-21f138597b50.png)
    
    + 이미지 인식 처리 및 NLP 목적으로 사용되는 DNN이다
    + ConvNet이라고도하는 CNN에는 입력 및 출력 레이어와 여러 개의 숨겨진 레이어가 있으며 그 중 다수는 컨볼루션이다
  - YOLO : Real-Time Object Detection
    + 단일 단계 방식의 객체 탐지 알고리즘이다
    + 원본 이미지를 동일한 크기의 그리드로 나눈다. 각 그리드에 대해 그리드 중앙을 중심으로 미리 정의된 형태로 지정된 경계박스의 개수를 예측하고 이를 기반으로 신뢰도를 계산한다
    
    ![image](https://user-images.githubusercontent.com/57993534/125788160-c97081d1-4950-4fd1-8ab4-bea54a96cc3a.png)
    
    + YOLO와 호환되는 3가지 프레임 워크
	    + Darknet
	    + Darkflow
	    + Opencv : YOLO와 함께 작동하는 딥 러닝 프레임워크가 있다
    + 예시 Cat Chaser : 고양이만 쫓아내기 위해 만든 시스템
    
    ![image](https://user-images.githubusercontent.com/57993534/125788377-1fabe1d6-bdf9-4151-8914-a7d4e2181157.png)
    
    + IP카메라를 이용해 정원을 촬영합니다
    + 촬영중인 영상을 Photon Server로 보내줍니다
    + Photon Server는 Jetson TX1으로 영상을 보내줍니다
    + Jetson TX1은 FCN Algorithm을 통해서 고양이의 유무를 확인한 뒤 다시 Photon Server로 결과를 전송합니다
    + Photon Server는 고양이의 유무에 따라 스프링클러의 작동여부를 결정합니다
    
### 3. 객체 추적
  - Mean-Shift Algorithm
    + 데이터 집합에서 특짐정, 코너, 색상정보와 같은 밀도 분포를 기반으로 ROI 객체를 추적해나가는 알고리즘이다.
    + 입력 영상에서 살색 영역에 대한 히스토그램 백투영 확률적인 정보를 얻어낸다.
    + 기존 위치가 빨간 박스라고 가정하고 빨간 박스 안에 있는 픽셀들의 평균 값을 계산한다.
    + 평균이 살색의 픽셀값과 비슷한 곳으로 조금조금씩 이동한다. 이 작업을 반복하다보면 어느 순간 움직임이 없어지게 된다. 그때 Mean Shift 알고리즘이 수렴했다고 한다.
    + OpenCV에서는 cv2,meanShift 함수를 제공한다.
    
    ![image](https://user-images.githubusercontent.com/57993534/125789094-e8bd198e-3136-41a2-8aca-246c7a0ba74a.png)


  - BackgroundSubtractorMOG2 
    + MOG2는 가우시안 혼합 기반 배경 분할 알고리즘이다.
    + 가우시안 분산값 K(K=3~5)의 홉합에 의해 각 배경 픽셀을 구성하는 방법이다. 
    + 혼합의 가중치는 장면에서 이들 색상값들이 머무르고 있는 시간 비율이다. 배경으로써 판단될 수 있는 색상은 더 오랜 시간동안 변하지 않는 것이다.
    + 알고리즘 역시 OpenCV에서 v2.createBackgroundSubtractorMOG2() 함수로 실행 가능하다.

  - GAAS 소프트웨어를 이용한 자율 물체 추적
    + GAAS는 완전 자율 주행 드론과 비행 자동차를 위해 설계된 오픈 소스 자율 항공 소프트웨어 플롯폼이다.
    + https://gaas.gitbook.io/guide/software-realization-build-your-own-autonomous-drone/basic-object-tracking
    + https://www.reddit.com/r/ROS/comments/cazljn/tutorial_build_autonomous_drone_realtime_object/
