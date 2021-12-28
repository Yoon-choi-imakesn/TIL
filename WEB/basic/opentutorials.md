# HTML

### Attribute 속성
src="Goya.jpg", width="50%"  
속성은 태그의 이름만으로는 정보가 부족할 때 사용됩니다.  


# CSS

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
  
    
