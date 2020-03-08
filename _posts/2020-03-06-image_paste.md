---
layout: post
title: "Visual Studio Code 마크다운 이미지 확장 프로그램"
subtitle: ""
categories : etc
date: 2020-03-06 11:00:00 +0900
background: '/img/posts/05.jpg'
---

 마크다운 문서에서 이미지를 추가하기 위해서는  
 `![표시이름](이미지경로 또는 주소)` 과 같은 형식으로 입력해야한다.  

 그런데 이미지를 해당 위치에 저장하고, 그 경로를 일일이 입력하기는 쉽지않다.  

# Paste Image
 Visual Studio Code(VSCode)에서는 `Paste Image`라는 확장프로그램을 사용하면 단순 `캡쳐+붙여넣기`만으로 이미지 저장과 `![표시이름](파일경로 또는 주소)` 형식의 코드입력을 한번에 할 수 있다.

# 사용법
하나의 폴더 내 문서와 이미지를 저장하는 경우에는, 간단히 이미지 경로를 복사하고, 코드 내에서 `Ctrl+Alt+V`만 누르면 입력된다.  


## For Github Page
그런데 github 블로그를 이용할때는 엑박이나 이미지가 뜨지않는 현상이 있어서 몇가지 설정을 해주어야한다.

 VSCode에서 Paste Image Extension의 톱니바퀴모양을 클릭하면 설정창이 나온다.


기본 붙여넣기 형식은 `![](이미지 이름)`이지만,  
github blog에서 사용하기위해  
` ![이름]](레포지토리 주소/blob/master/이미지경로/이미지이름?raw=true)`  
과 같은 형식으로 입력되도록 설정해주어야 한다. 

여기서 `이미지이름`은 기본값으로 입력되므로 신경쓰지 않아도 된다.  참고로 이미지 파일이름의 디폴트 형식은 `Y-MM-DD-HH-mm-ss` 이다.


결국 기존의 형식에서
 - 앞부분(Prefix) : `레포지토리 주소/blob/master/파일경로/`  
 - 뒷부분(Suffix) : `?raw=true`  
 가 추가하면 된다.
 



## 설정 방법
 나는 내 깃허브 블로그 레포지토리(`https://github.com/leeseho/leeseho.github.io`)의 `_posts/images`경로에 문서에 사용되는 이미지파일이 저장되어있다.  
![Path](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-03-06-11-41-25.png?raw=true)  
 그러므로 경로를 위와같이 설정했다. 참고로 `${currentFileDir}`은 `현재 문서 파일(.md)의 경로`이다. 이 경로는 이미지 파일이 저장되는 경로이기도 하다.


![Prefix](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-03-07-23-10-36.png?raw=true)
 그리고 이미지 파일이름 앞에 붙어야할 `레포지토리주소 + /blob/master/ + 경로` 형식을 넣어주었다.


![Suffix](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-03-06-11-41-56.png?raw=true)  
마지막으로 파일 뒤에 `?raw=true`를 입력해 준다.


## 그 외
  원하면 파일이름과 저장 위치, prefix, suffix 등을 수정할 수 있고, Insert Pattern도 수정할 수 있다.  