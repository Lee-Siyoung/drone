## WIFI와 LTE 비교
### WiFi 통신
WiFi의 거리는 사용하는 전파에 따라 크게 다르다.

WiFi에 사용되는 주요 전파의 종류는 2.4GHz와 5GHz로 각각 전파의 특성이 있기 때문이다.

2.4GHz는 멀리까지 전파가 도달하여 장애물이 있어도 연결이 쉬운 특성이 있다.

5GHz의 전파는 새로운 규격으로 통신 속도가 빠르고, 간섭하는 장비도 적기 때문에 안정적인 통신이 가능하다.

2.4GHz 와이파이는 최대 300Mbps의 속도를 내지만 5GHz 와이파이는 최대 867Mbps의 접속 모드를 지원한다. -> 농작지가 대상임으로 5GHz가 적절하다.

예를 들어, 건물 내에서 2.4GHz와 5GHz 각각의 WiFi에 접속한 경우 2.4GHz 쪽이 5GHz보다 먼 곳에서도 접속할 수 있다.

와이파이 거리를 늘리는 기술 : BeamForming

라우터가 자동으로 PC나 스마트폰 등의 단말기의 위치를 파악하고 그 자리에 집중적으로 전파를 송신하는 기술입니다. -> 농작지에 설치할 수도 있지만 그럴꺼면 lte 통신이 더 효율적임.

WiFi의 유효 통신거리는 일반적으로 라우터에서 직선거리로 50m~100m 정도가 기준이다. -> 철근 콘크리트제의 주택은 전파를 차단하기 쉽고, 목조 주택보다 WiFi 유효 통신거리는 짧아질 것입니다. 하지만 위 드론은 농작지를 대상이기 때문에 전파를 차단할 물체는 존재하지 않는다. 

### LTE 통신
휴대전화 네트워크의 용량과 속도를 증가시키기 위해 고안된 4세대 무선 기술(4G)을 향한 한 단계이다. 

LTE 표준은 100Mbps의 하향링크 최고 속도, 50Mbps의 상향링크 최고 속도이다.

통신거리는 동글, 라우터마다 차이가 있지만, 기본 전송 거리가 300m이다.
(https://www.hindawi.com/journals/jat/2017/2750452/)


화웨이 LTE USB 동글

![image](https://user-images.githubusercontent.com/57993534/125949540-c696ed70-2e7d-42f5-8667-5b7983e922d9.png)

지원 주파수

LTE FDD(Frequency Division Duplexing) : Band 1 (2.1 GHz )/ Band 3 (1.8GHz) / Band 5 (850mhz) / Band 8 (900mhz)

=> KT 권장 모델이기 때문에 Band3를 사용하여 최대 1.8GHz 주파수를 사용할 수 있음.

LTE TDD(Time Division Duplexing) : Band 38 (2600 MHz) / Band 40 (2300 MHz)

![image](https://user-images.githubusercontent.com/57993534/125949601-02b20984-6ba9-42aa-a1e4-a697fea0d479.png)

KT 기준 (10MHz = 75Mps)

uplink 주파수 : 25MHz => 187.5Mps 

downlink 주파수 : 30MHz => 225Mps

Jetson Xavier - Intel Dual Band Wireless-AC 8265

최대속도 : 867mps

국민 1인당 경지 면적은 0.04ha, 세계 평균은 0.24ha, 중국 0.10ha. 미국 0.66ha
(1ha = 10,000 m² 즉 우리나라 1인당 평균 경지 면적은 400 m² => 20m  20m 가로질러도 28.28m)

![image](https://user-images.githubusercontent.com/57993534/125949629-36157c2d-693b-44fb-be3e-188ce67f86e8.png)

