# face_detect_cam

    0 <------ pan left(pan++) ------- > 300   320 <------ pan right(pan--) ------------> 640
  0 +------------------------------------+-----+-----+------------------------------------+
    |                                    |     |     |                ^                   |
    |                                    |     |     |                |                   |
    |                                    |     |     |          tilt up(tilt--)           |    
    |                                    |     |     |                |                   |    
    |                                    |     |     |                v                   |    
220 +------------------------------------+-----+-----+------------------------------------+    
    |                                    |     |     |                                    |  
    |                                    |     |     |                                    |    
240 +------------------------------------+-----+-----+------------------------------------+   
    |                                    |     |     |                                    |    
    |                                    |     |     |                                    |     
260 +------------------------------------+-----+-----+------------------------------------+    
    |                                    |     |     |                ^                   |   
    |                                    |     |     |                |                   |    
    |                                    |     |     |                                    |   
    |                                    |     |     |          tilt down(tilt++)         |   
    |                                    |     |     |                |                   |    
    |                                    |     |     |                v                   |     
480 +------------------------------------+-----+-----+------------------------------------+    



mini project <얼굴 위치 추적 카메라><br/>

물체가 화면 중심에 위치할 때까지 pan과 tilt를 조절합니다.<br/>

pan과 tilt의 조절은 서보 모터를 특정 각도로 이동시키는 것으로 이해됩니다.<br/>

pan과 tilt의 이동 방향과 정지 조건은 물체의 중심 위치에 따라 결정됩니다.<br/>


-라이브러리 및 포트 설정
cv2: OpenCV 라이브러리를 사용하여 영상 처리를 위한 함수들을 사용합니다.
serial: 시리얼 통신을 위한 라이브러리입니다.
시리얼 포트 COM4를 연결하고, 속도를 9600으로 설정합니다.

-변수 설정
margin_x와 margin_y: 중앙을 기준으로 움직일 수 있는 범위의 마진 값입니다.
cam_center_x와 cam_center_y: 카메라의 중심 좌표입니다.
pos_x와 pos_y: 서보 모터의 현재 위치를 저장하는 변수입니다.

-웹캠 설정
webcam 객체를 초기화하고, 영상을 캡처합니다.
물체 감지를 위해 HSV 색상 공간으로 변환하고, 마스킹하여 특정 색상의 물체를 추출합니다.

-물체 감지 및 제어
물체가 감지되면 해당 물체의 중심을 찾고, 이를 이용하여 팬과 틸트를 조절합니다.
중심 좌표를 이용하여 물체의 위치를 계산하고, 해당 위치에 따라 팬과 틸트를 움직입니다.
물체가 화면의 특정 영역에 위치할 경우, 움직임을 멈추도록 설정되어 있습니다.
서보 모터의 위치를 변경하기 위해 시리얼 통신을 사용하여 아두이노에 데이터를 전송합니다.

-화면 출력
cv2.imshow()를 사용하여 영상을 출력하고, cv2.waitKey()를 통해 입력을 대기합니다.
ESC 키를 누르면 영상 캡처를 종료하고 창을 닫습니다.


