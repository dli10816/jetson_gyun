# jetson_gyun

Getting Started with AI on Jetson Nano

 1. Jetson Nano Setting 준비물
  
        - jetson nano 4gb
  
        - c type power adapter
  
        - 와이파이 동글
  
        - 웹캠(USB Camera), 또는 CSI Camera (라즈베리파이 V2)
  
        - 64기가 이상 마이크로sd카드
  
        - 그외 쿨링펜, lcd, 또는 모니터. hdmi

![jetson-nano-dev-kit-top-r6-HR-B01 (1)](https://github.com/user-attachments/assets/b845a744-9be0-47f7-abd0-e81373960e19)
2. jetson nano에 대하여


환영부터 따라하기 https://learn.nvidia.com/courses/course?course_id=course-v1:DLI+S-RX-02+V2&unit=block-v1:DLI+S-RX-02+V2+type@vertical+block@aba5104413ae454c8c63a6f301925337

3. jetpack downloads

https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write


4. 이미지 굽기 위해 필요한 것들.

```
   4-1. sd card formatter ---> download
   4-2. balenaetcher download --->  이미지 굽기
   4-3. 제슨나노에 sd넣고 우분투 설치
```

5. 쿨링팬 설치 (0~255) 와 쿨링팬과 jtop (jtop : system monitoring tool) terminal을 열어줍니다.
```
sudo sh -c 'echo 128 > /sys/devices/pwm-fan/target_pwm'
```


6. USB-Camera 얼굴의 코 눈 인식하는 것도 해봄, 이미지 캡쳐와 영상 녹화 CCTV기능 구현 J는 이미지 캡쳐, 1은 영상 녹화 시작 0은 영상녹화 스톱 mode=1은 사진, mode=2는 영상

```
git clone https://github.com/jetsonhacks/USB-Camera.git
cd USB-Camera
ls
python3 usb-camera-gst.py 
python3  face-detect-usb.py
nvgstcapture-1.0 --mode=1 --camsrc=0 --cap-dev-node=0
j
nvgstcapture-1.0 --mode=2 --camsrc=0 --cap-dev-node=0
1
0
```

 
![unnamed](https://github.com/user-attachments/assets/4b1fa393-0493-4cd5-bf85-207d815e9583)

이곳에 사진 넣고 영상 넣을 것 참고 링크 https://ndb796.tistory.com/557
7. 한글 설치 , reboot 한 후 오른쪽 하단 키보드 모양을 오른쪽 마우스 클릭→ configure click

```
참고 링크 https://driz2le.tistory.com/253
```

```
sudo apt-get update
sudo apt-get install fcitx-hangul
reboot
```

8. 제슨 알아보고 설치하기

https://developer.nvidia.com/embedded/learn/jetson-nano-2gb-devkit-user-guide#id-.JetsonNano2GBDeveloperKitUserGuidevbatuu_v1.0-DeveloperKitSetup

결과

![372466618-634eaeeb-1a8f-4bff-a953-55663eef1c7e](https://github.com/user-attachments/assets/2213f17f-03df-45db-a639-431923b4b82f) 

카메라 없어서 생기는 에러로 카메라 연결하고 다시 명령한다 dli@dli-desktop:~$ sudo docker run --runtime nvidia -it --rm --network host

```
--memory=500M --memory-swap=4G \
--volume ~/nvdli-data:/nvdli-nano/data \
--volume /tmp/argus_socket:/tmp/argus_socket \
--device /dev/video0 \
nvcr.io/nvidia/dli/dli-nano-ai:v2.0.2-r32.7.1kr
```





8. 제슨 알아보고 설치하기
9. <b> 
jetson nano image
![image](https://github.com/user-attachments/assets/b04114c0-01c8-45b7-9c23-9e8d58494e8f)
 <b> 
jetson nano image
![image](https://github.com/user-attachments/assets/7d33b4f0-9264-4370-9ac5-6f281b9ff99f)
<b> 
jetson nano image
![image](https://github.com/user-attachments/assets/24bb74eb-eb81-41e8-9b61-7873a476d083)

https://developer.nvidia.com/embedded/learn/jetson-nano-2gb-devkit-user-guide#id-.JetsonNano2GBDeveloperKitUserGuidevbatuu_v1.0-DeveloperKitSetup

10. image classification - Thumbs Project using ResNet

https://learn.nvidia.com/courses/course?course_id=course-v1:DLI+S-RX-02+V2&unit=block-v1:DLI+S-RX-02+V2+type@vertical+block@aabe204272214ba69309581d388b0734

11. image regression - Face XY Project

https://learn.nvidia.com/courses/course?course_id=course-v1:DLI+S-RX-02+V2&unit=block-v1:DLI+S-RX-02+V2+type@vertical+block@76a2873eb69946b4928c4f8432e04314
