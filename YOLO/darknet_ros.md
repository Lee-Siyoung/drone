## darknet_ros
ros에서 yolo 구동

workspace를 생성
```
## Create workspace for ROS, Change directory
mkdir -p workspace/src 
cd workspace/src

## init workspace
catkin_init_workspace

## Make
cd ../
catkin_make
```

깃헙에서 git 명령어를 활용하여 소스코드 가져오기
```
cd workspace/src
git clone --recursive git@github.com:leggedrobotics/darknet_ros.git
cd ../
```

소스코드 빌드
```
catkin_make -DCMAKE_BUILD_TYPE=Release
```

catkin 오류 시 https://github.com/Lee-Siyoung/drone/blob/main/YOLO/RealSense-ROS%20%EC%84%A4%EC%B9%98.md 참고

빌드 성공 시  yolov3와 관련된 파일을 다운받고 각 cfg, weight 파일은 ~/workspace/src/darknet_ros/darknet_ros/yolo_network_config/ 내의 cfg, weights 폴더에 각각 넣어줌

### 파일 수정
(1) ~/workspace/src/darknet_ros/darknet_ros/config/ 위치에서 yolov3.yaml 파일 생성 :

config_file과 weight_file의 name을 yolov3.cfg와 yolov3.weights로 수정.

(2) ~/workspace/src/darknet_ros/darknet_ros/config/ 위치에서 ros.yaml 파일 수정 :

ros.yaml 파일에서 camera_reading 부분의 topic을 자신의 카메라 환경에 맞게 바꿔줍니다.

리얼센스의 컬러 이미지 토픽이 /camera/color/image_raw여서 이렇게 수정(사용자마다 다를 수 있음).

(3) ~/workspace/src/darknet_ros/darknet_ros/launch/ 위치에서 darknet_ros.launch 파일 수정 :

Line 14 : yolov2.yaml -> yolov3.yaml 으로 수정

Line 6, 24 : 카메라 이미지 토픽이 다르다면, 토픽에 맞게 설정 (ex : /camera/color/image_raw)

## darknet_ros 실행
먼저 카메라 노드 실행(필자는 realsense의 컬러 이미지 노드 사용)
```
# 터미널 1 : 카메라 키기
roslaunch realsense2_camera rs_camera.launch
```
darknet-ros 노드 실행
```
# 터미널 2 : darknet_ros 구동
roslaunch darknet_ros darknet_ros.launch
```

![image](https://user-images.githubusercontent.com/57993534/126032567-af4e5d7e-5864-445a-8377-66fd31a033b4.png)

![image](https://user-images.githubusercontent.com/57993534/126032569-6905cd7c-3898-4bb2-bd81-07c25f6715a6.png)

![image](https://user-images.githubusercontent.com/57993534/126032571-7ec6ab7b-c19a-4024-9557-1bd91b4749ef.png)

(출처 : https://ropiens.tistory.com/67?category=905965)
