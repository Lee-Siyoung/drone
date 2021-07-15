## yolo 
#### 1. 하루 정도 돌린 결과 1737번 반복 학습하였습니다.

![image](https://user-images.githubusercontent.com/57993534/125824385-efbc0bb2-39d2-468b-95f5-2599c2b3b5ad.png)

current avg loss(손실률) : 0.0381
iteration(반복) : 1737
approx. time left(남은시간) : 6420.00 hours

#### 2. 일단 1700번 반복한 weight로 얼마나 정확률을 보이는지 확인했습니다.

![image](https://user-images.githubusercontent.com/57993534/125824416-c7b93f42-3c8c-43c3-a776-551819f86736.png)

학습에 사용하지 않은 사진으로 판별을 해보았습니다.
66%가 나왔습니다.
아직 학습한지 얼마 되지 않았기 때문에 좀 더 반복학습을 통해 정확률을 높일 예정입니다.

#### 3. realsense 카메라로 실시간 객체 인식을 했습니다.

![image](https://user-images.githubusercontent.com/57993534/125824436-b93c822c-9c81-4bc4-9ec3-f174a282b6ee.png)

realsense 카메라는  yolo에 웹캠으로 동작이 되지 않기 때문에 ros를 이용해 서로 토픽을 보내는 형식으로 yolo와 realsense 카메라를 연동하도록 했습니다.
darknet_ros(yolo를 간단히 동작할 수 있도록 한 ros 패키지)
realsense-ros(realsense 카메라를 ros에 동작할 수 있도록 한 ros 패키지)
이 두가지 패키지를 이용했습니다.
위의 사진은 기본 weight를 돌려 나온 결과이고 
사진에는 안나오지만 yolo-tiny 버전을 사용했기 때문에 FPS는 20~25가 나오고 정확률은 53%가 나왔습니다.
- yolo-tiny = 정확도는 낮지만 yolo보다 좀 더 가볍고 fps가 빠름.

#### 4. realsense 카메라로 실제 고라니, 멧돼지 사진 판별해보았습니다.

![image](https://user-images.githubusercontent.com/57993534/125824453-d689a34a-86e2-4692-a7a6-52e746954999.png)

![image](https://user-images.githubusercontent.com/57993534/125824460-92f8c43d-efe2-4da1-82cf-441ff8d966a7.png)

간단히 확인해보기 위해 사진을 앞에 두어 판별해보았습니다. 
custom weight이기 때문에 앞에 했던 것보다 무겁고 fps가 적게 나왔습니다.
고라니는 fps = 4 ~ 5, 정확률 = 90%
멧돼지는 fps = 4 ~ 5, 정확률 = 89%

앞으로의 과제는 fps를 늘리고 정확률을 높이는 것입니다.

![image](https://user-images.githubusercontent.com/57993534/125824480-ec201a2f-12f8-4c4f-a123-afbb677e9a3a.png)

/camera/realsense2_camera_manager/bond라는 토픽이 노드간 송수신하고 있는 모습입니다. /camera/realsense2_camera_manager/bond는 

#### Subscribed Topics 
- /camera_reading : 카메라 측정

#### Published Topics 
- object_detector : 감지 된 개체 수를 게시
- bounding_boxes : 경계 상자의 위치 및 크기 정보를 픽셀 좌표로 제공하는 경계 상자 배열을 게시
- detection_image : 경계 상자를 포함하여 감지 이미지의 이미지를 게시

#### Actions
- camera_reading : 이미지와 함께 작업을 전송하고 결과는 경계 상자의 배열로 나옴
