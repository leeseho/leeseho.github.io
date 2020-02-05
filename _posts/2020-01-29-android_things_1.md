---
layout: post
title: "Android Things 개발환경"
subtitle: ""
categories : [IoT]
date: 2020-1-29 14:00:00 -0900
background: '/img/posts/06.jpg'
---

# android things
`android things`는 안드로이드 개발툴과 임베디드 장치를 쉽게 개발할 수 있게해준다.
그리고 `Tensorflow Lite`를 이용해서, Android Things 기반의 앱에서 머신러닝을 쉽게 개발할 수 있다.

이번 예시에서는 [ImageNet](http://image-net.org/)을 이용해서 임베디드기기 로컬에서 분류를 수행하는 프로그램을 만든다.


## Requirement && Devices
- Raspberry Pi 3B (B+는 호환되지 않음)
- 8GB 이상의 micro SD 카드(컴퓨터와 연결할 리더기)
- Camera module
- Android SDK를 27.0.1 이상
- SDK with Andorid 8.1(API27) 이상
- [Raspberry Pi 3에 Android things 설치](https://developer.android.com/things/hardware/raspberrypi.html)


## Andorid Things 설치
### Android Things Setup Utility

[Android Things Setup Utility](https://partner.android.com/things/console/#/tools)를
다운받고 실행하여 설치를 진행한다.

### Flash android things

![Andorid things 설치 과정](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-01-29-15-21-29.png?raw=true)


![Andorid things 설치 과정-2](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-01-29-15-23-01.png?raw=true)

### 라즈베리파이 부팅
  sd카드를 라즈베리파이에 꼽은다음, 전원과 인터넷, HDMI를 연결한다. 라즈베리파이와 개발PC와 연결하기 위해 같은 공유기에 연결한다.
 부팅하면, 네트워크 부분에 IP주소가 나온다. 이를 이용해 adb에 연결한다.

### adb 연결
    먼저 adb가 환경변수에 추가되어있어야한다(여기서는 별도로 설명하지 않음). 그 후 명령 프롬프트에서 `adb connect IP주소`를 입력하여 라즈베리파이와 연결한다.  연결 후 `adb devices`를 입력하면, 연결된 라즈베리파이가 리스트에 출력되는 것을 확인할 수 있다.

### Build
 이제 안드로이드 스튜디오를 켜면, 기기가 연결된 것을 확인할 수 있다.

![connect_result](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-02-04-10-00-18.png?raw=true)
