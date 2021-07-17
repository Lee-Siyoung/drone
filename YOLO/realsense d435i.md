## realsense d435i 설치
```
# server's public key 등록
sudo apt-key adv --keyserver keys.gnupg.net --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE || sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE

# 서버추가(Ubuntu 18.04)
sudo add-apt-repository "deb http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo bionic main" -u

# 라이브러리 설치
sudo apt-get install librealsense2-dkms
sudo apt-get install librealsense2-utils

# Debug Package, Developer 설치(선택사항)
sudo apt-get install librealsense2-dev
sudo apt-get install librealsense2-dbg

# ROS Package 설치
sudo apt-get install ros-$$ROS_VER-realsense2-camera

# realsense-viewer 실행
realsense-viewer
```
![image](https://user-images.githubusercontent.com/57993534/126031747-b559841f-9fce-4836-891d-5849c0288a3d.png)
