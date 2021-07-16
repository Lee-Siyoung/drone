## GPS 연결
### RTCM 메시지
- RTCM 베이스 위치 메시지(1005)의 길이 : 22byte
- 가시 범위의 위성 숫자와 위성 신호수에 따라 길이가 달라짐

- 1005 : 안테나 참조 지점 값인 스테이션 좌표 XYZ 값(베이스 위치).
- 1077 : 전체 GPS 가상 범위, 캐리어 위상, 도플러 신호 세기 (고해상).
- 1087 : 전체 GLONASS 가상 범위, 캐리어 위상, 도플러 신호 세기 (고해상).
- 1230 : GLONASS 코드 위상 바이어스.
- 1097 : 전체 GLONASS 가상 범위, 캐리어 위상, 도플러 신호 세기 (고해상)
- 1127 : 전체 베이스 가상 범위, 캐리어 위상, 도플러 신호 세기 (고해상)

1. QGC에 GPS 연결하기

![image](https://user-images.githubusercontent.com/57993534/125954817-7f54fcd8-0303-4e5b-a354-d76ba45a7e4f.png)

Pixhawk4의 GPS 모듈
- Pixhawk4의 GPS모듈에 GPS 수신기뿐만아니라 지자계 센서와 부저가 함께 창착되어 있다.

Pixhawk4에 GPS 모듈 연결 후 baudrate(데이터 통신에서 시리얼 포트가 1초 동안 전송할 수 있는 최대 비트 크기)를 설정한다.

![image](https://user-images.githubusercontent.com/57993534/125954856-c38170f9-5952-4a6f-81f7-a2648a267aae.png)

2. QGC 펌웨어 설정

PX4 안정 버전을 설치하였다.

![image](https://user-images.githubusercontent.com/57993534/125954880-8378ae6a-1a52-4cd1-837c-2a44e17019df.png)

3. 센서 캘레브레이션

![image](https://user-images.githubusercontent.com/57993534/125954891-4917acf6-3056-4fe9-9ef8-2f2e78eee147.png)

4. GPS연결

Pixhawk에 각각의 Port는 다음과 같이 설정되어 있다.

![image](https://user-images.githubusercontent.com/57993534/125954904-fc96e1da-463f-4981-9975-62de60217057.png)

