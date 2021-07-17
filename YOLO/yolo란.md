# 객체 탐지 
: 이미지가 주어지면 배경과 사물을 구분하고 어떤 사물인지 인지하는 것

# YOLO(You Only Look Once) 
기존 모델보다 더 높은 정확도를 추구하는 것이 아닌, 근접한 정확도를 가지면서 더 많은 양의 이미지를 처리할 수 있는 실시간 객체 탐지를 하고자 등장함. 물체인식(Object Detection)을 수행하기 위해 고안된 심층 신경망으로서, 테두리상자 조정(Bounding Box Coordinate)과 분류(Classification)를 동일 신경망 구조를 통해 동시에 실행하는 통합인식(Unified Detection)을 구현하는 것이 가장 큰 특징

### 특징
- 이미지 전체를 한 번만 봄
- 통합된 모델 사용
- 실시간 객체 탐지

![image](https://user-images.githubusercontent.com/57993534/125814748-c03cc0d2-9ad1-4f23-a7cb-9ace22b7be75.png)

<기존의 객체 탐지 모델과의 속도 비교>


- R-CNN(Regions with Convolutional Neural Networks)과 비교하면 R-CNN은 이미지에서 일정한 규칙으로 이미지를 여러장 쪼개서 CNN모델을 통과시키기 때문에 한 장의 이미지에서 객체 탐지를 수행해도 실제로는 수 천장의 이미지를 모델에 통과시킴. 반면, YOLO는 이미지 전체를 말 그대로 단 한 번만 봄
- 그래서 R-CNN은 느리고 실시간으로 예측할 수 없지만 YOLO는 빠르고 실시간으로 예측할 수 있음
- 다른 객체 탐지 모델들은 다양한 전처리 모델과 인공 신경망을 결합해서 사용하지만 YOLO는 단 하나의 인공신경망에서 이를 전부 처리하기 때문에 간단함
- 실시간으로 여러 장의 이미지를 탐지할 수 있음. YOLO는 보통 45FPS의 성능을 가짐

![image](https://user-images.githubusercontent.com/57993534/125815327-25fd9df6-d322-483c-a7cc-5568b19086c9.png)

[YOLO 시스템 모델]

### YOLO 분석

![image](https://user-images.githubusercontent.com/57993534/125815394-c8d92e6d-02d0-49fd-bc7e-fbe0e4bc6a68.png)

[이미지가 YOLO Model을 통과한 결과]

#### 1. 먼저 입력 이미지를 S x S 그리드 영역으로 나눠 줌
#### 2. 각각의 grid cell은 B개의 Bounding box와 각 Bounding box에 대한 confidence score를 갖는다. (만약 cell에 Object가 존재하지 않는다면 confidence score는 0이 됨) confidence score는 이 시스템이 물체를 포함한다는 예측을 얼마나 확신하는지, 박스에 대한 예측이 얼마나 정확할지를 의미함
  - confidence score : Pr(Object) * IOU
  - IOU(Intersection over Union) : 학습 데이터의 바운딩 박스와 예측한 바운딩 박스가 일치하는 정도를 나타냄. 즉, 두 영역이 겹쳐져 있을때 두영역의 교집합을 합집합으로 나눈 것. (겹쳐진 넓이) / (전체 넓이)로 됨. 만약 두 영역이 완전히 겹쳐져 있다면 겹쳐진 넓이가 곧 전체 넓이라서 IOU = 1이 됨
  - Pr(Object) :  셀격자 내에 물체가 존재할 확률, 물체가 존재하지 않으면 confidence = 0 * IOU =0이 됨. 시스템은 pr(Object)를 1에 가깝게 만들고 싶어하고, 그럴 경우 confidence = IOU가 됨. 즉, confidence에 대한 오차 수정이 곧 IOU에 대한 오차 수정으로 되는 것
각 그리드에서 중심을 그리드 안쪽으로 하면서 크기가 일정하지 않은 Bounding box 2개를 생성함. 이 중 Bounding box 안쪽에 어떤 Object가 있을 것 같다고 확신(confidence score)할수록 박스가 굵게 그려짐
#### 3. 각각의 bounding box는 x, y , w, h와 confidence로 구성됨
  - (x, y): Bounding box의 중심점을 의미하며, grid cell의 범위에 대한 상대값이 입력됨
  - (w, h) : 전체 이미지의 width, height에 대한 상대값이 입력됨
  - confidence : 예측 box와 실제 정답 사이의 IOU를 의미함. 이 값들은 모두 (0,1)범위의 값으로 정규화
  - ex1) 만약 x가 grid cell의 가장 왼쪽에 있다면 x = 0, y가 grid cell의 중간에 있다면 y=0.5
  - ex2) bbox의 width가 이미지 widht의 절반이라면 w = 0.5
#### 4. 각각의 grid cell은 C(conditional class probability)를 갖는다.
  - Conditional Class probability : Pr(class _{i} | Object)
#### 5. 각 박스의 confidence score를 구한다
ClassSpecifiConfidenceScore

=ConditionalClassProbability * ConfidenceScore

=Pr(Class _{i} | Object) * Pr(Objects) * IOU

=Pr(Class _{i}) * IOU
 
일정 값보다 작은 Bounding box들을 지워 굵은 Bounding box들만(4) 남김. 일정 값은 사용자가 설정. Bounding box의 색깔은 클래스를 의미함

### Custom 학습 및 검출하는 방법
#### YOLO_mark
- 이미 학습되어있는 자료가 아닌 직접 이미지를 학습시키기 위한 프로그램 YOLO학습을 위한 이미지에 bounded boxes 마킹을 해 Box의 좌표를 지정해줌
- Bounding Box를 그려 마킹해줌
- YOLO_mark로 마킹한 이미지를 학습시켜 weight 파일을 만들 수 있음

![image](https://user-images.githubusercontent.com/57993534/125816371-ef56e1a1-b0e7-4f11-9311-d5b445432f93.png)

이미지 크롤링(image crawling) 
- 웹 상에서 데이터를 수집하는 것을 크롤링이라고 하고, 수집하고자 하는 데이터가 이미지라면 데이터 크롤링이라 부름
이유 학습하는데 많은 이미지 데이터가 필요한데 일일이 이미지들을 하나씩 다운로드 하는 방식은 너무 손이 많이 가고 번거롭기 때문
- 파이썬으로 진행, 필요한 패키지는 beautifulsoup4, requests
- requests : 다양한 http 요청을 할 수 있는 라이브러리
- beautifulsoup4 : requests로 불러온 html 코드에서 의미있는 정보를 추출할 수 있게 도와주는 라이브러리, html 코드를 python이 이해하는 객체 구조로 변환하는 파싱(구문 분석)을 맡고 있다.

yolo는 이미지를 일정 크기의 그리드로 자른 뒤 학습하기 때문에 해상도와 상관없다. 대신 전체 이미지 대비 학습할 물체의 크기가 지나치게 작을 경우 형상이 뚜렷함에도 불구하고 제대로 검출이 되지 않는다.

![image](https://user-images.githubusercontent.com/57993534/125816534-cfb28a0a-f7df-47af-bfa5-6f6ddeb22739.png)

그리고 yolo 모델 레이어 구조에 업샘플링을 할 수 있는 픽셀이 있기 때문에 너무 낮은 해상도도 충분히 학습하고 인식할 수 있다.
- 업 샘플링(up-sampling) : 저해상도에서 고해상도로 이미지 업스케일링(upscaling)할 때 사용, 픽셀과 픽셀 사이에 새로운 픽셀을 끼워 넣어 화질을 높여주는 기술

![image](https://user-images.githubusercontent.com/57993534/125816552-0ad6aa15-bdcd-42f1-83e9-977f652520aa.png)

## yolo를 선택한 이유
#### 1. 
주제가 유해조수를 탐지하고 추적하는 것이기 때문에 실시간으로 빨리 움직이는 동물들을 추적하는데 cnn 계열보다는 yolo이 더 좋다.

![image](https://user-images.githubusercontent.com/57993534/125819543-455cffb5-635f-4787-99b2-cb386ace0691.png)

<기존의 객체 탐지 모델과의 속도 비교>

https://www.youtube.com/watch?v=NM6lrxy0bxs

1분59초 ~ 2분40초 부분을 보면 0.5FPS – 6FPS – 30FPS순으로 프레임에 따른 감지 속도를 보여주고 있다. 만약 faster R-CNN이나 faster R-CNN을 쓴다면 순식간에 움직이는 동물들을 추적하는데 어려움이 따를 수 있기 때문에 yolo은 필수적이라 생각한다.

고라니 속도 https://www.youtube.com/watch?v=ZxgHYYgBQhQ

멧돼지 속도 https://www.youtube.com/watch?v=yoN8snPDprQ

#### 2. 
Jetson Nano는 성능이 좋지 않기 때문에 fast-rcnn모델은 Jetson Nano에 비해 매우 크다. 그리고 모델 자체가 복잡하기 때문에 tensorRT같은 nvidia에서 제공하는 딥러닝 SDK에서 즉시 작동하지 않는다. 지원되지 않는 노드가 많이 있어 fast-rcnn을 쓸려면 많은 사전처리가 필요하다. 그에 반에 yolo는 nvidia에서 공식 tensorRT yolo샘플이 있기 때문에 Jetson Nano에서 적용하기 쉽다. 그렇기 때문에 적용하기 쉬운 yolo를 써야한다.

#### 3.
Jetson Nano에서 실제 yolo를 돌리면 5 ~ 10fps정도가 나온다.

ex) https://www.youtube.com/watch?v=keuYwbkZz7c

그리고 fps를 더 높이고 싶다면 nvidia에서 제공하는 DeepStream 딥러닝 SDK를 이용해 20 ~ 25fps까지 높일 수 있다.

https://forums.developer.nvidia.com/t/deepstream-gst-nvstreammux-change-width-and-height-doesnt-affect-fps/83286#5392823

그리고 yolo에는 다른 모델들과 달리 yolo-tiny라고 경량화를 시킨 모델이 있다. yolo-tiny를 쓰면 fps가 10정도 더 늘어나게 할 수 있다.

ex) https://www.youtube.com/watch?v=7icaFX8qetE

다른 모델들은 yolo와 달리 경량화 모델이 없기 때문에 드론에서 실시간으로 처리한다면 드론에 가하는 부담이 커진다. 그에 반에 yolo-tiny는 용량도 작고 가볍기 때문에 실시간으로 드론에서 처리하는데 좋기 때문에 yolo를 써야한다.
