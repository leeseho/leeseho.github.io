---
layout: post
title: "AWS - Amazon Rekognition 사용법 정리.."
subtitle: "설치부터 Configuration 까지"
categories : [Cloud]
date: 2020-1-16 09:30:00 -0900
background: '/img/posts/06.jpg'
---

# 문서 목차
 - Amazon Rekognition ?
 - Amazon Rekognition 작동방식 (4p)
 - Amazon Rekognition 시작하기(10p)
 - 이미지 작업(23p)
 - 저장된 비디오 작업(49p)
 - 스트리밍 비디오 작업(77p)

# Amazon Rekognition ?
 Amazon Rekognition은 이미지와 비디오 분석을 위한 클라우드 서비스이다. API에 이미지나 비디오를 제공하면, 객체(사람, 장면, 활동 등)를 파악할 수 있다.
 이미지와 비디오로 검색하는 기능, 얼굴 기반 사용자 자격 증명, 감정 분석, 얼굴 검색(일치하는 얼굴이 있는 이미지나 비디오 검색), 부적절한 컨텐츠 감지, 유명인 인식, 텍스트 감지(인식 및 추출)와 같은 이용 사례가 있다.


## 사용시 이점
- 머신러닝 기능을 프로그램 내부에 포함시킬필요가 없다는 것이 장점.
- 알고리즘이나 구현방법을 몰라도 사용 가능.

# Amazon Rekognition 작동 방식
 이미지 분석에 사용하는 `Amazon Rekognition Image`, 비디오 분석에 사용하는 `Amazon Rekognition Video` 라는 2개의 API가 있다.
 ## 감지 및 인식 유형
- 레이블
- 얼굴
- 얼굴 검색
- 인물 경로
- 유명 인사
- 텍스트 감지
- 안전하지 않은 콘텐츠

 ## 이미지 및 비디오 작업
  ### Image 작업
    입력과 응답은 JSON 형식이며, `jpg` 또는 `png` 형식의 입력 이미지를 분석한다.

  ### Video 작업
    Amazon S3에 저장된 비디오 또는 Amazon Kinesis Video Streams를 통해 스트리밍된 비디오를 분석할 수 있다.

## AWS CLI 설치
[Installing AWS CLI version 1](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv1.html)


## Prerequisite
 - 파이썬 2.7 이상 또는 파이썬 3.4 이상 (AWS CLI 1.17 버전 기준)
 - Windows, Linux, macOS 지원

## 설치 방법
 설치는 아래 세 가지 방법 중 하나로 하면된다.
 - Bundled installer(MSI instller) 를 이용한 방법
 - pip를 이용한 방법
 - 가상 환경을 이용한 방법 (pip3 오류나는 경우..)


 나는 이 중에서 pip를 이용해서 설치해보았다. 프롬프트에서 아래 명령을 통해 설치가 가능하다.
 ```
pip3 install awscli --upgrade --user
 ```
 또는
 ```
 pip install awscli --upgrade --user
 ```
  ### 환경변수(PATH)에 추가
 MSI Installer를 이용한 경우, 자동으로 추가해주기 때문에 이 과정은 생략할 수 있다. 나는 pip를 이용하였으므로 따로 추가 해주었다.
 일반적으로  Windows10이고 Python 3.7버전인경우  `%USERPROFILE%\AppData\Roaming\Python\Python37\Scripts` 를 환경 변수에 추가해주면 된다.
 
만약 저 경로가 아닌경우, 명령프롬프트에서
 ```
 where /R c:\ aws
 ```
 를 입력해 경로를 찾을 수 있다.

 ### 설치확인
 `aws --version`을 입력하면 버전이 잘 출력된다.  
![버전확인](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-01-16-17-17-38.png?raw=true)  
 

## AWS Configuration
 AWS 서비스를 사용하기위해서는 내 계정의 Access Key와 region 등의 정보를 입력해주어야한다. 이는 `aws configure` 명령을 통해 설정이 가능하다.

 ```
$aws configure
AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
Default region name [None]: us-west-2
Default output format [None]: json
 ```



이 글은 [AWS Rekognition 개발자 안내서](https://docs.aws.amazon.com/ko_kr/rekognition/latest/dg/rekognition-dg.pdf)를 참고하여 보기 쉽게 정리 하였습니다.
