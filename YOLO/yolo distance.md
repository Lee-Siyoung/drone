### 1. yolo에 인식된 물체와 카메라 사이의 거리 측정 
- 고라니, 멧돼지 개체 동시 인식 및 거리 측정할 수 있음

![image](https://user-images.githubusercontent.com/57993534/125826599-ae2fe5a7-d049-45e6-b414-02db91162ebb.png)

![image](https://user-images.githubusercontent.com/57993534/125826613-d07b4989-b293-4741-ba0b-323bc401cfc3.png)

![image](https://user-images.githubusercontent.com/57993534/125826633-c92c6a1c-9e25-4d93-ae91-049e1238b7fa.png)

yolo로 물체가 인식이 되면 물체의 bounding_box의 정보를 얻어 RGB이미지와 depth이미지를 opencv 처리하기 위해 데이터 형식을 변환하고 RGB 이미지상의 좌표를 추출해 그 좌표에 해당하는 위치의 depth 이미지에서 거리를 추출한다.

- CamRgbImageCallback() : RGB 이미지를 불러와서 opencv 처리를 한 후 좌표를 추출해 처리된 depth 이미지에서 거리를 추출한다. 고라니가 인식될 경우, 멧돼지가 인식될 경우 나눠서 처리한다.
- CamDepthImageCallback() : depth 이미지를 불러와서 opencv 처리를 한다.
- DarknetBboxCallbackv : yolo에 인식된 Bounding_box의 정보를 부른다.

![image](https://user-images.githubusercontent.com/57993534/125826654-ffc63d1a-873c-4e6a-b2c1-879e6892343e.png)

![image](https://user-images.githubusercontent.com/57993534/125826665-1fc3422e-604d-4734-9c0a-47f588a73b9e.png)

- 물체가 인식이 되면 인식을 바탕으로 boundingbox 정보를 이용해 네모 박스와 위에 인식 대상 이름과 거리가 적혀진다.

![image](https://user-images.githubusercontent.com/57993534/125826678-9f742970-eeda-4e01-9f6e-7cae030e205e.png)

- 숫자는 ros의 파라미터, class는 인식 대상 이름, score는 인식률, Dist는 카메라와 인식 대상과의 거리이다.
