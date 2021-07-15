## px4flow

![image](https://user-images.githubusercontent.com/57993534/125822925-f1ba257c-a3bd-4f3a-90fb-630fb699fe39.png)

- 조명 LED 없이 실내 및 실외 조명이 약한 조건에서 작동하는 광학 흐름 카메라
- 드론의 위치 제어와 옵티컬 플로우를 계산하는 가장 쉽고 가장 확립된 보드
(옵티컬 플로우 : 관찰자와 장면 사이의 상대적인 움직임에 의해 유발되는 시각적 장면에서의 물체, 표면 및 가장자리의 명백한 움직임의 패턴)
- 거리 센서와 함께 속도 추정을 위해 사용
- 기본적이고 효율적인 저수준 컴퓨터 비전 작업을 수행하도록 자유롭게 프로그래밍 가능
- 168MHz Cortex M4F CPU (128 + 64KB RAM)
- 752 x 480 픽셀 MT9V034 이미지 센서, L3GD20 3D 자이로
- 16mm M12 렌즈(IR 블록 필터)
- 크기 45.5mm x 35mm
- 소비 전력 115mA / 5V
- 400Hz에서 4x4 비닝 및 잘린 영역의 광학 흐름을 계산하여 매우 높은 감광도 제공
- 24 x 24 슈퍼 픽셀로 뛰어난 감광도
- USB 부트 로더, USB 전원 옵션, 최대 921600 baud의 USB 직렬
- 최대 2000/s 및 780Hz 업데이트 속도의 온보드 16 비트 자이로 스코프, 500/s의 기본 고정밀 모드
- PX4Flow의 기본 I2C 주소는 0x42
- 영상 화질과 출력 구성 가능

![image](https://user-images.githubusercontent.com/57993534/125823008-53b6b8a5-8106-4fe5-bfaa-7d541f057001.png)


## Pixhawk 설정
- Pixhawk에 연결하고 매개변수 SENS_EN_PX4FLOW를 설정하여 드라이버 활성화
- 장착 / 방향

![image](https://user-images.githubusercontent.com/57993534/125823044-0a3d1709-0b6f-40bd-8b4b-cdb0a1ec9fcf.png)

- PX4에서 방향은 SENS_FLOW_ROT 매개변수 사용해 설정(기본값 270)
- 상당한 양의 전자기 방사선을 방출하기 때문에 다른 전자장치(특히 GPS 모듈)로부터 멀리 떨어져 있어야 한다.


### PX4 구성 매개변수

|매개변수|설명|
|------|---|
|SENS_EN_PX4Flow|PX4 Flow 드라이버 시작|
|SENS_FLOW_MAXHGT|광학 흐름에 의존하는 경우 지상 최대 높이|
|SENS_FLOW_MINHGT|광학 흐름에 의존하는 경우 지상 최소 높이|
|SENS_FLOW_MAXR|광학 유량 센서가 신뢰성 있게 측정할 수 있는 최대 각도 유량|
|SENS_FLOW_ROT|차체 프레임에 상대적인 PX4FLOW 보드의 요 회전|

## 렌즈 포커싱
- 좋은 광학 흐름 품질을 보장하기 위해 초첨 맞춤
- QGroundControl px4flow 인터페이스를 이용

![image](https://user-images.githubusercontent.com/57993534/125823280-d7e1f911-8d77-4474-9fa5-9f68d213686e.png)

## 광학
- 초점 길이 렌즈 및 지상의 최대 속도

|지상 거리|1m|3m|10m|
|------|---|---|---|
|16mm 렌즈|2.4m/s|7.2m/s|24m/s|
|8mm 렌즈|4.8m/s|14.4m/s|48m/s|
|6mm 렌즈|6.4m/s|19.2m/s|64m/s|
|4mm 렌즈|9.6m/s|28.8m/s|96m/s|
