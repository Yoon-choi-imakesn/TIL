##### 01.03.2022
##### text element & center
- Problem) 하나의 parent element 안에 h1과 p가 있을 때 'h1&p 자체' 'h1&p 안에 있는 text' - 이 두 가지 모두를 어떻게 cent에 위치시킬 것인가.   
- category) HTML text element (https://developer.mozilla.org/en-US/docs/Web/HTML/Element)    
- at) kokoa clone coding - index.css        
- Solution) 
  ```
  .welcome-header {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 90px 0px;
    text-align: center;
    /* 안에 있는 h1, p 모두 text element이기에 가능 
        : h1 안에 있는 text, p 안에 있는 text를 센터로
      h1, p 자체를 center로 위치시키는 것은 display: flex 사용 */
  }
  ```
 - What I learned     
   - text-align은 text element 안의 text를 align함
   - text element 즉 box 자체의 위치를 바꾸고 싶을 때는 display 속성 이용

