해당 내용은 코딩애플🍎 수업을 듣고 정리한 글입니다.

# Selector
- document.getElementById( id이름 )
- document.getElementsByClassName( class이름 )
- document.getElementsByName( name이름 )
- document.querySelector( 셀렉터 )
<br/>
<br/>

# 변수 (Variables) 
## var
- Global Scope
```Javascript
// 1. Global scope
{
  var x = 2;
}
// x CAN be used here

// 2. 동일 이름으로 재선언 가능
var x = "John Doe";
var x = 0; // 가능
```

## let
- ES6 부터 사용 가능, Block scope
```Javascript
// 1. Block scope
{
  let x = 2;
}
// x can NOT be used here

// 2. 동일 이름으로 재선언 불가
let x = "John Doe";
let x = 0;    // 불가능
```

## const
- ES6 부터 사용 가능, Block scope, 변수값 변경 불가능
```Javascript
const PI = 3.141592653589793;
PI = 3.14;      // This will give an error
PI = PI + 10;   // This will also give an error
```

## `var` vs `let` vs `const`   
| **Type** | **범위**             | **재선언**     | **재할당**    | **`this`에 바인딩** |
|----------|----------------------|---------------|--------------|-------------------|
| `var`    | function-scoped      | Yes           | Yes          |  Yes              |
| `let`    | {Block-scoped}       | No            | Yes          |  No               |
| `const`  | {Block-scoped}       | No            | No           |  No               |   
<br/>

## Declaring Variables Shorthand (변수 단축 선언)
같은 선언 타입을 가진 변수를 한줄로 선언. const로 단축 선언 시, 초기값 할당하지 않으면 SyntaxError 발생.
```JavaScript
let a,
    b = 1,
    c;
//a : undefined
//b : 2
//c : undefined

const d = 4,
    e = 5;
//const d,e=5; => Uncaught SyntaxError: Missing initializer in const declaration
```
<br/>
<br/>

# 함수 (function)
- 긴 코드를 짧게 축약
- 특정 파라미터를 받고 원하는 결과를 출력(return)
## 문법
```Javascript
function functionName (parameter1, parameter2, ...) {
  // 실행 할 코드

  // 출력할 결과물
  return "result";
}
```

> <details>
> <summary> 함수에서 (소수)계산 오류 발생이유</summary>   
> 
> ```javascript
> console.log(1.1 + 0.3) // 기대값: 1.4 , 실제 출력값: 1.40000000001
> ```
>
> **원치않는 결과 값이 나오는 이유?**
> - 컴퓨터는 2진법으로 설계되어 있음. 예를 들어, `10+20` 을 하라고 한다면 `1010(2) + 10100(2)` 으로 연산하고 다시 10진법으로 바꿔서 보여줌.
> - 근데 일부 숫자는(ex) 1.1)은 2진법으로 바꿨을때 딱 나눠떨어지지 않고 패턴이 무한이 반복됨.
> - 때문에 컴퓨터는 적당히 끊고 반올림 하여 저장하기 때문에 `소수들끼리의 연산`은 `아주 작은 오차 발생 가능성` 있음
>
> **해결 방법?**
> - 덧셈하기 전에 10 곱해서 덧셈하고 10으로 나눔
> - 외부 라이브러리 활용
> - 오차는 무시할 정도로 작으니 그냥 반올림
> </details>
<br/>
<br/>

# 이벤트 (Event)
## 문법
```Javascript
// Event Listener 생성
document.getElementById('어쩌구').addEventListener('click', function(){
  // 실행 할 코드 
});

// Event Listener 제거
document.getElementById('어쩌구').removeEventListener('click', function(){
  // 실행 할 코드 
});
```

## 이벤트 종류
| **그룹**           | **설명**                                                                  | **이벤트 종류**                   | 
|-------------------|---------------------------------------------------------------------------|---------------------------------|
| **Drag and Drop** | Events related to the Drag and Drop API. Drag events fired on `Document`. | drag, dragover, dragstart, drop.|
| **Focus**         | Events related to elements gaining or losing focus. Events fired on `Element`, `Window`. | blur, focus, focusout |
| **Form**          | Events related to forms being constructed, reset, or submitted. Events fired on `HTMLFormElement`.| submit  |
| **Inputs**        | Events related to HTML input elements (`<input>`, `<select>`, `<textarea>`). Events fired on `HTMLElement`, `HTMLInputElement`.    | cancel, change, select, input|
| **Keyboard**      | Events related to keyboard interactions. Notifies when keys are pressed, released, or moved. Events fired on `Document`, `Element`.| keydown, keypress, keyup|
| **Mouse**         | Events related to mouse interactions. (e.g., clicks, double clicks, movement, etc.). Mouse events fired on `Element`.              | click, dbclick, mousedown, mouseenter, mouseleave, mousemove, mouseout, mouseover, mouseup, scroll |
| **Timing**        | Events related to time. Events fired on `Window`.                          | setTimeout, clearTimeout, setInterval, clearInterval|

- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/Events)
- [W3Schools](https://www.w3schools.com/jsref/dom_obj_event.asp)
<br/>
<br/>

## Event Bubbling
- 어떤 HTML 태그에 이벤트가 발생하면 그의 모든 상위 요소까지 이벤트가 실행되는 현상

### Event Bubbling 막는 법
```javascript
  document.querySelector('.black-bg').addEventListener('click', function(e){
    e.target;            // 실제 클릭한 요소
    e.currentTarget;     // 이벤트 리스너가 달린 곳 (this와 동일)
    e.preventDefault();  // 이벤트의 기본 동작을 막음.
    e.stopPropagation();; // 상위요소로의 이벤트 버블링을 막음.
  })
```

# 조건문
## if/else
```Javascript
if (조건식){
  실행할코드
} else if(또 다른 조건식) {
  실행할 코드
} else {
  실행할 코드
}
```

## Switch
```javascript
let 변수 = 2 + 2;

switch (변수){
  case 3 :
    alert('변수가 3이네요');
    break
  case 4 :
    alert('변수가 4네요');
    break
  default : 
    alert('다 아니네')
}
```

## Short-circuit Evaluation (단축 평가 값)
논리 연산자는 왼쪽에서 오른쪽으로 실행되므로, `||`인 경우 왼쪽에서 true가 나오면, 더 이상 오른쪽의 값은 평가되지 않고 바로 종료.<br/>
하지만, `&&` 인 경우 끝까지 실행.
- true가 되는 조건: 값이 존재   
- false가 되는 조건: null, undefined, false, etc.
```JavaScript
const str = "some text";
const result1 = str || "default value";
// result1 = "some text";

const nothing = null;
const result2 = nothing || "default value";
// result2 = "default value";

const result3 = str && "If str is truthy return this";
//result3 = "If str is truthy return this"
```
<br/>
<br/>

# 반복문 (Loop)
| **반복문**              | **설명**                                                                 |
|------------------------|-------------------------------------------------------------------------|
| [for](#1-for)          | 코드를 정해진 횟수만큼 반복 실행                                             |
| [for/in](#2-forin)     | 객체의 속성(property)을 반복 실행                                           |
| [for/of](#3-forof)     | 반복 가능한(iterable) 객체의 값을 반복 실행                                  |
| [while](#4-while)      | 주어진 조건이 참(`true`)인 동안 코드를 반복 실행                              |
| [do/while](#5-dowhile) | 주어진 조건이 참(`true`)인 동안 코드를 반복 실행. 조건을 확인하기 전에 한 번은 실행|


## 1) for 
```javascript
/**
 * for (초기화; 조건; 증감) {
 * // 실행할 코드
 * }
*/

const cars = ["BMW", "Volvo", "Saab", "Ford", "Fiat", "Audi"];
let   text = "";

for (let i = 0; i < cars.length; i++) {
  text += cars[i] + " ";
}

console.log(text); // BMW Volvo Saab Ford Fiat Audi
```

## 2) for/in 
- `key: value`로 이루어진 object 타입에서 사용하고, `출력 순서가 보장되지 않음`.
- Array에서 사용 시 눈에 보이는 배열의 element 뿐 아니라, 눈에 보이지 않는 프로토타입 속성의 인덱스까지 모두 돌며 반복되고, index 보장도 안됨.

```javascript
/**
 * for (key in object) {
 * // code block to be executed
 * }
*/

// key:value 타입
const person1 = {fname:"John", lname:"Doe", age:25};

let text1 = "";
for (let key in person1) {
  text1 += person1[key];
}
console.log(text1); // John Doe 25
```

## 3) for/of
- [iterable object(Arrays, Strings, Maps, NodeLists)](https://www.w3schools.com/js/js_iterables.asp)에서 사용하고 `순서가 보장`. `주로 배열`에서 사용. 
- `key: value`로 이루어진 object 타입에서 사용할 경우 에러 발생(`Uncaught TypeError: obj is not iterable`)
```javascript
/**
 * for (variable of iterable) {
 *   // code block to be executed
 * }
*/

// 1) Array인 경우
const cars = ["BMW", "Volvo", "Mini"];

let text1 = "";
for (let value of cars) {
  text1 += value;
}
console.log(text1); // BMW Volvo Mini

// 2) String인 경우
let language = "JavaScript";

let text2 = "";
for (let x of language) {
  text2 += x + " ";
}
console.log(text2); // J a v a S c r i p t
```

## 4) while 
- 조어진 조건이 참인 경우, 반복 실행
```javascript
while (condition) {
  // code block to be executed
}
```

## 5) do/while 
- 조어진 조건이 참인 경우 반복 실행되나, 거짓이여도 최초의 1번은 실행됨
```javascript
do {
  // code block to be executed
}
while (condition);
```


# 자료형 (Data Types)
## 1. 원시형 (Primitive types)    
  | **Type**                     | **`typeof` Return Value** | **Object Wrapper**  |
  |------------------------------|---------------------------|---------------------|
  | [**Null**](#1-null)          | `object`                  | N/A                 |
  | [**Undefined**](#2-undefined)| `undefined`               | N/A                 |
  | [**Boolean**](#3-boolean)    | `boolean`                 | `Boolean`           |
  | [**Number**](#4-number)      | `number`                  | `Number`            |
  | [**BigInt**](#5-bigint)      | `bigint`                  | `BigInt`            |
  | [**String**](#6-string)      | `string`                  | `String`            |
  | [**Symbol**](#7-symbol-type) | `symbol`                  | `Symbol`            |

> null을 제외한 모든 기본 타입은 `typeof` 연산자로 테스트 가능. `typeof null`은 "object"를 반환하므로 `=== null`을 사용하여 테스트   

### 1) Null
- Null 타입은 null이라는 오직 하나의 값만 가질 수 있음
```Javascript 
let nulltype = null;
```

### 2) Undefined
- Undefined 타입은 `undefined`이라는 오직 하나의 값만 가질 수 있음
- `Undefined`는 값이 없음을 의미하고 `null`은 객체가 없음을 의미   
  ex) 존재하지 않는 객체 속성에 접근, 초기화가 없는 변수 선언

### 3) Boolean
- `true / false` 두 가지 값을 가짐
- 일반적으로 `삼항연산자`, `if/else`, `while` 등을 포함한 조건부 연산에서 사용
```Javascript 
let x = true;
let y = false;
```

### 4) Number
- ±(-2<sup>-1074</sup> 와 -2<sup>1024</sup>) 범위의 숫자 저장
- 'NaN': **N**ot **a** **N**umber, 계산 결과값이 숫자가 아닌 경우.
```Javascript 
// 1. 변수 선언
let x = 3.14;            // A number with decimals
let y = 3;               // A number without decimals
let z = 123e5;           // 12300000
let w = 123e-5;          // 0.00123

// 2. 값이 숫자인지 아닌지 확인
let x = 100 / "Apple";
isNaN(x);  // true, but NaN은 number 이므로 typeof NaN은 number를 리턴.

// 3. Object 타입의 숫자
let x = new Number(123);
let a = new Number(123); // a는 number가 아니라 object임 => new로 선언하였으므로.

console.log( x == y );  // false => Object 타입의 경우, 보이는 값이 아니라 주소값을 저장하고 있으므로 같을 수 없음.
console.log( x === y ); // false
```

| **Method**                                   | **설명**    |
|----------------------------------------------|------------|
| [number].toString()                          | 문자로 변환  |
| [number].parseInt()                          | 정수로 변환  |
| [number].parseFloat()                        | 실수로 변환  |


### 5) BigInt
- BigInt는 Number의 범위를 넘어서는 큰 정수도 안전하게 저장하고 연산할 수 있음.
- 범위가 굉장히 크므로 일반적으로는 Number 사용

### 6) String
```Javascript 
let color    = "Yellow";                     // Double quotes
let lastName = 'Johnson';                    // Single quotes
let answer1  = "It's alright";               // Use quotes inside a string
let text     = `He's often called "Johnny"`; // Template Strings
```

**- Escape Characters**
| **Code** | **Result**       |
|----------|------------------|
| `\'`     | `'`              |
| `\"`     | `"`              |
| `\\`     | `\`              |
| `\b`     | Backspace        |
| `\f`     | Form Feed        |
| `\n`     | New Line         |
| `\r`     | Carriage Return  |
| `\t`     | Horizontal Tab   |
| `\v`     | Vertical Tab     |

  ex)      
  ```Javascript
  // string에서 따옴표 또는 쌍따옴표를 쓰고 싶을 경우 `escape characters` 사용 가능.
  let text1 = "We are the so-called \"Vikings\" from the north."; // We are the so-called "Vikings" from the north.
  let text2 = 'It\'s alright.';                                   // It's alright.
  let text3 = "The character \\ is called backslash.";            // The character \ is called backslash.
  ```

**- Methods**
| **Method**                                   | **Description**                                                                        |
|----------------------------------------------|----------------------------------------------------------------------------------------|
| [text].length                                | 문자열 길이                                                                              |
| [text].charAt(n)                             | 문자열의 `n`번째 글자                                                                     |
| [text].charCodeAt(n)                         | 문자열의 `n`번째 글자의 유니코드                                                            |
| [text].slice(start, end)                     | `start`부터 `end`전 까지의 문자. <br/> `end`는 필수X. `end`가 없을 경우, `start` 부터 끝까지. |
| [text].substring(start, end)                 | `start`부터 `end`전 까지의 문자. `slice()`와 유사.                                         |
| [text].substr(start, length)                 | `start`부터 `length`만큼의 문자.                                                          |
| [text].toUpperCase()                         | 전부 다 대문자로 변환                                                                     |
| [text].toLowerCase()                         | 전부 다 소문자로 변환                                                                     |
| [text].concat(text1, text2)                  | 기존 문자열에 `text1`과 `text2` 합침                                                      |
| [text].trim()                                | 시작과 끝의 공백 문자 제거                                                                  |
| [text].padStart(length, text)                | 문자열 앞에 `length` 만큼 `text` 추가 ex) [text].padStart(4,"0"); // 0000[text]            |
| [text].padEnd()                              | 문자열 뒤에 `length` 만큼 `text` 추가                                                      |
| [text].replace(originalText, replaceText)    | `originalText`를 `replaceText`로 치환하는데, 일치하는 첫번째 문자만 치환.                     |
| [text].ReplaceAll(originalText, replaceText) | `originalText`를 `replaceText`로 치환하는데, 일치하는 모든 문자만 치환.                       |
| [text].split(separator)                      | 문자열을 `separator`로 잘라서 `array` 타입으로 리턴                                         |
| [text].indexOf(searchText)                   | 문자열에서 `searchText`를 찾아서 위치(숫자) 리턴                                             |
| [text].search(searchText)                    | 문자열에서 `searchText`를 찾아서 위치(숫자) 리턴. indexOf() 와 유사하나, regular expression 사용 가능하다는 특징이 있음.|
| [text].match(searchText)                     | 문자열에서 `searchText`를 찾아서 `array` 타입으로 리턴. regular expression 사용 가능           |
| [text].includes(searchText)                  | 문자열에서 `searchText`를 찾아서 `true/false` 리턴.                                         |
- [String methods](https://www.w3schools.com/js/js_string_methods.asp)   
- [String Search](https://www.w3schools.com/js/js_string_search.asp)

**- Templates**
`백틱(``)`을 사용하여 문자열 정의하는 방법

```Javascript
// 1. 일반 문자열
let text = `Hello World!`;

// 2. 문자열 합치기
let firstName = "John";
let lastName = "Doe";
let text     = `Welcome ${firstName}, ${lastName}!`;   // Welcome John, Doe!

// 3. 숫자계산 
let price = 10;
let VAT = 0.25;
let total = `Total: ${(price * (1 + VAT)).toFixed(2)}`; // Total: 12.50

// 4. 반복문에서 사용
let header = "Template Strings";
let tags = ["template strings", "javascript", "es6"];

let html = `<h2>${header}</h2><ul>`;
for (const x of tags) {
  html += `<li>${x}</li>`;
}

html += `</ul>`;

/*
<h2>Template Strings</h2>
<ul>
  <li>template strings</li>
  <li>javascript</li>
  <li>es6</li>
</ul>
*/
```

### 7) Symbol type
- 유하고 변경 불가능한 원시(Primitive) 값


## 2. 객체 타입 (Object types)  
  | **Type**                      | **`typeof` Return Value** |
  |-------------------------------|---------------------------|
  | [**Objects**](#1-object)      | `objects`                 |
  | [**arrays**](#2-arrays)       | `arrays`                  |
  | [**dates**](#3-dates)         | `dates`                   |
  | [**maps**](#4-maps)           | `maps`                    |
  | [**sets**](#5-sets)           | `sets`                    |
  | [**intarrays**](#6-intarrays) | `intarrays`               |
  | [**promises**](#7-promises)   | `promises`                |


### 1) object
- 많은 변수/함수를 한번에 담을 수 있는 객체 타입으로 `key: value`의 쌍으로 이루어져 있음.   
- Object객체는 순서 개념 없음

```Javascript
// 1. 변수 선언
// 1-1) 값 할당과 동시에 객체 생성
let person1 = {
  firstName: "John",
  lastName : "Doe",
  age      : 50,
  eyeColor : "blue",
  fullName: function () {
    return this.firstName + " " + this.lastName;
  }

// 1-2) 객체 생성 후 properties 및 값 할당
const person2 = new Object();

person2.firstName = "John";
person2.lastName = "Doe";
person2.age = 50;
person2.eyeColor = "blue";
person2.fullName = function () {
  return this.firstName + " " + this.lastName;
}

// 1-3) 생성자(Constructor) 함수를 이용하여 선언
function Person(first, last, age, eye) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eye;
}
const myFather = new Person("John", "Doe", 50, "blue");
const myMother = new Person("Sally", "Rally", 48, "green");

// 1-4) 객체에 속성으로 사용하려는 키 값과 같은 이름의 변수가 있을 경우, key: value할당을 축약형으로 사용하여 선언
const a = 1, b = 2, c = 3;
const obj1 = { a: a,  b: b, c: c };
const obj2 = { a, b, c }; // {a:1,b:2,c:3}


// 2. 값 사용: objectName.property 또는 objectName[property]
let firstName = person1.firstName;    // John
let lastName  = person1.lastName;     // Doe
let age       = person1.age;          // 50
let eyeColor  = person1.eyeColor;     // blue
let fullName  = person1.fullName;     // John Doe

let firstName = person1["firstName"]; // John
let lastName  = person1["lastName"];  // Doe
let age       = person1["age"];       // 50
let eyeColor  = person1["eyeColor"];  // blue
let fullName  = person1.fullName();   // John Doe

// 3. 값 삭제
delete person1.age;
delete person1["eyeColor"];
```
<br/>

### 2) arrays
- 여러가지 자료를 한곳에 저장하고 싶을 때 사용하는 타입으로 순서가 있음.
```javascript
// 1. 배열 생성
var cars = ["소나타", 50000, "white"];

// 2. 데이터 수정
cars[0]= "BMW";

// 3. 데이터 출력
console.log(cars[0]);  // BMW
console.log(cars[1]);  // 50000
console.log(cars[2]);  // white
```

**- Basic Methods**
| **Method**     | **Description**                                                                                    |
|----------------|----------------------------------------------------------------------------------------------------|
| length         | 배열길이                                                                                            |
| toString()     | 배열 자료형을 String 자료형으로 변환                                                                   |
| at()           | 특정 위치의 데이터 갖고오기                                                                            |
| join()         | 모든 배열의 요소를 String 로 변환하는 것(toString()과 유사)하나, join()의 경우 요소 사이에 구분자 추가 가능.  | 
| pop()          | 배열의 마지막 요소 꺼내기                                                                             |
| push()         | 배열의 마지막 요소 다음에 새로운 요소 추가하기                                                           |
| shift()        | 배열의 첫번째 요소를 삭제하고 한칸씩 앞으로 땡김                                                         |
| unshift()      | 배열의 첫번째 요소에 새로운 요소를 추가하고 한 칸씩 뒤로 보냄                                              |
| concat()       | 배열 2개를 합쳐서 새로운 배열 생성. 기존 배열은 변하지 않음                                               |
| splice()       | 배열의 특정 위치에 새로운 요소들을 추가/삭제할 때 사용.                                                   |
| slice()        | 배열의 특정 부분을 잘라서 새로운 배열로 리턴                                                             |

```javascript
const fruits = ["Banana", "Orange", "Apple", "Mango"];

// 1) length
console.log( fruits.length ); //4

// 2) toString()
console.log( fruits.toString() ); // Banana,Orange,Apple,Mango

// 3) at()
console.log( fruits.at(2) ); // Apple

// 4) join()
console.log( fruits.join(" * ") ); // Banana * Orange * Apple * Mango

// 5) pop()
console.log( fruits.pop() ); // Mango
console.log( fruits );       // Banana,Orange,Apple

// 6) push()
console.log( fruits.push("Kiwi") ); // 4
console.log( fruits );              // Banana,Orange,Apple,Kiwi

// 7) shift()
fruits.shift();
console.log( fruits ); // Orange,Apple,Kiwi

// 8) unshift()  
fruits.unshift("Lemon");
console.log( fruits ); // Lemon, Orange,Apple,Kiwi

// 9) concat()
const myGirls = ["Cecilie", "Lone"];
const myBoys = ["Emil", "Tobias", "Linus"];

const myChildren = myGirls.concat(myBoys);
console.log(myChildren); // Cecilie,Lone,Emil,Tobias,Linus

// 10) splice()
const color = ["Yellow", "Orange", "Red", "Green"];
//추가
color.splice(2, 0, "Black", "Blue"); // splice([어디를 잘라서 새로운 요소 넣을지], [몇개의 요소를 삭제하고 넣을지], [들어갈 요소])
console.log(color);                  // Yellow,Orange,Black,Blue,Red,Green
// 삭제
color.splice(0, 1);                  // splice([어디를 잘라서 새로운 요소 넣을지], [몇개의 요소를 삭제하고 넣을지], [들어갈 요소])
console.log(color);                  // Orange,Black,Blue,Red,Green

// 11) slice()
const fruits1 = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
const citrus1 = fruits1.slice(3);   // slice([어디서부터 자를지])
console.log(citrus1)                // Apple,Mango

const fruits2 = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
const citrus2 = fruits.slice(1, 3); // slice([어디서부터 자를지], [어디까지 자를지(해당 위치는 포함안됨)])
console.log(citrus2)                // Orange,Lemon
```
<br/>

**- Find and Search Methods**   
  **1) indexOf()**
  - 해당 검색어에 해당하는 첫번째 아이템을 찾고 그 위치를 리턴.
  ```javascript
  const fruits = ["Apple", "Orange", "Apple", "Mango"];
  console.log( fruits.indexOf("Apple") ); // 0
  ```
  <br/>

  **2) find()**
  - 조건에 만족하는 첫번째 아이템을 찾아서 리턴.
  ```javascript
  // 예제1
  const numbers = [4, 9, 16, 25, 29];
  let first = numbers.find((value, index) => {
    return value > 18;
  });
  console.log(first); // 25

  // 예제2
  const inventory = [
  { name: "apples", quantity: 2 },
  { name: "bananas", quantity: 0 },
  { name: "cherries", quantity: 5 },
  ];
  let foundCherries = inventory.find( (item, index)=>{ return item.name === "cherries" });
  console.log( foundCherries ); // { name: 'cherries', quantity: 5 }
  ```
  <br/>

  **4) findIndex()**
  -  특정 자료를 찾아서 몇번째인지 리턴
  ```javascript
  const inventory = [
  { name: "apples", quantity: 2 },
  { name: "bananas", quantity: 0 },
  { name: "cherries", quantity: 5 },
  ];

  let foundIndex = inventory.findIndex( (ele)=>{ return ele.name === "cherries" });

  console.log( foundIndex ); // 2
  ```

  <br/>

  **4) includes()**
  - 해당 검색어가 포함되어있는지 확인하고 true/false 리턴.
  ```javascript
  const fruits = ["Banana", "Orange", "Apple", "Mango"];
  console.log(fruits.includes("Mango")); // true
  ```
<br/>

**- Sort Methods**
  **1) sort()**
  - 배열을 알파벳 오름차순(default), 또는 원하는 방법(사용자 정의 함수)으로 정렬.
  ```javascript
  // 1) 알파벳 순으로 정렬
  const fruits = ["Banana", "Orange", "Apple", "Mango"];
  fruits.sort();
  console.log(fruits); // Apple,Banana,Mango,Orange

  // 2) 문자정렬
  let arr=["Kim", "Hyeon", "Ahn"];
  arr.sort( (a, b)=>{
    const nameA = a.toUpperCase();  
    const nameB = b.toUpperCase();

    if( nameA > nameB )  return 1;
    if( nameA < nameB )  return -1;

    return 0; // 반드시 리턴있어야 하므로
    
  });

  // 3) 숫자 정렬
  // 기본적으로 sort() 함수는 알파벳순 정렬이므로, 25와 100을 비교했을 때, 100이 더 앞에 위치. 1이 2보다 작으므로.
  // 따라서, 숫자 정렬을 위해서는 비교하는 함수를 구현
  // 'a - b : 음수'라면, a 다음 b
  // 'a - b : 0'이라면, 변화 없음
  // 'a - b : 양수'라면, b 다음 a
  const points = [40, 100, 1, 5, 25, 10];
  points.sort(function(a, b){return a - b}); // 1,5,10,25,40,100

  // 4) ascii 문자가 아닌 경우 비교
  let arr2 = ["réservé", "premier", "communiqué", "café", "adieu", "éclair"];
  arr2.sort( (a, b) => a.localeCompare(b) );
  console.log( err2 ); // ['adieu', 'café', 'communiqué', 'éclair', 'premier', 'réservé']
  ```

  **2) toSorted()**
  - 원본 배열을 손상하지 않고, 알파벳 오름차순(default), 또는 원하는 방법(사용자 정의 함수)으로 정렬
  ```javascript
  // 1) 알파벳 순으로 정렬
  const fruits = ["Jan", "Feb", "Mar", "Apr"];
  const sorted = months.toSorted();
  
  console.log(sorted); // Apr,Feb,Jan,Mar
  ```

  **3) reverse()**
  - 배열을 역순으로 정렬
  ```javascript
  const fruits = ["Banana", "Orange", "Apple", "Mango"];
  fruits.reverse();
  
  console.log(fruits); // Mango,Apple,Orange,Banana
  ```

**- Iteration Methods**   
  **1) foreach()**
  - 반복문처럼 사용. 배열의 자료 개수만큼 안의 코드 실행. 원본 데이터 변형.
  ```javascript
  /**
   * obj.forEach( ([element], [index], [array])=>{ [callback function] }) 
   */
  const numbers = [45, 4, 9, 16, 25];
  let txt = "";
  numbers.forEach( function myFunction(value, index, array) {
    console.log(value); // 45 4 9 16 25
  });
  ```

  **2) map()**
  - 반복문처럼 사용. 배열의 자료 개수만큼 안의 코드 실행. 원본 데이터 유지.
  ```javascript
  /**
   * obj.map( ([element], [index], [array])=>{ [callback function] }) 
   */
  var numbers = [7,3,5,2,40];
  var newNumbers = numbers.map(function(a){
    return a * 4;
  });
  ```

  > [!NOTE]
  > <details>
  > <summary> forEach() vs map() </summary>
  >   
  > |      특징      |   forEach()                                     |  map()                                                            |
  > | ---------------| ------------------------------------------------| -------------------------------------------------------------------- |
  > |    문법        | obj.forEach( ([element], [index], [array])=>{}) | obj.map( ([element], [index], [array])=>{})                 |
  > |    특징        | 반복문 (array/object 각 요소에 대해 작업을 수행)   | 반복문 (array/object 각 요소를 반환하여 새로운 객체를 생성)           |
  > |    공통점      | 원본 객체를 변경하지 않음                         | 원본 객체를 변경하지 않음                                           |
  > |    차이점      | 리턴값 없음(undefined)                           | 리턴값 있음                                                        | 
  >
  > ```JavaScript
  > let arr = [1, 2, 3];
  > // 1. 리턴값 비교
  > // 1-1) forEach()
  > let f = arr.forEach( (val) => val+1 )
  > console.log(f); // undefined
  >
  > // 1-2) map()
  > let m = arr.map( (val)=> val+1 )
  > console.log(m) //[2, 3, 4]
  >
  > 
  > // 2. 특정 객체의 값을 변경하고 싶을 때
  > // 2-1) forEach()
  > let newArr1 = [];
  > arr.forEach( (val)=>{ newArr1.push(val*2) })
  > console.log(newArr1) // [2, 4, 6]
  >
  > // 2-2) map()
  > let newArr2 = arr.map( (val)=> val*2 )
  > console.log(newArr2); // [2, 4, 6]
  > ```
  > </details>

  **3) filter()**
  - 필터 조건에 만족하는 요소로 새로운 배열을 리턴.
  ```javascript
  const numbers = [45, 4, 9, 16, 25];
  const over18 = numbers.filter( function myFunction(value, index, array) {
    return value > 18;
  });

  console.log(over18); // 45, 25
  ```

  **4) some()**
  - 각 요소들 중 하나라도 true 값을 리턴한다면, true
  ```javascript
  // Array.prototype.some( ([element], [index], [array]) => { return [조건] } )

  const array = [1, 2, 3, 4, 5];

  // Checks whether an element is even
  const even = (element) => element % 2 === 0;

  console.log(array.some(even)); // Expected output: true
  ```

  **5) every()**
  - 각 요소들 모두가 다 true 이여야만, true
  ```javascript
  const array = [1, 2, 3, 4, 5];

  // Checks whether an element is even
  const even = (element) => element % 2 === 0;

  console.log(array.some(even)); // Expected output: false
  ```
  <br/>

  **배열 중복제거**
  - Set이용
  ```javascript
  const dupArr    = [1, 2, 3, 1, 2];
  const set       = new Set(dupArr);
  const uniqueArr = [...set];

  console.log(uniqueArr) // 결과: [1, 2 ,3]
  ```


### 3) dates
- 날짜 객체
[JS Dates](https://www.w3schools.com/js/js_dates.asp)

```javascript
// 1. 날짜 객체 생성
const d1 = new Date();              // Wed Dec 18 2024 16:39:20 GMT+1100 (Australian Eastern Daylight Time) => 오늘날짜
const d2 = new Date("2024-12-18");  // Wed Dec 18 2024 11:00:00 GMT+1100 (Australian Eastern Daylight Time)
const d3 = new Date(2024, 12);      // Wed Jan 01 2025 00:00:00 GMT+1100 (Australian Eastern Daylight Time)
const d4 = new Date(year,month,day);
const d5 = new Date(year,month,day,hours);
const d6 = new Date(year,month,day,hours,minutes);
const d7 = new Date(year,month,day,hours,minutes,seconds);
const d8 = new Date(year,month,day,hours,minutes,seconds,ms);
const d9 = new Date(milliseconds)

```

### 4) maps
[Maps](https://www.w3schools.com/js/js_maps.asp)
[Maps Methods](https://www.w3schools.com/js/js_map_methods.asp)

### 5) sets
[Sets](https://www.w3schools.com/js/js_sets.asp)
[Sets Methods](https://www.w3schools.com/js/js_set_methods.asp)

### 6) intarrays

### 7) promises
[Promises](https://www.w3schools.com/js/js_promise.asp)

<br/>
<br/>

# 연산자 (JavaScript Operators)
| **연산자**    | **설명**                          |
|--------------|----------------------------------|
| `+`          | 덧셈                              |
| `-`          | 뺄셈                              |
| `*`          | 곱셈                              |
| `**`         | 지수 (ES2016)                     |
| `/`          | 나눗셈                            |
| `%`          | 나머지구하기                       |
| `++`         | 1씩 증가                          |
| `--`         | 1씩 감소                          |

<br/>
<br/>

# 정규식 (Regualr Expression)
- 문자열에서 특정 문자 조합을 찾기 위한 패턴.
![정규식 구조](https://github.com/Narae-H/study-javascript/blob/main/images/custom_reg_exp.png?raw=true)

## 사용방법
### 1) 문자 (알파벳/숫자/특수문자)
| 문자               | 설명                                            | 정규식 예시    | 매칭되는 문자열              |
|-------------------|-------------------------------------------------|--------------|----------------------------|
| `[abc]`, `[a-c]`  | `[]` 안에 주어진 문자나 문자 범위에 하나 이상 일치    | `abc[abc]`   | `abca`, `abcb`, `abcc`     |
| `[^abc]`, `[^a-c]`| `[]` 안에 주어진 문자나 문자 범위를 제외하고 일치     | `abc[^abc]`  | `abcd`, `abce`, `abc1`     |
| `.`               | 모든 문자. 줄바꿈은 제외                           | `bc.`        | `bca`, `bcd`, `bc1`, `b.`  |
| `\d`              | 숫자 (`[0-9]`와 동일)                            | `c\d`        | `c1`, `c2`, `c3`           |
| `\D`              | 숫자가 아닌 문자 (`[^0-9]`와 동일)                | `c\D`         | `ca`, `c.`, `c*`           |
| `\w`              | 알파벳이나 숫자 (`[A-Za-z0-9_]`와 동일)           | `a\w`         | `aa`, `a1`, `a_`           |
| `\W`              | 알파벳이나 숫자가 아닌 문자 (`[^A-Za-z0-9_]`와 동일)| `a\W`        | `a)`, `a$`, `a?`            |
| `\s`              | 공백 문자 (스페이스, 탭, 줄 바꿈 등)               | `a\s`         | `a `                        |
| `\S`              | 공백 문자가 아닌 문자                             | `a\S`        | `aa`                        |
| `\t`              | 수평 탭 문자                                     | `T\tab`      | `T  ab`                     |
| `x\|y`            | `x` 또는 `y` 중 하나와 일치                       | `a\|b`       | `a`, `b`                    |
  - 한글 문자 범위: [ㄱ-ㅎ가-힣ㅏ-ㅣ] 

### 2) Assertions
| 문자              | 설명                                                   | 예시           | 매칭되는 문자열                |
|------------------|-------------------------------------------------------|----------------|------------------------------|
| `^`              | 문자열의 시작 또는 여러줄인 경우는 첫 줄의 시작              | `^abc.*`       | `abc`, `abcd`, `abc1#!`      |
| `$`              | 문자열의 끝 또는 여러줄인 경우 가장 마지막 줄의 끝           | `.*xyz$`       | `xyz`, `wxyz`, `abcdxyz`     |
| `\b`             | 단어 경계 <sup>1)</sup>가 일치(앞, 뒤, 또는 앞뒤에 사용가능)| `My.*\bpie`    | `My apple pie`               |
| `\B`             | 단어 경계가 아닌경우 일치                                 | `c.*\Bcat`     | `copycat`                    |
| `x(?=y)`         | 긍정적 전방탐색<sup>2)</sup>: "x" 뒤에 "y"가 위치할 때     | `[0-9](?=kg)`  | `52kg 75kg 100lbs` 중 `2`만 매칭    |
| `x(?!y)`         | 부정적 전방탐색<sup>2)</sup>: "x" 뒤에 "y" 가 오지 않을 때 | `[0-9](?!kg)`  | `52kg 10lbs` 중 `5`만 매칭          |
| `(?<=y)x`        | 긍정적 후방탐색<sup>2)</sup>: "x" 앞에 "y"가 위치         | `(?<=a)b`      | `abc ab ac b` 중  첫번째 `b` 만 매칭 |
| `(?<!y)x`        | 부정적 후방탐색<sup>2)</sup>: "x" 앞에 "y"가 오지 않을 때  | `(?<!a)b`      | `abc ab ac b` 중  마지막 `b` 만 매칭 |

  > <details> 
  > <summary>1) 단어 경계란?</summary>
  >
  > 단어 경계: 다른 종류의 문자를 만나는 곳이나 단어가 아닌 문자를 만나는 곳
  > - 단어 문자: [a-zA-Z0-9_] (알파벳, 숫자, 밑줄)   
  > - 단어 문자가 아닌경우: 공백, 구두점, 특수문자(예: !, @), 문자열의 시작(^), 문자열의 끝($)   
  >
  > 단어의 경계를 `|`로 표시한다면?    
  > ex 1) hello world! => `|`hello`|` `|`world`|`!`|`
  > ex 2) 123abc! def456 => `|`123`|`abc`|`!`|` `|`def`|`456`|`
  >
  > ```javascript
  > // 자바스크립트 정규식 테스트
  > const text = "hello world!";
  >
  > // 1) 단어경계(\b)가 앞 뒤로 있는 경우
  > console.log(text.match(/\bworld\b/)); // 매칭됨: ["world"]
  > console.log(text.match(/\bwor\b/));   // 매칭되지 않음
  > console.log(text.match(/\bhello\b/)); // 매칭됨: ["hello"]
  >
  > // 2) 단어경계가 앞에만 있는 경우
  > console.log(text.match(/\bworld/)); // 매칭됨: ["world"]
  > console.log(text.match(/\bwor/));   // 매칭됨: ["wor"]
  > console.log(text.match(/\bhello/)); // 매칭됨: ["hello"]
  >
  > // 3) 단어경계가 뒤에만 있는 경우
  > console.log(text.match(/world\b/)); // 매칭됨: ["world"]
  > console.log(text.match(/wor\b/));   // 매칭되지 않음
  > console.log(text.match(/hello\b/)); // 매칭됨: ["hello"]
  > ```
  > </details>

  > <details> 
  > <summary>2) 긍정적/부정적 전방탐색, 긍정적/부정적 후방탐색 </summary>
  > 매칭된 결과는 x만 포함하고 b는 결과에 포함 안함
  > 매칭되는 첫번째 결과만을 리턴
  >
  > ```javascript
  > // 자바스크립트 정규식 테스트
  > const text1 = "52kg 73lbs 108kg";
  > // 1) 긍정적 전방탐색 (Positive lookahead)
  > console.log(text1.match(/[0-9](?=kg)/)); // 결과: 2 => 숫자이고, 그 다음으로 kg이 위치하므로
  > 
  > // 2) 부정적 전방탐색 (Negative lookahead)
  > console.log(text1.match(/[0-9](?!kg)/)); // 결과: 5 => 숫자이고, 그 다음으로 kg이 위치하지 않으므로
  > 
  > const text2 = "abc ab ac b";
  > // 3) 긍정적 후방탐색 (Positive lookbehind): 모든 브라우저에서 서포트 하지는 않음
  > console.log(text1.match(/(?<=a)b/));    // 결과: b (abc의 b) => 'b' 이면서 앞에 'a'가 위치하므로
  > 
  > // 4) 부정적 후방탐색 (Negative lookbehind): 모든 브라우저에서 서포트 하지는 않음
  > console.log(text1.match(/(?<!a)b/));    // 결과: b (마지막 b) => 'b' 이면서 앞에 'a'가 위치하지 않으므로
  > 
  > ``` 
  > </details>

### 3) Quantifiers
| 문자            | 설명                                            | 예시           | 매칭되는 문자열                |
|----------------|-------------------------------------------------|----------------|-----------------------------|
| `x*`           | 앞의 문자 `x`를 0번 이상 매칭.                     | `a*`           | `a`, `aa`, `aaa`            |
| `x+`           | 앞의 문자 `x`를 1번 이상 매칭. `{1,}`과 동일.       | `a+`           | `a`, `aa`, `aaa`            |
| `x?`           | 앞의 문자 `x`를 0번 또는 1번 매칭.                 | `ab?`          | `a`, `ab`                   |
| `x{n}`         | 앞의 문자 `x`를 `n`번 매칭. (`n`은 양의 정수)       | `ab{5}c`       | `abbbbbc`                   |
| `x{n,}`        | 앞의 문자 `x`를 최소 `n`번 이상 매칭(`n`은 양의 정수)| `ab{2,}c`      | `abbc`, `abbbc`, `abbbbc`   |
| `x{n,m}`       | 앞의 항목 `x`를 최소 `n`번, 최대 `m`번 매칭(`n < m`)| `ab{2,3}c`     | `abbc`, `abbbc`             |

### 4) Flags
- 정규식의 마지막에 위치하여 정규식이 어떻게 작동할지를 결정
- 예시) /w3schools/`i`;   

| 문자        | 설명                                                   |
|------------|--------------------------------------------------------|
| `g`        | 전역 검색을 수행. 일치하는 모든 것 리턴 (**g**lobal match)  |
| `i`        | 대소문자를 구분하지 않고 검색 (case-**i**nsensitive)       |
| `m`        | 여러 줄 검색을 수행 (**m**ultiline matching)             |
| `d`        | 하위 문자열 매칭에 대한 인덱스를 생성                       |
| `s`        | `.`이 줄바꿈 문자도 매칭하도록 허용                        |


## JS에서 정규식 사용하려면?
### 1) search()
- 정규식과 매칭되는 부분을 찾고, 매칭 되는 부분의 `위치`(0부터 시작)를 리턴
```javascript
let text = "Visit W3Schools!";
console.log(text.search(/w3schools/i)); // 6
``` 

### 2) replace()
- 정규식과 매칭되는 부분을 찾고, 특정 문자열로 `변경`
```javascript
let text = "Visit Microsoft!";
console.log(text.replace(/microsoft/i, "W3Schools")); // Visit W3Schools!
``` 

### 3) test()
- 정규식과 매칭되는지 `true/false` 리턴
```Javascript
const pattern = /e/;
console.log(pattern.test("The best things in life are free!")); // true
```

### 4) exec()
- 정규식과 매칭되는게 있다면 해당 문자 `object` 형태로 리턴, 그게 아니라면 `empty(null) object` 리턴
```Javascript
const returnObj = /e/.exec("The best things in life are free!");

console.log( returnObj[0] );    // e
console.log( returnObj.index ); // 2
console.log( returnObj.input ); // The best things in life are free!
```

## 정규식 검사 사이트
- [https://regexr.com/](https://regexr.com/)

# Dataset 문법
- HTML 태그 안에 데이터 넣어 놓는 방법
```javascript
<div id="div-name" data-name="Hong"></div> 
<div id="div-id"   data-id="id1"></div> 

console.log(document.querySelector("#div-name").dataset.data.name); // 출력: Hong
console.log(document.querySelector("#div-id").dataset.data.id);     // 출력: id1
```
<br/>
<br/>

# HTML elements 생성
- HTML elements 생성: `document.createElement('p')`
- 생성된 HTML element를 특정 위치에 붙임: `document.querySelector('#test').appendChild(a)` 
- HTML elements 생성 + 특정 위치에 붙임: ` document.querySelector('#test').insertAdjacentHTML('beforeend', a);`
```javascript
// 1. Javascript 문법을 이용하여 특정 element를 생성하고 붙이기
var a = document.createElement('p');            // 1) 생성
a.innerHTML = '안녕';
document.querySelector('#test').appendChild(a); // 2) 붙이기

// 2. Javascript 문법을 이용하여 특정 elelement 생성과 붙이는걸 동시에
var b = '<p>안녕</p>';
document.querySelector('#test').insertAdjacentHTML('beforeend', b); // 생성 + 붙이기
```

# JavaScript: Sync / async 
- JavaScript는 일반적으로 synchronous(동기) 처리 => 윗부분부터 순서대로 코드가 실행
- 하지만, 일부 함수들(시간이 오래걸리는애들)은 asynchronous(비동기)로 처리. => 순차적으로 실행되지 않고 완료되면 실행 ex) ajax(), setTimeout()
  <br/>
  <br/>
  
# 서버에 데이터 요청: Ajax
**AJAX (Asynchronous JavaScript and XML)**는 웹 페이지를 새로고침하지 않고 서버와 `데이터를 비동기적으로 주고받을 수 있는 기술` (특정 언어가 아님)

## 주요특징
- 전체 페이지를 `새로고침 하지 않고` 필요한 **데이터**만 주고 받음(HTML 페이지를 받는게 아님)
- 전통적인 링크 방식과 달리 중복된 HTML, CSS, JS 파일을 매번 다운로드 하지 않아도 되므로 `속도가 빠름`.
- `JSON, XML, HTML, 텍스트`(array, object는 안됨) 등 다양한 형식의 데이터를 서버에서 받아 처리할 수 있음
- JavaScript, HTML, CSS와 함께 사용되며, 서버는 어떤 언어로든 구현 가능
- 검색 엔진 최적화(SEO)에 불리할 수 있음
- 브라우저의 보안 정책(CORS)에 영향을 받음

## 동작 방식
- 클라이언트는 Ajax 방식으로 요청을하고 서버로부터 HTML 페이지가 아닌, **JSON, HTML, 텍스트** 등의 데이터를 직접적으로 응답받기를 기대함.
  - 일반 요청(서버사이드랜더링): 서버에서 html을 만들어서 클라이언트에게 보냄. 새로고침O <br/>
  <img src="https://github.com/Narae-H/study-javascript/blob/main/images/%EC%A0%84%ED%86%B5%EC%A0%81%EC%9D%B8%20%ED%86%B5%EC%8B%A0%EB%B0%A9%EC%8B%9D.png?raw=true" width="500px" alt="전통적인 통식방법"><br/>

  - Ajax 요청(클라이언트사이드 랜더링): 서버에서는 데이터만 보내주고 클라이언트에서 html만듬. 새로고침X          
  <img src="https://github.com/Narae-H/study-javascript/blob/main/images/ajax%ED%86%B5%EC%8B%A0%EB%B0%A9%EC%8B%9D.png?raw=true" width="500px" alt="Ajax 통식방법"><br/>
    
## 사용법
### 서버로 요청(Request) 방법
- fetch( "요청 URL", {추가데이터} ).then( 응답 ).then( 클라이언트에 보낼것들 처리 )
```js
  fetch("요청 URL~~", {
    method : 'HTTP Method',
    headers : { 'Content-Type' : 'application/json' },
    body : JSON.stringify({ "key" : "value"})
  }).then( (res) => {
    if( res.status == 200 ) {
      return res => res.json(); // 응답이 JSON 데이터인경우
      // return res => res.data(); // 응답이 일반 텍스트인경우
    } else {
      console.log("서버에서 에러남");
    }
  })    
  .then( (res) => {
    console.log("성공 시, 실행할 코드 여기 작성");
  })
  .catch( (error) => {
    console.log('실패 시, 실행할 코드 여기 작성');
  });
```
<br/>

- **요청 주의사항**
  - AJAX 요청을 서버에서 처리할 때는 `res.redirect(), res.render()를 사용하면 안됨`. 
  - 해당 메소드는 Ajax가 요청했을 때 클라이언트가 응답받기를 기대하는 형식(JSON 또는 텍스트)이 아님.
  
  **res.redirect()사용 시 문제**
  - res.redirect()는 서버가 클라이언트를 다른 URL로 리디렉션하도록 지시.
  - 브라우저는 Ajax 요청에서 리디렉션 응답(302 Found)을 따로 처리하지 않음.
  - Ajax 요청으로 리디렉션하면 요청을 보낸 페이지가 아닌 클라이언트 내부 스크립트로 응답이 전달되기 때문에, 브라우저는 새 페이지로 이동하지 않음.
  - `클라이언트는 리디렉션된 URL의 응답을 데이터로 처리하려고 시도`하지만, 이는 의도와 맞지 않을 가능성이 큼.
  
  **res.render()사용 시 문제**
  - res.render()는 서버가 템플릿 엔진(EJS, Pug 등)을 사용해 HTML 페이지를 렌더링하고 이를 클라이언트에 전달(JSON 또는 텍스트가 아님)
  - 클라이언트는 응답으로 전달된 HTML 데이터를 JSON이나 텍스트로 처리하려고 시도하지만, 원치않던 응답이라 오류를 유발하거나 예상치 못한 결과를 초래

### 클라이언트에게 올바른 응답(Response) 방법
**방법 1. JSON 데이터**

```js
  app.post('/example', (req, res) => {
      const data = { message: "Success", result: true };
      res.json(data); // JSON 응답
});
```
<br/>

**방법 2. 텍스트 데이터: 일반 텍스트**   

```js
app.get('/example', (req, res) => {
    res.send('Hello, world!'); // 텍스트 응답
});
```
<br/>

**방법 3. 텍스트 데이터: HTML 일부 (필요한 경우)**   

```js
app.get('/example', (req, res) => {
    res.send('<div>Some HTML content</div>'); // HTML 일부
});
```
<br/>

**방법 4. 텍스트 데이터: 리다렉트 주소 (필요한 경우)**   

```js
app.post('/example', (req, res) => {
    res.json({ redirect: '/new-url' }); // 클라이언트에게 리디렉션 주소 전달 -> 클라이언트에서 리디렉션 수행
});
```

## Ajax 라이브러리
- axios: fetch()문법보다 좀 더 간결하게 Ajax 사용 가능.

<br/>
<br/>

# DOM (Document Object Model)
- 자바스크립트가 HTML에 대한 정보들 (id, class, name, style, innerHTML 등)을 object 자료로 정리한걸 DOM이라고 부름.
- 브라우저는 HTML 문서를 위에서부터 읽으며 DOM 생성.
  ```html
  <script>
    document.getElementById('test').innerHTML = '안녕' // 에러: 아직 생성안된 HTML element에 접근하려고 하였으므로.
  </script>

  <p id="test">임시글자</p>
  ```
- 위 에러가 나지 않게 하려면? => 'HTML을 다 읽었는지 확인후에 실행하라'라는 코드 쓰면 됨.
  ```javascript
  // 1) Javascript 사용
  document.addEventListener('DOMContentLoaded', function() { 실행할 코드 }) 
  
  // 2) jQuery 사용
  $(document).ready(function(){ 실행할 코드 })
  
  ```

- `css/jss 파일`이 로드 됐는지 체크하기 법
  ```javascript
  // 1) Javascript 사용
  window.addEventListener('load', function(){
    //document 안의 이미지, js 파일 포함 전부 로드가 되었을 경우 실행할 코드
  })

  // 2) jQuery 사용
  $(window).on('load', function(){
    //document 안의 이미지, js 파일 포함 전부 로드가 되었을 경우 실행할 코드 
  });
  ```

# 브라우저 스토리지(LocalStorage/sessionStorage) 
- 브라우저에는 여러종류의 저장공간이 있음.

| **저장소 종류**                      | **설명**                                                            |
|------------------------------------|---------------------------------------------------------------------|
| [Local Storage](#local-storage)    | `key : value` 형태로 문자, 숫자 데이터를 저장할 수 있는 공간              |
| [Session Storage](#session-storage)| `key : value` 형태로 문자, 숫자 데이터를 저장하며, 브라우저 세션 동안만 유지 |
| Indexed DB                         | 크고 구조화된 데이터를 데이터베이스처럼 저장 가능하지만, 문법이 복잡          |
| Cookies                            | 유저의 로그인 정보와 같은 데이터를 저장하는 공간                           |
| Cache Storage                      | HTML, CSS, JavaScript, 이미지 파일 등을 저장해 두는 공간                 |


## Local Storage
- 브라우저 안에 있는 저장소

### 위치
Chrome 개발자 모드(F12) > Application 탭 > Local Storage

### 특징
1. key:value 형태로 저장가능   
2. 최대 5MB까지 문자/JSON만 저장가능 (숫자를 저장해도 문자로 변환해서 저장 됨)   
3. 유저가 캐시를 지우지 않는 한, 사이트 재접속해도 남아있음    
> [!NOTE] Local Storage는 재접속해도 남아있지만, Session Storage는 브라우저 끄면 날라감.

### 사용법
1. 일반 문자인 경우
```JavaScript
localStorage.setItem('age', '20') // 자료 저장
localStorage.getItem('age')       // 자료 꺼냄
localStorage.removeItem('age')    // 자료 삭제
```

2. array/object 인 경우   
local storage는 문자 또는 JSON만 저장 가능하므로, JSON 타입으로 변형필요
```JavaScript
let obj = {name : 'kim'}

// 넣을때: JSON.stringify() 이용해서 '객체 -> 문자'로 변경
localStorage.setItem('data', JSON.stringify(obj)); 

// 꺼낼때: JSON.parse() 이용해서 '문자 -> JSON'으로 변경
console.log( JSON.parse( localStorage.getItem('data') ) )
```

### 외부 라이브러리
- redux-persist
- Jotai
- Zustand

## Session Storage

<br/>
<br/>

# Rest parameter
- 파라미터가 몇 개 들어올지 미리 정의가 불가능한 경우 `...[파라미터명]`로 남아있는 파라미터 전부 다 배열 형태로 받을 수 있음
- rest parameter는 파라미터 제일 뒤에 위치해야 함.
```javascript
function 전부더하기(...a){
  let res = 0;
  a.foreach( (item) => {
    res += item;
  })
  console.log(`합 => ${res}`);
}

전부더하기(1,2,3,4,5)
```
<br/>
<br/>

# Spread operator
- array 혹은 object에서 괄호 벗기고 싶을 때 사용.
```javascript
let arr = [3,4,5];
let arr2 = [1,2, ...arr]
console.log(arr2); //1,2,3,4,5
```
<br/>
<br/>

# Destructuring
- 배열/객체의 속성을 해체하여, 그 값을 개별 변수에 담을 수 있게 하는 표현식 <br/>
- 자바스크립트에서 array, object 안에 있는 데이터를 빼서 변수를 만들고 싶을 때 사용. <br/>
- object destructuring 일땐 변수이름과 속성을 맞춰주는게 편리하고 array destructuring은 마음대로 작명 가능. <br/>

```javascript
// 1. object
let { student, age } = { student : true, age : 20 }
console.log( student ); // true
console.log( age );     // 20

// 2. array
// 1) 왼쪽과 오른쪽 일치
let [a, b] = ['안녕', 100]
console.log(a); // 안녕
console.log(b); // 100

// 2) 왼쪽과 오른쪽 개수 불일치
let [a, b] = ["1", "2", "3"];                 // a : 1 , b : 2
let [c, d, ...e] = ["1", "2", "3", "4", "5"]; // c : 1, d : 2, e : [3, 4, 5]
```
<br/>
<br/>

# Default Parameter Value(기본값 매개변수)
argument 없이 함수가 실행될 경우 undefined 대신 사용될 값을 할당.
```JavaScript
function fn1(name = "John Doe", age = 30) {
    console.log(`${name} is ${age} years old`);
}
fn1();
//John Doe is 30 years old
fn1("Peter", 15);
//Peter is 15 years old
```
<br/>
<br/>

# 객체지향 프로그래밍
- object 자료형으로 정보 저장할때, class 문법을 이용하면 비슷한 object를 쉽게 찍어내기 가능

## 템플릿을 이용한 객체(Object) 생성
### 1) function 사용
- 옛날 Javascript 문법은 class 문법 없어서 function 으로 만듬.
  ```javascript
  function car(name, year) {
    this.name = name; // this: 기계()로 부터 새롭게 생성되는 object(instance)
    this.year = year;
  }
  const myCar1 = new car("Ford", 2014);
  const myCar2 = new car("Audi", 2019);

  ```
### 2) class 사용 (ES6 이후 문법)
- class의 이름은 항상 대문자로.
- class 안에는 반드시 constructor()를 추가하여야 하며, 이는 새로운 object가 생성될때 자동으로 실행됨. 
- class는 constructor()외에 다른 methods도 사용 가능.
  ```javascript
    class Car {
      constructor(name, year) {
        this.name = name;
        this.year = year;
      }
    }
    const myCar1 = new Car("Ford", 2014); 
    const myCar2 = new Car("Audi", 2019);
  ```

## Prototype: 객체(Object)의 상속
- prototype이란 겉으로는 보이지 않지만 상속되어 몰래 숨어있는 `부모의 유전자`

### 객체의 특징
**1) 이미 존재하는 객체 생성자에는 새로운 속성 추가 못함.**
```javascript
function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;

  Person.nationality = "English"; // 불가능
}
```

**2) prototype chain**: 모든 JavaScript 객체는 부모의 속성이 상속 됨.
  ```javascript
  var arr = new Array(1, 2, 3);
  arr.sort(); 
  
  // sort()정의한 적 없는데 쓸 수 있는 이유는?
  // => 해당 객체의 부모(Array)가 sort()를 가지고 있어서 상속되었음.
  // => 부모의 부모, 부모의 부모의 부모, ... 전부 다 자식으로 상속 됨.  
  ```
  <sup>* [Inheritance and the prototype chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)</sup>

### prototype 활용
- 이미 존재하는 객체에 constructor()를 바꾸지 않고 새로운 속성 추가하고 싶을 때
- 같은 부모로 부터 생성된 모든 자식이 같은 속성을 갖고 싶을 때
  > <small>[!Note] 내가 생성한 객체의 prototype만 변경하자. JavaScript 기본 객체의 prototype변경하면 혼란을 야기할 수 있음</small>
  <br/>

  <sub>**예시1)** 새로운 값 추가</sub>
  ```javascript
  function Person(first, last, age, eyecolor) {
    this.firstName = first;
    this.lastName = last;
    this.age = age;
    this.eyeColor = eyecolor;
  }

  Person.prototype.nationality = "English";
  ```
  <sub>**예시2)** 새로운 methods 추가</sub>
  ```javascript
  function Person(first, last) {
    this.firstName = first;
    this.lastName = last;
  }

  Person.prototype.show = function() {
    console.log(this.firstName + " " + this.lastName)
  };
  ```

