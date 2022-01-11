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
  
## 4) 'use strict';
- ES5에서 시작    
- 유연함에서 생기는 비상식적인 일 불가능하도록 막음 ex) 선언되지 않은 변수 값 할당 가능   
  
  
  
  
# 3. data types, let vs var, hoisting

## 1) variable VS constant
### 1-1) variable
#### a. 기본
- **rw**   
- **mutable: 변수가 메모리 어딘가 할당된 박스를 가르키기에, 포인터를 이용해 지칭하는 값을 계속 바꿀 수 있다.**
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
- **r**   
- **immutable: 값을 가리키는 포인터가 잠겨있어서, 할당 이후 값 변경 불가능**   
#### b. 장점 세 가지
- security   
- thread safety: thread들이 동시에 작동할 때 값을 변경하는 것을 막기 위해서   
- reduce human mistakes
### 1-3) 정리   
- Immutable data types: premitive types, frozen objects(i.e. object.freeze())
- Mutable data types: all objects by default are mutable in JS 

## 2) Variable types
어떤 언어든 아래 두 가지로 나뉘어진다.   
- a. primitive   
  - single item: 더이상 나눌 수 없는 단위   
  - number, string, boolean, null, undefined, symbol   
  - 메모리에 값 저장되는 방식: value 자체가 메모리에 저장됨   
- b. object   
  - box container: single item을 여러개 묶어서 한 박스로 관리함    
  - 메모리에 값 저장되는 방식: 크기에 한번에 메모리에 저장되지 못함. object를 가리키는 레퍼런스가 저장됨.   
- c. function   
  - first-class function: JS에서는 function도 변수에 할당이 가능하고, 또 그렇기에 함수 인자, ruturn타입으로 return할 수 있다.   
### 2-1) number   
C, Java와 달리 number만 있음. 심지어 number이라고 타입 선언하지 않아도 괜찮다.   
const count = 17; // integer => type:number   
const size = 17.1; // decimal number  => type:number   
### 2-2) number - speicla numeric values: infinity, -infinity, NaN
const infinity = 1 / 0;    
const negativeInfinity = -1 / 0;   
const nAn = 'not a number' / 2;   
* 값이 정말 valid한 값인지 확인하지 않으면 오류가 생길 수 있다.    
### 2-3) string
const char = 'c';   
const brendan = 'brendan';   
const greeting = 'hello ' + brendan; // value: hello brendon => type:string    
### 2-4) boolean
- false: 0, null, undefined, NaN, ''   
- true: any other value   
const canRead = true; // => value: ture/ type: boolean   
const test = 3 < 1; // => value: false/ type:boolean   
### 2-5) null
null이라고 할당, 즉 empty값이라고 지정   
let nothing = null; // => value: null, type: object   
### 2-6) undefined
선언은 되었지만 값은 지정하지 않았음   
let x; // => value: undefined, type: object undefined   
### 2-7) symbol, create unique identifiers for object
고유한 식별자가 필요할 때   
- map 등 자료구조에서   
- 동시다발적으로 일어나는 코드에서 우선순위를 설정해야 할 때   
const symbol1 = Symbol('id');   
const symbol2 = Symbol('id');   
  console.log(symbol1 === symbol2);// false   
const gSymbol1 = Symbol.for('id');   
const gSymbol2 = Symbol.for('id');   
  console.log(gSymbol1 === gSymbol2); // true   
- symbol 출력시: '.description' 이용하여 string으로 변환하지 않으면 출력시 오류   
console.log(`value: ${symbol1.description}, type: ${typeof symbol1}`); //  => value: id, type: symbol

## 3) object, real-life object, data structure
const ellie = { name: 'ellie', age: 20 };   
ellie.age = 21;   

## 4) Dynamic typing: dynamically typed language
let text = 'hello'; // => type: string   
text = 1; // => type: number   
text = '7' + 5; // => valueu: 75, type: string   
text = '8' / '2'; => valueu: 4, type: number   
- 이런 식으로 혼동이 생겨서 type을 지정하는 것이 typescript   




# 4. operator

## 1) String concatenation 
console.log('my' + ' cat');   
console.log('1' + 2);   
console.log(`string literals: 1 + 2 = ${1 + 2}`);   

## 2) Numeric operators
console.log(1 + 1); // add   
console.log(1 - 1); // substract   
console.log(1 / 1); // divide   
console.log(1 * 1); // multiply   
console.log(5 % 2); // remainder   
console.log(2 ** 3); // exponentiation   

