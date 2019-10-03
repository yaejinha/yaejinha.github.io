---
layout: post
title: Javascript this 바인딩 1 [객체 내부 메서드 호출과 함수 호출]
date:  2019-08-10 12:36:00 +0800
img: javascript.jpg # Add image post (optional)
categories: [study]
tags: [공부] # add tag
sitemap :
changefreq : daily
priority : 1.0
---

 함수 호출 방식에 따라서  this 인자는 다른 객체를 참조한다. 

JS 로 Exercism 문제를 풀고 있는데 이 개념을 정확히 안 잡고 가니까 자꾸 엉뚱한데에서 헤맸다. 이것도 정리해봐야겠다. ( 인사이드 자바스크립트 책 참고) 

1. 객체의 메서드 호출시 
객체 내부의 메서드 프로퍼티를 호출할때  this 는  해당 메서드를 호출한 객체로 바인딩된다. 

        var myObject ={
           name: 'foo',
           sayName: function(){
             console.log (this.name);
             }
        };
        
        var otherObject={
           name : 'bar'
        };
        
       otherObject.sayName = myObject.sayName;
         
       myObject.sayName();
       otherObject.sayName();
       =======================================
       foo
       bar
     두 번의 sayName 메서드가  호출한 객체의 name 으로 바인딩 된 것을 확인할 수 있다. 

2. 함수 호출시의  this 
함수 호출시에는 this 가  전역 객체에  바인딩 된다.  브라우저 실행시에는 window 객체 바인딩 된다.  변수명을 정의할 때 잘 정의해야하는 이유가 되기도 한다. (window 객체 이름이랑 중복되면 바인딩 시 에러의 원인이 되니까) 

여기까지는 이해가 쉬웠는데 내부함수를 호출할 경우 부터 개념이 헷갈리기 시작했다. 
내부 함수에 this 를 사용한다면, 내부 함수 호출도 함수 호출 패턴으로 인식되기에 전역 객체에 바인딩 된다.   

**부모 함수의 객체에 바인딩하기 위해서는  내부 함수가 접근 가능한 다른 변수에 저장하는  패턴이 사용**된다!!!! 

    var value = 100;
    
    var myObject={
    	value=1,
    	func1: function(){
	    		var that=this;  //that 변수에 this 저장함으로써 접근 가능
	    		this.value+=1;
		    	console. log (this.value) ;
		    	func2:  function(){
			    	that.value+=1; 
			    	console.log(that.value);
		    	}
		    	func2();
	    	}
    };
    myObject.func1();
    =======================================
    102

