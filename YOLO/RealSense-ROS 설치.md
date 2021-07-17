## RealSense-ROS
RealSense를 ROS로 구동할 수 있는 패키지

https://github.com/IntelRealSense/realsense-ros
```
# 1. install realsense2_camera
export ROS_VER=melodic
sudo apt-get install ros-$ROS_VER-realsense2-camera

# 2. install realsense SDK, 이미 realsense 설치했으면 넘어가기
sudo apt-get install librealsense2-utils
sudo apt-get install librealsense2-dev

# 3. Install Intel® RealSense™ ROS from Sources
# 3.1) Create a catkin workspace Ubuntu
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/src/

# 3.2) Clone the latest Intel® RealSense™ ROS from here into 'catkin_ws/src/'
git clone https://github.com/IntelRealSense/realsense-ros.git
cd realsense-ros/
git checkout `git tag | sort -V | grep -P "^2.\d+\.\d+" | tail -1`
git checkout -b 2.2.22

# 3.3) Clone ddynamic_reconfigure into 'catkin_ws/src/'
git clone https://github.com/pal-robotics/ddynamic_reconfigure.git

# 3.4) catkin make
# 'catkin_ws/src/'
catkin_init_workspace
cd ..

# 'catkin_ws/'
catkin_make clean
catkin_make -DCATKIN_ENABLE_TESTING=False -DCMAKE_BUILD_TYPE=Release
catkin_make install

echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

catkin에서 에러날 시

![image](https://user-images.githubusercontent.com/57993534/126032120-a0bf9101-c24d-46cf-ad65-d7c2442e4d11.png)
```
cd /opt/ros/melodic/share/cv_bridge/cmake
sudo gedit cv_bridgeConfig.cmake
```
cv_bridgeConfig.cmake 파일 수정

![image](https://user-images.githubusercontent.com/57993534/126032168-f75d3a02-f7f9-46a7-ae16-dae2a7f89102.png)

if문 조건 안에 _include_dirs에 본인의 opencv 디렉터리 위치 입력
(출처. https://95mkr.tistory.com/entry/ROS6)

realsense 노드 키기
```
roslaunch realsense2_camera rs_camera.launch
```