## 3) Increment and decrement operators
let counter = 2;   
- const preIncrement = ++counter;   
// counter = counter + 1; //3   
// preIncrement = counter; // 3   
- const postIncrement = counter++;   
// postIncrement = counter; //3      
// counter = counter + 1; //4      

## 4) Assignment operators
let x = 3;   
let y = 6;   
x += y; // x = x + y;   

## 5) Comparison operators
console.log(10 < 6); // less than   
console.log(10 <= 6); // less than or equal   
console.log(10 > 6); // greater than   
console.log(10 >= 6); // greater than or equal   

## 6) Logical operators: || (or), && (and), ! (not)
'''
const value1 = true (혹은 false);
const value2 = 4 < 2;
function check() {
  for (let i = 0; i < 10; i++) {
    //wasting time
    console.log('😱');
  }
  return true;
}
'''   
#### || (or), finds the first truthy value
console.log(`or: ${value1 || value2 || check()}`);   
- 아래 and도 마찬가지이지만, 코드 작성시 과정이 가장 무거운 것을 마지막에 놓는 것이 좋은 코드   
#### && (and), finds the first falsy value
console.log(`and: ${value1 && value2 && check()}`);   
- often used to compress long if-statement    
- nullableObject && nullableObject.something   
#### ! (not)
console.log(!value1);   

## 7 ) Equality
'''
const stringFive = '5';
const numberFive = 5;
'''
#### == loose equality, with type conversion
console.log(stringFive == numberFive); // true   
console.log(stringFive != numberFive); // false   
#### === strict equality, no type conversion
console.log(stringFive === numberFive); // false   
console.log(stringFive !== numberFive); // true   
###  # object equality by reference
'''
const ellie1 = { name: 'ellie' };
const ellie2 = { name: 'ellie' };
const ellie3 = ellie1;
'''
console.log(ellie1 == ellie2); // false, 다른 레퍼런스가 저장되어 있음   
console.log(ellie1 === ellie2); // false, 레퍼런스 값도 다름   
console.log(ellie1 === ellie3); // true   
// equality - puzzler
console.log(0 == false); // true   
console.log(0 === false); // false, 0 bolean 아니어서   
console.log('' == false); // true   
console.log('' === false); // false, '' bolean 아니어서   
console.log(null == undefined); // true   
console.log(null === undefined); // false   

## 8) Conditional operators: if
'''
const name = 'df';   
if (name === 'ellie') {   
  console.log('Welcome, Ellie!');   
} else if (name === 'coder') {   
  console.log('You are amazing coder');   
} else {   
  console.log('unkwnon');   
}  
'''   

## 9) Ternary operator: ?
- if를 간단하게   
- condition ? value1 : value2;   
console.log(name === 'ellie' ? 'yes' : 'no');   

## 10) Switch statement
- use for multiple if checks    
- use for enum-like value check   
- use for multiple type checks in TS   
'''
const browser = 'IE';
switch (browser) {
  case 'IE':
    console.log('go away!');
    break;
  case 'Chrome':
  case 'Firefox':
    console.log('love you!');
    break;
  default:
    console.log('same all!');
    break;
}
'''




# 5. loops

## 1) while
- 조건문이 맞을 때만 실행하고 싶다면   
- while loop, while the condition is truthy,   
- body code is executed.   
'''
let i = 3;
while (i > 0) {
  console.log(`while: ${i}`);
  i--;
}

## 2) do while
-  block 먼저 실행하고 싶다면    
-  do while loop, body code is executed first,   
-  then check the condition.   
'''
do {
  console.log(`do while: ${i}`);
  i--;
} while (i > 0);
'''

## 3) for loop
- for(begin; condition; step)   
'''
for (i = 3; i > 0; i--) {
  console.log(`for: ${i}`);
}
'''
'''
for (let i = 3; i > 0; i = i - 2) {
  // inline variable declaration
  console.log(`inline variable for: ${i}`);
}
'''

## 4) nested loops
'''
for (let i = 0; i < 10; i++) {
  for (let j = 0; j < 10; j++) {
    console.log(`i: ${i}, j:${j}`);
  }
}
'''   

## 5) break, continue
- break: loop 완전히 끝냄   
- continue: 지금 것만 건너뜀   

