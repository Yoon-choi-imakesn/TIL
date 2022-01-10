#### [Dreamcoding 자바스크립트 기초 강의]


# 1. 자바스크립트의 역사와 현재 그리고 미래
- 10일만에 만든 유연한 언어
- 다른 언어 기준 비상식적인 일들이 가능함 ex) 선언되지 않은 변수 값 할당 가능


# 2. 콘솔에 출력, script async 와 defer의 차이점 및 앞으로 자바스크립트 공부 방향
## 1) node.js
node js에는 js 엔진이 있어서 브라우저 없이 실행할 수 있다. 
## 2) Web API
Web API: 브라우저가 이해하는 함수들
여러 web API 중 console API가 있고 그중 한 함수가 log
## 3) async VS defer
영상 좋음 https://www.youtube.com/watch?v=tJieVCgGzhs&list=PLv2d7VI9OotTVOL4QmPfvJWPJvkmv6h-2&index=2
1)  head 안
  - 브러우저가 한줄한줄 파싱해서 돔으로 변환
2) body 끝
  - html 가져오고 난 다음에 fetching js
  - js 의존적일 경우 fetching 기다려야 함
3) asyn
  - parsing 하다가 병렬적으로
4) defer

## 4) 'use strict';
- ES5에서 시작
- 유연함에서 생기는 비상식적인 일 불가능하도록 막음 ex) 선언되지 않은 변수 값 할당 가능
