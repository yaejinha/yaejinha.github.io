---
layout: post
title: 실습 with spring boot  Netflix OSS 3- Eureka 
date:  2020-03-01 20:23
img: gorapaduck.png # Add image post (optional)
categories: [기타]
tags: [IT, Spring cloud, NetflixOSS, Eureka, Hystrix] # add tag
sitemap :
changefreq : daily
priority : 1.0
---

이번 실습은 Eureka 설정이다.   
Eureka를 간단히 말하자면 연결된 서버들의 생사 체크도 해서 레지스트리로 관리하고  서버가 죽었으면 서비스에서 제외하는 load balancing 역할을 하는 거다.   
여기서 각 클라이언트들은 또 서버가 되서 다른 연결된 서버들을 클라이언트 삼을수도 있다. [링크](https://www.baeldung.com/spring-cloud-netflix-eureka)  

나는 여기서 유레카 서버 하나 만들고 클라이언트 역할 하나만들어서 등록이랑 해제만 해보겠다. 

## Eureka Server 

1) 일단 클라이언트들 생사체크를 하고 분산 처리를 할  서버 역할을 할 spring boot project 만든다.  여기에는 eureka-server 디펜던시를 넣어준다.  
```xml
<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
</dependency>
``` 

2) 서버 설정을 넣어준다.  
```properties
eureka.client.registerWithEureka = false   // 스스로도 클라이언트처럼 등록하여 사용할 수도 있는데, 여기서는 서버로 사용할 거니까 false 로 자기자신은 등록 안하도록 한다. 
eureka.client.fetchRegistry = false  // 클라이언트들이 레지스트리를 캐시로 사용할 수있도록 할지 선택
server.port = 8761  //유레카 서버 기본 포트 

```

3)@EnableEurekaServer  어노테이션으로 Eureka server 작동시킨다.  


## Eureka Client 

클라이언트는 유레카 서버에 서비스 등록하고 싶은 어플리케이션을 말한다.  

1.  eureka client 디펜던시 넣기.  
```xml
 <dependency>
     <groupId>org.springframework.cloud</groupId>
     <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
 </dependency>
 ```

 2. 설정 넣기. 

```properties
 eureka.client.serviceUrl.defaultZone  = http://localhost:8761/eureka  // 체크될 유레카 서버 서비스 url 넣는다. 여러개 일수 있음
 spring.application.name = eurekaclient  // 유레카 서버에 등록될 이름 
```

3. @EnableDiscoveryClient 어노테이션으로 등록 


여기까지 해서 두개 다 띄워보면 유레카 모니터링 화면에서 확인할 수 있다.  

![유레카 모니터링](/assets/img/eureka.png)  

그럼 등록까진 확인이 되는거다.  
그냥 포트를 죽여서 서비스 해제 까지 보려고 했는데 해제가 잘 안된다.  
이건 내일 해봐야지. 좀 더 공식 문서도 보고 설정값도 좀 봐야겠다. 




