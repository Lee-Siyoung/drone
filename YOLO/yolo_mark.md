## yolo custom 학습을 위한 yolo_mark 
1. yolo_mark를 설치한다.
```
git clone https://github.com/AlexeyAB/Yolo_mark
cd Yolo_mark
```
```
cmake .
make
chmod u+x ./linux_mark.sh 
```
Yolo_mark/x64/Release/data로 이동 후 obj.data 클래스 개수 수정, obj.names 클래스 이름 수정.

Yolo_mark폴더로 가서 
```
./linux_mark.sh 
```
![image](https://user-images.githubusercontent.com/57993534/125822376-860237d1-5ffb-4a8f-9831-cc47b66b4a37.png)

- 스페이스바 : 넘어가기
- c : 박스 삭제
- 마우스 : 박스 그리기
