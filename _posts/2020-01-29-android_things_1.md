---
layout: post
title: "android things example"
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
- Raspberry Pi 3
- 8GB 이상의 micro SD 카드(컴퓨터와 연결할 리더기)
- Camera module
- Android SDK를 27.0.1 이상
- SDK with Andorid 8.1(API27) 이상
- [Raspberry Pi 3에 Android things 설치](https://developer.android.com/things/hardware/raspberrypi.html)


## Andorid things 설치
### Flash android things


![Andorid things 설치 과정](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-01-29-15-21-29.png?raw=true)


![Andorid things 설치 과정-2](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-01-29-15-23-01.png?raw=true)


## MQTT를 이용한 통신하기





[구글 코드랩 참고](https://codelabs.developers.google.com/codelabs/androidthings-classifier/index.html?index=..%2F..index#0)