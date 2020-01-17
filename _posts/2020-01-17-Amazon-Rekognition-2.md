---
layout: post
title: "AWS - Amazon Rekognition 사용법"
subtitle: "Detect Label 예제"
categories : [Cloud]
date: 2020-1-17 11:00:00 -0900
background: '/img/posts/06.jpg'
---


AWS S3 데이터베이스에 있는 데이터를 사용할 수 있으나, 로컬에 있는 파일을 사용할 일도 많을 것이다. 참고로 CLI에서 바로 바이트 이미지를 전달하는 기능은 지원되지 않는다. 일반적으로 CLI에서 바로 사용하지 않고, SDK를 이용해 사용한다.

# SDK 설치
 나는 파이썬을 사용하였으므로 pip를 이용해 설치하였다.
 ```
pip install boto3 
 ```

# 코드 분석
``` python 
import boto3 # AWS SDK import
import cv2   # 이미지 처리를 위한 openCV
```
AWS SDK와 openCV를 import 한다.

``` python
def detect_labels_local_file(photo):
    
    client=boto3.client('rekognition')
    
    with open(photo, 'rb') as image:
        response = client.detect_labels(Image={'Bytes': image.read()})
        
    #print('Check response type/shape: ', response, '\n') # response가 어떤 형식으로 들어오는지 check
        
        
        
        
    print('Detected labels in ' + photo)
    for label in response['Labels']: 
        print (label['Name'] + ' : ' + str(label['Confidence'])) # label은 List의 각 원소이고, 딕셔너리형임.
        
        
    return len(response['Labels']), response
```
이미지 파일을 열어
이미지를 Rekognition에 전달(`client.detect_label`)하여 response를 받는다. 로컬에 있는 사진을 전달하므로 Image 옵션으로 `{'Bytes': image.read()}`를 전달한다. 파일의 `read함수를 통해 파일 전체를 문자열로 전달`하는 것이다.


response는 딕셔너리형태로 반환된다. 

``` python
label_count, res_street = detect_labels_local_file("street.jpg") # 
#print("Labels detected : " + str(label_count))

img = cv2.imread("street.jpg") # 이미지 파일 read

img_width = img.shape[1] # 가로 해상도 
img_height = img.shape[0] # 세로 해상도

cv2.imshow("before",img) # 이미지 출력
cv2.waitKey(0)
cv2.destroyAllWindows()
```
 이제 res_street에는 레이블, 레이블별 인스턴스, (위치) 등의 정보가 있다. 이를 이용해서 원본이미지에 위치를 표시할 수 있다.

# 결과 화면
![before](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-01-17-16-20-27.png?raw=true)

 원본 이미지  

----


![result](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-01-17-16-23-44.png?raw=true)

 결과 이미지  
 버스는 빨간색으로, 사람은 파란색으로 표시해보았다.





# 전체 코드
``` python
import boto3
import cv2

def detect_labels_local_file(photo):
    
    client=boto3.client('rekognition')
    
    with open(photo, 'rb') as image:
        response = client.detect_labels(Image={'Bytes': image.read()})
      
        
        
    print('Detected labels in ' + photo)
    for label in response['Labels']: 
        print (label['Name'] + ' : ' + str(label['Confidence']))
        
        
    return len(response['Labels']), response 


label_count, res_street = detect_labels_local_file("street.jpg") 

img = cv2.imread("street.jpg")

img_width = img.shape[1]
img_height = img.shape[0]

print(type(img))
print(img.shape[1], img.shape[0])


cv2.imshow("before",img)
cv2.waitKey(0)
cv2.destroyAllWindows()

for label in res_street['Labels']: # Label
    if (label['Name'] == 'Bus') : # Bus로 Label된 경우
        for instance in label['Instances'] : # Objects 
            left = int(img_width * instance['BoundingBox']['Left'])
            top = int(img_height * instance['BoundingBox']['Top'])
            width = int(img_width * instance['BoundingBox']['Width'])
            height = int(img_height * instance['BoundingBox']['Height'])
            
            print(left, top, width, height) 
            
        
            cv2.rectangle(img, (left, top), (left + width, top + height), (0,0,255))
            cv2.imshow("bus ", img)
            cv2.waitKey(0)
            cv2.destroyAllWindows()
            
    if (label['Name'] == 'Person') : 
        for instance in label['Instances'] : 
            left = int(img_width * instance['BoundingBox']['Left'])
            top = int(img_height * instance['BoundingBox']['Top'])
            width = int(img_width * instance['BoundingBox']['Width'])
            height = int(img_height * instance['BoundingBox']['Height'])
            
            print(left, top, width, height) 
            
            
            cv2.rectangle(img, (left, top), (left + width, top + height), (255,0,0))
            cv2.imshow("person ", img)
            cv2.waitKey(0)
            cv2.destroyAllWindows()
            
            
```





이 글은 [AWS Rekognition 개발자 안내서](https://docs.aws.amazon.com/ko_kr/rekognition/latest/dg/rekognition-dg.pdf)를 참고하여 보기 쉽게 정리 하였습니다.
