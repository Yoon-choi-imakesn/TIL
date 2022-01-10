이미지 출처: 드림코딩 유튜브(드림코드 마크 있을 시), https://flexboxfroggy.com, 자체 제작   
내용 참조: 드림코딩 유튜브, 노마드코더 카카오 클론 강의

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

## 1) 의미, 정의
Cascading Style Sheet
정의된 세부 사항이 있다면 그것을 쓰고, 없다면 기본 지정된 것으로 넘어간다.  
- Author style
- User style
- Browser
[nomadcoder] 브라우저가 CSS를 읽을 때 위에서부터 순서대로 읽는다.  
CSS를 직접 적는 것을 inline CSS, CSS 파일을 include 하는 것을 external CSS라고 한다. 만약 같은 selector를 가리키는 CSS가 여러개이면, 가장 마지막 스타일이 적용된다.  

## 2) Selector
- universal *
- type Tag
- ID #id
- class .class
- state :
  - active, hover, focus, visited, focus-within(부모 요소에게 적용. 자신의 자식 요소 중 하나가 focused되었을 때 효과를 적용)
- attribute []
```
# state :
button:hover {
  color:red;
}
# attribute []
a[href] {
  color:green;
}
# attribute [] 세부적으로
a[href="naver.com] {
  color:green;
}
```

###  Pseudo Selectors (다양한 연습 https://flukeout.github.io/)
- A  B/ #id  A  
  - Descendant Selector: Select an element inside another element  
  - Selects all B inside of A. B is called a descendant because it is inside of another element.  
- A  *
- A + B: This selects all B elements that *directly* follow A.
- A ~ B: A ~ B selects all B that follow a A
- A > B: selects all B that are a direct children A
- :first-child: selects all first child elements  
  - p:first-child
  - div p:first-child
- :only-child: You can select any element that is the only element inside of another one.   
  - ex) plate pickle:only-child
  - 벤토 위, 접시 위에 각각 하나 씩 피클이 있을 때, 접시 위에 있는 피클만 고르고 싶을 경우
- :nth-child(A)/ nth-last-child(A)
- :nth-of-type(2)/(odd)/(even)/(2n+3)
- :first-of-type

## 3) 레이아웃 : dispay & position

### 3-1) display
##### a. block
  - 한 줄  
  - [nomadcoder] box임  
    -  옆에 아무것도 올 수 없다.  
    -  margin, padding, border 있음 
  - ex.div  
##### b. inline 
  - 컨텐츠를 꾸며준다    
  - ex.span(: 짧은 글귀)  
  - [nomadcoder] box 아님
    - margin(좌우만), padding, border 있음  
    - width, height 없다. 그래서 위, 아래에 margin을 가질 수 없다.    
    - 이와 같은 상황에 margin을 위, 아래에 적용하고 싶다면, inline 요소를 block으로 바꿔줘야 한다.  
##### c. inline-block  
  - 한 줄에 여러개 넣는데, 상자로 변환된다. 즉, 컨텐츠 크기에 상관 없이 지정한 width, height 등에 맞추어서  
  - [nomadcoder] block으로 인식하게 한다.  
    - width, height 가질 수 있고, 그래서 사방 margin을 가질 수 있다. 
    - 동시에 inline이어서 바로 옆에 다른 요소가 올 수도 있다.  
    - 문제점 많음 (간격 있고, 정해진 형식 없다.): 창 크기가 달라지면 박스 크기 달라질 수 있다. 
    - - **=> flex**

#####  *[nomadcoders] Collapsing margin*  
  - 상하에서만 발생함  
  - child box 경계가 parent box 경계와 같을 때 발생
  - 두 box의 margin이 하나가 된다, 큰 margin으로 통일됨.
  - **=> padding**

## 3-2) position 
https://developer.mozilla.org/en-US/docs/Web/CSS/position

<img src="Containing_Block.png" width="600"/>  
https://developer.mozilla.org/en-US/docs/Web/CSS/Containing_Block

##### a. static
  - 디폴트값
  - right, top 등 있어도 아무 영향 못 미침.  
  - **position 변경 기준: bloack container(즉 부모)**        
##### b. relative
  - 원래 있어야 하는 아이템에서 옮겨간 것
  - **position 변경 기준: bloack container(즉 부모)**     
##### c. absolute  
  - [nomadcoders] 가장 가까운 relative 부모를 기준으로 이동. position:relative; 를 해주면 부모가 된다. 없으면 body.  
  - [dreamcoding 이게 더 정확한 듯] 가장 가까운 부모 중 static이 아닌 부모 기준으로 이동. static이 아닌 한 사례가 rerlative   
  - [MDN] **The element is removed from the normal document flow**, and no space is created for the element in the page layout. **It is positioned relative to its closest positioned ancestor(=static이 아닌 부모)**, if any; otherwise, it is placed relative to the initial containing block. Its final position is determined by the values of top, right, bottom, and left.   
  - **position 변경 기준: 부모 중 static이 아닌 부모**   
