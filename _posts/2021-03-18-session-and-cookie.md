---
layout: post
title: 세션과 쿠키 이야기,, 즐거운 웹 생활
date:  2021-03-18 19:00
img: cookiemonster.jpeg # Add image post (optional)
categories: [python]
tags: [IT,  web, web programming, cookie, session] # add tag
sitemap :
changefreq : daily
priority : 1.0
---

세션과 쿠키는 대충 들어본 적은 있지만 정확히 정리하고 넘어간 적 없다.   

요즘 팀 보안담당 업무를 하면서 모의해킹 연습을 하는데  쿠키, 세션이 조금 헷갈렸다.  
마침 듣고 있는 인강에도 나와서 간단하게 정리하고 가야지.  

## 1. 쿠키 
사용자 컴퓨터에 저장하며, 주로 사용자가 어떤 리퀘 보내는지 트랙킹하는 용도로 많이 사용된다.  
그래서 우리가 어떤 사이트 처음가면 쿠키 수집을 허용하시겠습니까 ? 이런 메시지 뜨는 것   
우리가 가지고 있는 웹서핑한 기록인 쿠키를 수집하면 우리에 대한 정보를 넘겨주는 꼴!!   

## 2. 세션 
시스템 서버 메모리에 저장하거나 redis 같이 단발성 저장하는 것.  
임의의 세션 아이디로  사용자를 구분하는  키로 씀.  
이걸로 개개인 사용자를 구분할 수 있기에  보안적인 측면에서 사용한다.   
로그안하고 다른 페이지 넘어가도 그 사람인지 인증하기 위해선 세션 체크가 필요 !  
모의해킹 해볼때는  이 세션 값 탈취해서 다른 창 띄워서 사용 가능한지 해봤다.   
세션 아이디를 만들고 부여하는건  사용자를 구분할 수 있도록  암호화-복호화도 하고 어쩌구 저쩌구 복잡한데 flask 에서는  라이브러리가 있어 사용할 수 있다고 한다.  
아마 다른 언어나 프레임워크도 마찬가지로 라이브러리 있겠지? 하나하나 다 어케해요...   

어쨌든 역시 실전으로  고민해봐야 머리에 잘 남는다 ^^...   

나같은 무근본은 기초 지식도 헷갈리는데 경험이 사람을 만든다 하ㅎ ㅏ 
