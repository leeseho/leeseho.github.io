---
layout: post
title: "노트북 발열 해결 - 방열 작업.."
subtitle: "서멀패드+서멀컴파운드"
date: 2020-03-07 10:00:00 -0900
background: '/img/posts/05.jpg'
---




 노트북을 처음 살때부터, 쿨링팬 소리가 너무 심했어서 언더볼팅이나, 클럭 제한, 서비스 정리 등 여러 방법을 써보았지만 한계가 있었다. 그래서 같은 기종을 방열 작업했던 글을 참고하여 방열 작업을 해보았다.  

 찾아보니 내 노트북은 다른 노트북들에 비하면 나름 온도가 괜찮은 편인것같다. 그러나 CPU 부하가 높은 작업에서는 쓰로틀링이 너무 쉽게 걸리는 것이 불편해서, 한번 시도해보기로 했다.  

  ## 방열작업 전
![방열작업전 온도](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-03-07-10-16-59.png?raw=true)  

![Stress test](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-03-07-11-16-45.png?raw=true)  
 스트레스 테스트 몇 초만 90도를 넘는다..  

 
 ## 방열작업 후
  ![방열작업 직후](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-03-07-16-35-24.png?raw=true)  
  부팅직후 최저 온도가 28도까지 내려간다..! (방열작업전 부팅직후 40~50도)  


![방열 후 고부하 작업](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-03-07-16-43-44.png?raw=true)
    
![XTU Stress test](https://github.com/leeseho/leeseho.github.io/blob/master/_posts/images/2020-03-07-16-50-03.png?raw=true)  
 2.8GHz 100% 로드시에도 최고온도는 80밖에 되지 않는다. 
 테스트 결과 3.1GHz에서도 80도 전후를 유지한다.



 ## 후기
 결과는 매우 성공적이다. 한편으로는, 삼성에서 알루미늄 바디를 가지고 있는 제품임에도 방열을 이렇게까지 하지않은 이유도 알것같다.  
CPU 온도가 떨어지는대신 후면 판이 엄청 뜨거워진다. 풀로드시에는 거의 손이 데일 것 같이 뜨거워진다. 특히, 노트북 펜S 제품은 360도 뒤집어 필기가 가능한 제품인데,  
그 때 화면 패널이 그 온도에 닿는다면 패널에 번인현상이 생기거나 고장이 날 것이다. 그렇기에 뒤집어 사용할 시에는 반드시 배터리절약모드를 해야할 것 같다.