##### d. fixed
  - 상자가 아니라, 페이지(윈도우) 상에서 옮겨간 것     
  - [nomadcoders] 레이어를 부수고 제일 위에 있는 새로운 레이어가 생겨서 거기 위치하게 된다. 
  - vh 크게 해서 스크롤 해도 따라오는 메뉴바에서 쓰임 (생각해보면 자연스레 부모 기준 sticky 보다는 전체 viewport 기준 fixed가 전체 홈페이지 메뉴바에 어울림.)
  - 부모 중 static이 아닌 부모   
  - **position 변경 기준: viewport** 
##### e. sticky 
  - 원래 자리에 있으면서 스크롤링해도 그 자리 유지
  - **position 변경 기준: bloack container(즉 부모) 그런데 이때 가장 근접한 부모 요소가 모든 요소를 말하는것이 아니고, 스크롤이 가능한 부모 요소중! **     
<img src="position.png" width="600"/>  

[nomadcoders]   
- 사용 용도: 레이아웃 차원이 아니라, 위치를 조금 옮기고 싶을 때 사용

## 4) Flexbox: container & item
### 4-1) main/cross axis
### 4-2) container
- display: flex;    
- flex-flow: column wrap;  
  - flex-direction: row/column-reverse;  
  - <img src="row-reverse.png" width="400"/>
  - flex-wrap: nowrap/wrap-reverse;  
    - [nomadcoders]  wrap 적용 안할 경우 자식 크기가 화면 사이즈에 따라 유동적으로 변화되나, 적용하면 initial 크기 유지  
- justify-content:  
  - *main axis*
  -  flex-start/felx-end/center/**space-around/space-between/space-evenly**;   
  - <img src="space-around.png" width="400"/>
  - <img src="space-between.png" width="400"/>
  - <img src="space-evenly.png" width="400"/>
- align-items:  
  - *cross axis - flex line을 기준으로 아이템 정렬*   
  - flex-start/felx-end/center/**baseline**;  
  - baseline: 텍스트가 균등하게 보이도록  
  - <img src="align-items.png" width="400"/>
- align-content:  
  - *cross axis - flex line을 정렬*  
  - flex-start/felx-end/center/**space-around/space-between**;  
  - align-content는 corss axis에 대한 justify-content라 이해할 수 있습니다.   
  - align-content는 여러 줄들 사이의 간격을 지정하며, align-items는 컨테이너 안에서 어떻게 모든 요소들이 정렬하는지를 지정합니다. 한 줄만 있는 경우, align-content는 효과를 보이지 않습니다.    

### 4-3) item
- flex: *grow, shrink, basis*  
  - flex-grow/shrink  
  - flex-basis: auto/30%;  
- align-self: center;  
  - item별로 아이템 정렬  

[nomadcoders] flex rules  
**1. 자식이 아니라 부모에게 명시한다**  
  - div의 부모를 display:flex로 만든다
  - 부모에 display: flex를 명시해야, 부모 자식 관계가 생김 ex. font-size 부모에 명시해서 자식에 적용 가능  
**2. main axis & cross axis**
  - justify-content는 main axis를 따라 움직임  
  - align-items는 cross axis를 따라 움직임

  

## 5) Responxive Web

### 5-1) 문법
  ```
  @media screen/speech/print/all and/not/only/, (min-width: 800px){
    .container {
      width: 50%;
    }
  }
  ```
  
### 5-2) absolute VS relative
- absolute: px
- relative: % v* em rem

### 5-3) 기준에 따른 사용
#### a. parent VS browser
  - parent: %, em
  - browser: v*, rem
#### b. box VS font
  - box: %, v*
  - font: re, rem

### 5-4) em VS rem
  - em: relative to parent element (font-size)
    ```
    ex.
    .parent {
      font-size: 8em;   # 디폴트 값 16px * 8 = 128px
    }
    .child {
      font-size: 0.5em;   # 128px * 0.5 = 64px
    }
    ```
  - rem: relative to root element (font-size)

 ```
 # 사례
        h1 {
            font-size: 1.75rem;
            color: palevioletred;
            margin: auto;
            text-align: center;  /* !!! */
        }
        .container {
            display: flex;
            padding: 2em; /*32px*/
        }
        /* uncalled properties at @media follow above normal properties */
        @media screen and (max-width: 768px) {
            .container {
                flex-direction: column;
            }
        }
        .component {
            border: 1px solid palevioletred;
            margin: 1em  /*16px: font-size 기준이기에*/
        }
        .title {
            font-size: 1.5rem;
            padding: 1em;
            background-color: palevioletred;
        }
        .contents {
            font-size: 1.125rem;
            padding: 1em;
        }
