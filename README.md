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
<br/>
<br/>

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

### 2) arrays
- 여러가지 자료를 한곳에 저장하고 싶을 때

```javascript
```

### 3) dates

### 4) maps

### 5) sets

### 6) intarrays

### 7) promises

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
![정규식 구조](https://raw.githubusercontent.com/Narae-H/study-javascript/refs/heads/main/custom_reg_exp.png)

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

console.log(document.querySelector("#div-name").dataset.data.name);  // 출력: Hong
console.log(document.querySelector("#div-id").dataset.data.id);    // 출력: id1
```

# 유용한 자바스크립트 라이브러리들
- [Chart.js](https://www.chartjs.org/docs/latest/): 웹페이지에서 차트 만들고 싶을 때
- [Animate On Scroll](https://michalsnik.github.io/aos/): 스크롤 내리면 요소가 서서히 등장하는 애니메이션 만들고 싶을 때
- [EmailJS](https://www.emailjs.com/docs/introduction/how-does-emailjs-work/): 자바스크립트만으로 이메일 전송
- [React](https://react.dev/): Single Page Application 만들 떄 사용 
- [Vue](https://vuejs.org/): Single Page Application 만들 떄 사용 