### JavaScript 기본 객체의 prototype
- 모든 JavaScript 객체는 부모로 부터 properties와 methods 상속 (최상위 객체는 `Object.prototype`)  
**ex1)** `Date` 객체는 부모의 모든 [prototypes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#instance_methods) 사용 가능.   
**ex2)** `Array` 객체는 부모의 모든 [prototypes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#instance_methods) 사용 가능.   
**ex3)** 내가 생성한 `Person` 객체는 부모의 모든 prototypes 사용 가능.

<br/>
<br/>

# 유용한 자바스크립트 라이브러리들
- [Chart.js](https://www.chartjs.org/docs/latest/): 웹페이지에서 차트 만들고 싶을 때
- [Animate On Scroll](https://michalsnik.github.io/aos/): 스크롤 내리면 요소가 서서히 등장하는 애니메이션 만들고 싶을 때
- [EmailJS](https://www.emailjs.com/docs/introduction/how-does-emailjs-work/): 자바스크립트만으로 이메일 전송
- [React](https://react.dev/): Single Page Application 만들 떄 사용 
- [Vue](https://vuejs.org/): Single Page Application 만들 떄 사용 

# 모던 웹 개발 시 알아야 할 배경 지식
## npm
- `라이브러리 설치/수정/삭제/버전 관리`를 쉽게 하기 위해 사용
- 작업하던 폴더에서 터미널 열어서 npm install 라이브러리명 이런거 입력하면 라이브러리 설치 끝.

## nodejs
- 구글이 만든 `자바스크립트 해석 엔진`
- 내가 짠 자바스크립트 코드를 컴퓨터 친화적인 코드로 변환해서 돌려주는 엔진으로 V8이라고 부름.
- V8이 너무 잘 만들어져 그걸 독립적인 실행프로그램으로 만들어서 배포하고 있는데 이름이 Node.js임.

## bundling tool
- npm으로 라이브러리 이거저거 설치해서 js 파일이 수천개씩 쌓였을 때, 쓸모없는 라이브러리 정리해주는 툴
- 예전에는 Webpack, parcel, snowpack 사용. 현재는 Vite 사용

## build
- build 작업(나의 소스코드를 분석해서 꼭 필요한 js파일과 코드만 남겨주는 작업)을 하면 결과물로 js파일 html 파일 이런걸 뱉어줌
- 서버에 배포하기 위해 필요함.

## SPA (Single Page Application)
- 자바스크립트로 html 변경하는 작업을 매우 쉽게 할 수 있도록 도와주는 React, Vue 라이브러리 많이 씀.
- 이런 라이브러리들을 쓰면 `Single page application`을 만들 수 있는데, 이게 바로 새로고침 없이 페이지 전환 부드럽게 한페이지에 모든 UI를 띄어주는 방법.

## state management
- React, Vue 같은 라이브러리 설치해서 쓰면 html 덩어리들을 재사용하고 싶을 때 컴포넌트라는걸 만들어서 사용.
- 근데 그 컴포넌트끼리 변수를 공유하는게 매우 어렵기 때문에 그걸 쉽게 도와주는 라이브러리(Redux toolkit, Zustand)를 또 설치해서 씀. 

## server side rendering
- `Client side rendering`: React, Vue로 html 덩어리들을 브라우저에서 마구 만들어내는걸
- `Server side rendering`: html을 서버에서 미리 전부 완성해서 보내주는 식

## typescript 
- 자바스크립트는 타입이 자유료운 언어라도 버그발생 가능성이 높음. 
- 따라서, 타입이 명시할 수 있는 typescript를 사용함. 타입스크립트로 코드짜로 build tool이 알아서 .js로 변환해줌.