```
 

## 6) useful tips
- Q) 덕분에 반응형에 대한 개념을 좀 더 알아갈 수 있었습니다! 혹시 padding, margin, font 등 크기를 설정할 때 어떤 기준이 있으신가요? 임의적으로  적당한 사이즈를 넣는 것인지 아니면 컨벤션이 따로 있는 것인지 알고 싶습니다. 아니면 디자이너와 협업할 때 시안대로 사이즈를 작성하시나요 ?  
- A) 현업에서는 디자이너가 제공해준 시안에 지정된 값을 사용하구요.
개인 프로젝트를 이용할때는 제가 적당한 사이즈를 넣는데, 그냥 아무 숫자나 넣는건 아니구 저는 Material Design Guidelines를 따라 가고 있어요.
예를 들어 스페이싱을 줄때 4배수로 넣고 (4, 8, 12, 16..) 그리고 간격은 최소 16dp가 좋고 버튼은 최소 32dp (아, 48dp 였나? 기억이 가물) 쓰고. 
딱히 이런 숫자를 따라하야 하는건 아니구요 :) 사용자가 쓸때 편리한지, 마우스로 쓸때 괜찮은지, 터치디바이스 (폰, 태블릿)에서 손가락으로 눌렀을때 적당한 크기 인지를 보고 일정한 값을 프로젝트에서 쓰는게 중요해요 🤗 
머테리얼 디자인에 대해 더 공부해 보고 싶으시다면: https://material.io/design/layout/understanding-layout.html#usage  

[nomadcoders]
## 7) transition & transformation
### 7-1) transition
  #### a.  기본
  - 어떤 상태에서 다른 상태로의 변화를 보내주는 애니매이션        
  - rule1: transtion은 state가 없는 요소에 붙어야한다 (state에 있다면, state 해당 안되면 원상태로 바로 돌아감 ex. hover 떼면)      
  - rule2: transtion 에 변화를 준것들은 state에 들어있는 것들, 즉 바뀌는 것들에 한정      
  - 효과와 해당 코드 확인 사이트 https://matthewlein.com/tools/ceaser 
  #### b.  문법
  ```
    a {
      background-color: wheat;
      color: tomato;
      border-radius: 50px;
      transition: background-color 3s ease-in-out, color 10s ease-in-out;
    }
    a:hover {
      background-color: tomato;
      color: wheat;
    }
  ```
### 7-2) transformation
https://developer.mozilla.org/en-US/docs/Web/CSS/transform
  #### a.  기본
  - 한 요소를 말 그대로 변형시킴, css로 3D까지 가능   
  - transform은 box 차원이 아니라 pixel 차원이기에, padding margin값을 줘도 적용이 안된다   
  - 즉 sibling들에게 영향을 끼치지 않는다 해당 요소만 적용을 시키기 때문 
  #### b.  문법
  ```
    img {
      border: 10px soild black;
      border-radius: 50%;   <!-- 원 -->
      transition: transform 10s ease-in-out;
    }
    img:hover {
      transform: rotateY(90deg) scale (0.5)
    }
  ```
  
  
## 8) Animation <- transition & transformation
  #### a.  기본
  - animation: 원하는만큼 만들고 재생 가능   
  - cf) transition & transformation: state일 때만 효과   
  - transform 이외 property들도 애니매이션으로 만들 수 있으나, transform을 쓰는걸 권한다. 일부 property는 애니매이션이 잘 안되기 때문.   

  #### b.  문법
  ```
    @keyframes superSexyCoinFlip {
      0% {
        transform: rotateY(0);
      }
      50% {
        transform: rotateY(180deg) translateY(100px);
      }
      100% {      <!-- 0%이랑 맞추어야 예쁨 -->
        transform: rotateY(Y) translateY(0px);
      }
    }
    img {
      border: 10px soild black;
      border-radius: 50%;   <!-- 원 -->
      animation: superSexyCoinFlip 10s ease-in-out infinite;
    }
  ```
  
  ## 9) 추가 내용
  ### 9-1) Box Sizing
  https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing   
  <img src="boxsizing.png" alt="drawing" height="600"/>   
  - box-sizing: border-box;   
    - border까지의 영역을 정하기 때문에, border+padding 넣은만큼 content box 크기는 작아진다.   
    - 통상적으로 패딩 넣을 때, 박스 안에 여백 만들기 때문에, 대부분  box-sizing: border-box; 이용   
  - box-sizing: content-box;   
    - content box를 결정하기에, content box 사이즈는 변하지 않는다.    
### 9-2) Centerinig trick   
  <img src="centering.png" alt="drawing" height="600"/>   
### 9-3) Responsive background
  ```
  .box1 {
  background-image: url('');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  
  background: center/cover no-repeat
    url('');
  }
  ```

