## CSI
CSI(Camera Serial Interface)는 카메라 모듈을 애플리케이션 프로세서에 연결하기 위한 프로토콜이다.
Ros에 jebot camera driver가 존재하기 때문에 따로 픽셀값을 일일이 받아오지 않고 노드가 통신으로 이미지 데이터를 가져온다. 

C-PHY는 최대 3개의 데이터 레인만이 있으며 D-PHY와 다르게 1개 레인당 3개의 핀(라인)이 사용된다. 클럭은 별도의 레인이 없고 전송되는 데이터에 임베디드시키게 된다. 따라서, 데이터를 받는 쪽에서 임베디드된 클럭을 찾아 내는 모듈(CDR, Clock Data Recovery)가 사용된다.

클럭은 별도의 레인이 없고 전송되는 데이터에 임베디드시키게 된다. 따라서, 데이터를 받는 쪽에서 임베디드된 클럭을 찾아 내는 모듈(CDR, Clock Data Recovery)가 사용된다.

C-PHY에서 하나의 레인은 3개의 라인으로 구성이 되고, 각각의 라인은 High, Middle, Low의 신호를 전송한다. 따라서, 하나의 레인으로 총 27 종류의 신호를 보낼 수 있다. 이 중에서 차분 신호로의 특성을 살릴 수 있는 6가지만 경우만 선별하여 사용한다.
C-PHY에서는 데이터 전송 속도의 단위를 Gsym/s로 표현한다. 즉, 초당 심볼수로 전송 속도를 나타내며, 심볼당 데이터의 수는 2.28비트이다. C-PHY의 레인당 최대 속도는 2.5 Gsym/s이므로, 이를 비트로 환산을 하면 2.5 x 2.28 = 5.7 Gbps가 된다. 결국, 3개의 레인을 사용할 경우 17.1 Gbps의 최대 데이터 전송 속도가 나오며, 4개의 레인을 사용하는 D-PHY의 경우 2.5 Gbps x 4 = 10 Gbps 보다 훨씬 빠른 데이터 전송이 가능하다.

### C-PHY 데이터 변환 순서

![image](https://user-images.githubusercontent.com/57993534/125947741-6337ec48-5dda-45bb-a032-a1833597c4c5.png)

1. Wire differential
- 각 wire의 상태와 다른 wire 상태를 비교한 differential 신호 값이다.
- 비교 조건은 A>B, B>C, C>A 3가지이다.

2. Wire States (3bit)
- Wire differential 값을 3bit로 표현한 값이다.
-  A > B가 상위 bit, B > C가 중간 bit, C > A가 하위 bit 값이다.

![image](https://user-images.githubusercontent.com/57993534/125947757-578625ce-d712-4eec-ad51-ffecf1c3a4ec.png)

3. Symbols (3bit)
- Symbol은 현재 Wire state에서 다음 Wire state로 변하는 값으로 추출하는 데이터이다.
- Wire state는 총 6가지 state가 있으며 연속된 state가 올 수 없으므로 자기 자신을 제외한 5가지 state로 값이 변하게 되며 이때 wire state name이 바귀는 조건에 따라 symbol값이 정해진다.
- 
![image](https://user-images.githubusercontent.com/57993534/125947789-f9160108-4ab3-4bbd-ad1c-65aba73c9600.png)

4. Integers (16bit)
- 7자리의 symbol 값은 16bit integer 값으로 mapping 된다.
- symbol 값은 0~4의 값으로 7자리 이므로 최대 78125가지의 값이 있을 수 있다. 이중 65536 값은 16bit integer 값과 1대1 mapping 값으로 사용되며 나머지 12589 값은 marker 값 등으로 사용된다.

![image](https://user-images.githubusercontent.com/57993534/125947811-1c9f1d96-8217-4ac5-97a5-13781f039cd0.png)

참고 자료 - https://m.blog.naver.com/laonple/220876151247


## GStreamer
### GStreamer란?
- 스트리밍 미디어 응용 프로그램 만들기 위한 프레임 워크, 모든 유형의 스트리밍 멀티미디어 응용 프로그램 작성할 수 있다.
- 구성요소를 임의의 파이프라인에 혼합해 응용 프로그램 작성할 수 있는 장점이 있다.

![image](https://user-images.githubusercontent.com/57993534/125947850-f75adb2a-49ea-477b-a6a7-4ffc94627d55.png)

- gstremer는 elements를 담은 최상위 bin으로 응용프로그램을 위한 버스를 제공한다.
- file-source는 디스크, 사운드 카드에서 읽어 파이프라인에 사용할 데이터 생성, 출력 pad만이 존재
- demuxer, muxers and coder는 입출력 pad가 존재하고 데이터를 받고 처리 후 전송한다. 데이터는 filter(볼륨), convertor(비디오 크기변환), ogg(비디오 + 음성 포함 파일) demuxer 등이 있다.
- sink는 미디어 파이프라인의 끝 점이며 입력만 받는다.


### Gstreamer communication

 ![image](https://user-images.githubusercontent.com/57993534/125947916-3c4ee7b0-a4f1-4055-96b3-bfd65a937d84.png)

- buffer를 통해서 파이프라인 element 간 데이터 전달을 위한 객체이다.
- event는 element 또는 application에서 element로 전송되는 객체
- message는 파이프라인의 메시지 버스에 element별로 게시된 개체, application에서 수집을 위해 유지됨. 주로 error나 tag, 상태변화, buffer 상태의 정보를 전달할 때 사용된다.
- query는 application에서 query를 통해 파이프라인에서 지속시간, 현재 재생 위치같은 정보 요청 가능

jetson nano gstreamer 설치 가이드 - https://docs.nvidia.com/jetson/l4t/index.html#page/Tegra%20Linux%20Driver%20Package%20Development%20Guide/accelerated_gstreamer.html

참고용 : 프레임 올려주는 영상 - https://www.youtube.com/watch?v=GQ3drRllX3I
