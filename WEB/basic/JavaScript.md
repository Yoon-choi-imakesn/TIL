#### [Dreamcoding 자바스크립트 기초 강의]


# 1. 자바스크립트의 역사와 현재 그리고 미래
- 10일만에 만든 유연한 언어  
- 다른 언어 기준 비상식적인 일들이 가능함 ex) 선언되지 않은 변수 값 할당 가능   


# 2. 콘솔에 출력, script async 와 defer의 차이점
## 1) node.js
node js에는 js 엔진이 있어서 브라우저 없이 실행할 수 있다.    
## 2) Web API
Web API: 브라우저가 이해하는 함수들  
여러 web API 중 console API가 있고 그중 한 함수가 log 
## 3) async VS defer
영상 좋음 https://www.youtube.com/watch?v=tJieVCgGzhs&list=PLv2d7VI9OotTVOL4QmPfvJWPJvkmv6h-2&index=2  
a. head 안   
  - 브러우저가 한줄한줄 파싱해서 돔으로 변환   
  <img src="img/async_1.png" width="600"/>  
b. body 끝  
  - html 가져오고 난 다음에 fetching js   
  - js 의존적일 경우 fetching 기다려야 함   
  <img src="img/async_2.png" width="600"/>   
c. asyn  
  - parsing 하다가 병렬적으로   
 <img src="img/async_3.png" width="600"/>  
d. defer  
  <img src="img/async_4.png" width="600"/>  
  
  <img src="img/async_5.png" width="600"/> 
  <img src="img/async_6.png" width="600"/> 
  
  
# 3. data types, let vs var, hoisting

## 1) variable VS constant

### 1-1) variable
#### a. 기본
**mutable: 변수가 메모리 어딘가 할당된 박스를 가르키기에, 포인터를 이용해 지칭하는 값을 계속 바꿀 수 있다.**
'''
let name = 'yoon'; 가리키는 것이 만들어짐
console.log(name);
name = 'cho'; 가리키는 대상은 달라질 수 있음
console.log(name);
'''
#### b. global/ local
- block scope에 들어가있는지 여부에 따라
#### c. let과 비교하는 var
- es5 이전   
- 선언 이전에도 할당/출력이 가능했음   
- *var hoisting*: 어디 선언했는지 상관 없이 선언을 제일 위로 올림   
- black scope이 없다, 즉 아무 곳에서나 사용 가능    
### 1-2) constant
#### a. 기본
**immutable: 값을 가리키는 포인터가 잠겨있어서, 할당 이후 값 변경 불가능**   
#### b. 장점 세 가지
- security   
- thread safety: thread들이 동시에 작동할 때 값을 변경하는 것을 막기 위해서   
- reduce human mistakes   

## 2) Variable types
12:40 number
15:10 infinity, NaN(not a number)
16:25 bigInt
17:25 string , ${variable}
18:45 boolean
19:20 null, undefined
20:00 symbol
21:40 dynamic typing
  
  

## 4) 'use strict';
- ES5에서 시작    
- 유연함에서 생기는 비상식적인 일 불가능하도록 막음 ex) 선언되지 않은 변수 값 할당 가능  
