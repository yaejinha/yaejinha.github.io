---
layout: post
title: IoC 와 DI
date:  2019-08-15 21:36:00 +0800
img: cliff.jpg # Add image post (optional)
categories: [spring-framework]
tags: [공부] # add tag
---

사진으로 절벽에 매달린 나의 심정을 나타내봤다 ㅠㅠ...  
스프링 프레임워크를 공부하기로 마음 먹자마자 위기에 빠졌다.  

**도대체 IoC 랑 DI 가 뭔데?**

# Inversion of Control 
[블로그 변역글]() 에서 길게 얘기 했지만 무림식으로 요약해보겠다.  
 너무나도 방대해지고 무거워지는 Java EE 어플리케이션 을 탈피하고자 태초에 무림에는 여러 프레임워크들이 자웅을 겨루고 있었다.  
 그들에게 가장 기본적이고 중요한 해결과제가 있었으니... 바로 의존성을 어떻게 주입할 것인가 !  
 여기서 나온 방법이 Inversion of Control (프레임워크가 정한 일정 규칙만 따르면 알아서 넣어줄게) 이고 이 IoC 의 작은 범위가 DI 라는 것이다. 