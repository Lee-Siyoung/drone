## yolo 설치
```
apt install git
git clone https://github.com/pjreddie/darknet.git
cd darknet
make
```

Makefile을 열어 GPU, CUDNN, OPENCV 값을 1로 수정한 후, make를 다시 입력

YOLOv3 기본 가중치 데이터를 가져온다
```
wget https://pjreddie.com/media/files/yolov3.weights		# 기본 버전
wget https://pjreddie.com/media/files/yolov3-tiny.weights	# Tiny 버전
```

해당 가중치를 사용하여 인식 테스트를 한다
```
./darknet detect cfg/yolov3.cfg yolov3.weights data/dog.jpg		# 기본 버전
./darknet detect cfg/yolov3-tiny.cfg yolov3-tiny.weights data/dog.jpg	# Tiny 버전
```

![image](https://user-images.githubusercontent.com/57993534/126030292-833846ad-e51d-4b20-9d6d-85983601a818.png)
