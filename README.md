# README

### 프로그램 소개, 목적

1. <포스텍 로봇카 르네상스를 이룩하자>(이하 포로리)는 자율주행 RC카를 만드는 프로젝트이다. 확장 가능한 형태의 RC카인 ‘동키카’에 소형 컴퓨터인 ‘라즈베리파이3B+’를 결합했고, 여기에 RPLiDAR와 2D카메라, USB 마이크를 연결해 hector-SLAM 매핑과 YOLO 오브젝트 식별, 음성인식 주행을 구현했다.
2. 간단하게 동키카의 작동방식을 설명하면, 음성인식으로 받은 명령을 모터를 움직이는 모듈에 전달해 ‘go(출발)’, ‘stop(정지)’, ‘right(우회전)’, ‘left(좌회전)’, ‘fast(빠르게)’, ‘slow(느리게)’ 등의 조종이 가능하게 만들었다. 주행도중 5초에 한 번씩 사진을 찍고, 사진 속에 나타난 오브젝트를 인식할 수 있는 기능도 있다. 그리고 주행한 공간의 2D 지도를 생성할 수 있다.

### 프로그램 기능 및 예시

1. RPLiDAR를 이용한 hector-SLAM 매핑 (gsr 524호)

    SLAM (Simultaneous localization and mapping) 은 이동하는 물체를 통하여 위치추적과 지도작성을 동시에 수행하는 것을 말한다. Hector-SLAM은 ROS를 통해서 실행시킬 수 있는 파일들의 패키지이다. 우리조는 lidar를 이용하여 hector slam을 실행시켰다.

    ![images/image2.jpg](images/image2.jpg)

    ![images/image3.jpg](images/image3.jpg)

2. 2D 카메라를 이용한 YOLO 오브젝트 식별

    동키카에 장착한 pi camera에서 받은 사진과 미리 학습시켜놓은 darknet의 yolov3_tiny_weight를 이용해서 object detection을 구현하였다.

    ![images/image4.png](images/image4.png)

3. 음성인식과 ros를 이용한 차량 조종

    음성인식을 통한 차량 조종을 구현에는 GOOGLE SPEECH API와 teleop-twist- keyboard이 중심이었다. 라즈베리파이에 USB 마이크를 연결하고, stt API와 음성인식 파일을 받아와 수정한다. 한편, teleop-twist-keyboard는 키보드 입력을 받아 rc카를 조종하는 방식이었는데 , 키 설정 단계에서 특정 단어가 나오면 단어에 맞는 키로 설정되도록 코드를 변경하였다. 각 단계마다 음성인식 파일을 종료하고 다시 파일을 실행하여 마이크 입력 시간을 연장하고 단어에 의한 명령 혼란을 줄였다.

    ![images/image5.png](images/image5.png)

4. 동키카의 조립된 모습

    ![images/image6.png](images/image6.png)

    ![images/image7.png](images/image7.png)