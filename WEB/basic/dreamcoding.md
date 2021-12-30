자료 출처: 드림코딩 유튜브

# 1. HTML

## 1) 태그는 두 가지로 구분 가능
- a. box: sectionig을 도와줌
- b. item  
<img src="box&item.png" alt="drawing" width="600"/>
<img src="sectioning1.png" alt="drawing" width="600"/>
<img src="sectioning2.png" alt="drawing" width="600"/>
article: 반복되는 것을 묶어줌

## 2) Tag & Element & Attribute
<img src="Tag&Element.png" alt="drawing" width="600"/>
element, 다른 말로 node라고도 한다.
<img src="Attribute.png" alt="drawing" width="600"/>
  
## 3) Black & Inline
block ex.div
inline ex.span

## 4) Input & Type
<img src="input&type.png" alt="drawing" width="600"/>

# 2. CSS

### CSS 삽입 방법 두 가지
a. <style> 태그  
b. style이라는 속성  
  - style이라는 속성을 쓰면 그 속성의 값을 웹 브라우저가 CSS 문법에 따라 해석해서 그 결과를 style 속성이 위치한 태그에 적용합니다.
  - style=""은 HTML의 속성
  - style이라는 속성은 값으로 반드시 CSS 효과가가 들어온다고 약속되어 있습니다. 
  
## CSS 문법
a{  
  color:red;  
}  
- "a": selector 선택자
- "color:red;": declaration 선언, 효과
- "color": property 속성
- "red": value 값

## selector
전제: 구체적일수록 우선 순위 높음, 반대로 추상적일수록(포괄적일수록) 우선 순위 낮음  
똑같은 형태의 선택자라면 맨 마지막에 등장하는 선택자가 우선순위가 높다 (CSS가 순서대로 작동하는가? 그렇다면 마지막이 앞선 코드 실행을 덮을 수 있어서 그러한가)
낮은 우선 순위대로
- 태그 선택자
- class 선택자(.)
- id 선택자(#)
  - id 값은 단 한번만 등장해야 한다(마치 학생 ID가 고유한 것처럼)  
* #gird ol 등 특정 선택 가능
  
## box
#### box model  
  ![box model](./1_css_boxmodel.png)  
#### alignment 기본값 두 가지
  - block level alignment (ex. div)
  - inline alignment (ex. span)
  - display 속성 이용하여 변경 가능
  
## 캐싱 cache: CSS 파일 사용 이유
  cache: 저장한다라는 의미. css 파일을 한번 다운로드했다면, 웹 브라우저가 해당 파일을 컴퓨터에 저장한다. 따라서 네트워크 트래픽을 훨신 더 적게 쓸 수 있다. 
  

# 3.JavaScript  

### JS 기본 정리  
  - JS는 HTML을 제어하는 언어이다.  
  - 자바스크립트 코드가 와야 하는 속성 값이 존재한다 (ex. on-)  
  
## 이벤트  
  - 이벤트는 자바스크립트가 사용자와 상호작용하는 데 핵심적인 역할을 합니다.
  - *this*
       이벤트 안에서 실행되는 코드에서 현재 코드가 속해 있는 태그를 가리키도록 약속돼 있는 특수한 키워드  

## 문법
  #### 1) 변수와 대입연산자
  #### 2) 프로퍼티(properties) ex. .length
  #### 3) 함수  
  ##### a. 기본적인 분법  
          ```
          function sum(left, right) {
            document.wirte(legt + right + '<br>');
          }
          sum(2,3);
          ```
  ##### b. 매개변수 parameter: 인자를 받아서 함수 안으로 매개하는 변수
           ex. left, right
  ##### c. 인자 argument: 함수로 전달하는 값
           ex. 2, 3
  ##### d. return 키워드

## 객체  
### 기본
 여기서 정리할 객체의 특성: 정리 정돈의 수단으로써의 객체  
 함수와 변수가 많아지면 연관된 것들을 정리 정돈하는 도구  
  cf) 함수: 코드가 많아지면 정리 정돈하는 도구  
  ### 객체가 담을 수 있는 대상
  - 데이터: 문자열, 배열, 숫자 등
  - 함수도 담을 수 있다.
### 문법
  #### a. 객체 생성
  ```
  <script>
    // cats이라는 변수에 객체를 담는다. 
    var cats = {
        "우이동 고양이":"김석관",
        "중화동 고양이":"최까루"
     }
    </script>
  ```
  #### b. 객체와 반복 (feat. key(aka. index))
  ```
  <script>
    for(var key in cats) {
       document.write(key + ' : ' + cats[key] + '<br>');
    }
  </script>
  ```
  #### c. 객체 프로퍼티와 메서드(feat. this)
  - 메서드: 객체에 소속된 함수 ex. toUpperCase(), querySelectorAll()
  - 프로퍼티: 객체에 소속된 변수 ex. length
  ``` 
  // this 적용 전
  <script>
    // showAll()이라는 메서드 추가
    cats.showAll = function {
      for(var key in cats) {
         document.write(key + ' : ' + cats[key] + '<br>');
      }
    }
    cats.showAll();
  </script>
  ```
  ``` 
  // this 적용 후
  <script>
    // showAll()이라는 메서드 추가
    cats.showAll = function {
      for(var key in this) {
         document.write(key + ' : ' + this[key] + '<br>');
      }
    }
    cats.showAll();
  </script>
  ```
  ``` 
  // 객체 선언과 동시에 메서드 생성하는 법
var Body = {
  setColor: function (color) {
    document.querySelector('body').style.color = color;
   },
  setBackgroundColor: function (color) {
    document.querySelector('body').style.backgroundColor = color;
   }
}
  ```
 
# 4. etc

### 프로그래밍 언어
HTML, JS 둘 다 컴퓨터 언어이지만, HTML은 프로그래밍 언어가 아닙니다.  
프로그래밍 언어는 시간 순서에 따라 실행돼야 할 기능을 갖춘 문법으로 이루어진 컴퓨터 언어를 프로그래밍 언어라고 합니다. 
  
## refactoring
  - 코드의 가독성을 높이고  
  - 유지보수를 편리하게 만들고
  - 중복된 코드를 줄임
### a. this  
  : 이벤트 안에서 실행되는 코드에서 현재 코드가 속해 있는 태그를 가리키도록 약속돼 있는 특수한 키워드
### b. 변수
```
# this 적용 전
<input id="night_day" type="button" value="night" onclick="
  if(document.querySelector('#night_day').value=='night') {
    document.querySelector('body').style.backgroundColor = 'black';
    document.querySelector('body').style.color='white';
    document.querySelector('#night_day').value = 'day';
  } else {
    document.querySelector('body').style.backgroundColor = 'white';
    document.querySelector('body').style.color='black';
    document.querySelector('#night_day').value = 'night';
  }
">
  
# this 적용 후
<input type="button" value="night" onclick="
  if(this.value=='night') {
    document.querySelector('body').style.backgroundColor = 'black';
    document.querySelector('body').style.color='white';
    this.value = 'day';
  } else {
    document.querySelector('body').style.backgroundColor = 'white';
    document.querySelector('body').style.color='black';
    this.value = 'night';
  }
">
  
# 변수 적용 후 
<input type="button" value="night" onclick="
 var target = document.querySelector('body');                                          
  if(this.value=='night') {
    target.style.backgroundColor = 'black';
    target.style.color='white';
    this.value = 'day';
  } else {
    target.style.backgroundColor = 'white';
    target.style.color='black';
    this.value = 'night';
  }
">
```
  
  
