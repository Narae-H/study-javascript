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

## var vs let vs const   
| **Type** | **범위**             | **재선언**     | **재할당**    | **`this`에 바인딩** |
|----------|----------------------|---------------|--------------|-------------------|
| `var`    | function-scoped      | Yes           | Yes          |  Yes              |
| `let`    | {Block-scoped}       | No            | Yes          |  No               |
| `const`  | {Block-scoped}       | No            | No           |  No               |   

<br/>
<br/>

# 함수선언
## 문법
```Javascript
function functionName (parameter1, parameter2, ...) {
  // 실행 할 코드
}
```
<br/>
<br/>

# 이벤트
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
| **그룹**          | **설명**                                                                                                                             | **이벤트 종류**                                                                              |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| **Drag and Drop**  | Events related to the Drag and Drop API. Drag events fired on `Document`.                                                          | drag, dragover, dragstart, drop.                                                           |
| **Focus**          | Events related to elements gaining or losing focus. Events fired on `Element`, `Window`.                                           | blur, focus, focusout                                                                      |
| **Form**           | Events related to forms being constructed, reset, or submitted. Events fired on `HTMLFormElement`.                                 | submit                                                                                     |
| **Inputs**         | Events related to HTML input elements (`<input>`, `<select>`, `<textarea>`). Events fired on `HTMLElement`, `HTMLInputElement`.    | cancel, change, select, input                                                              |
| **Keyboard**       | Events related to keyboard interactions. Notifies when keys are pressed, released, or moved. Events fired on `Document`, `Element`.| keydown, keypress, keyup                                                                   |
| **Mouse**          | Events related to mouse interactions. (e.g., clicks, double clicks, movement, etc.). Mouse events fired on `Element`.              | click, dbclick, mousedown, mouseenter, mouseleave, mousemove, mouseout, mouseover, mouseup |
| **Timing**         | Events related to time. Events fired on `Window`.                                                                                  | setTimeout, clearTimeout, setInterval, clearInterval                                       |

- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/Events)
- [W3Schools](https://www.w3schools.com/jsref/dom_obj_event.asp)
<br/>
<br/>

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
## Overview
### 1. 원시형 (Primitive types)    
  | **Type**                    | **`typeof` Return Value** | **Object Wrapper** |
  |-----------------------------|---------------------------|---------------------|
  | [**Null**](#null)           | `object`                  | N/A                 |
  | [**Undefined**](#undefined) | `undefined`               | N/A                 |
  | [**Boolean**](#boolean)     | `boolean`                 | `Boolean`           |
  | [**Number**](#number)       | `number`                  | `Number`            |
  | [**BigInt**](#bigint)       | `bigint`                  | `BigInt`            |
  | [**String**](#string)       | `string`                  | `String`            |
  | [**Symbol**](#symbol)       | `symbol`                  | `Symbol`            |

> [!Note] null을 제외한 모든 기본 타입은 `typeof` 연산자로 테스트 가능. `typeof null`은 "object"를 반환하므로 `=== null`을 사용하여 테스트   

### 2. 객체 타입 (Object types)  
  | **Type**                    | **`typeof` Return Value** |
  |-----------------------------|---------------------------|
  | [**Objects**](#objects)     | `objects`                 |
  | [**arrays**](#arrays)       | `arrays`                  |
  | [**dates**](#dates)         | `dates`                   |
  | [**maps**](#maps)           | `maps`                    |
  | [**sets**](#sets)           | `sets`                    |
  | [**intarrays**](#intarrays) | `intarrays`               |
  | [**promises**](#promises)   | `promises`                |

## Null
- Null 타입은 null이라는 오직 하나의 값만 가질 수 있음
```Javascript 
let nulltype = null;
```

## Undefined
- Undefined 타입은 `undefined`이라는 오직 하나의 값만 가질 수 있음
- `Undefined`는 값이 없음을 의미하고 `null`은 객체가 없음을 의미   
  ex) 존재하지 않는 객체 속성에 접근, 초기화가 없는 변수 선언

## Boolean
### 사용법
- `true / false` 두 가지 값을 가짐
- 일반적으로 `삼항연산자`, `if/else`, `while` 등을 포함한 조건부 연산에서 사용
```Javascript 
let x = true;
let y = false;
```

## Number
### 사용법
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

### Methods
| **Method**                                   | **설명**    |
|----------------------------------------------|------------|
| [number].toString()                          | 문자로 변환  |
| [number].parseInt()                          | 정수로 변환  |


## BigInt
- BigInt는 Number의 범위를 넘어서는 큰 정수도 안전하게 저장하고 연산할 수 있음.
- 범위가 굉장히 크므로 일반적으로는 Number 사용

## string
### 사용법
```Javascript 
let color    = "Yellow";                     // Double quotes
let lastName = 'Johnson';                    // Single quotes
let answer1  = "It's alright";               // Use quotes inside a string
let text     = `He's often called "Johnny"`; // Template Strings
```

### Escape Characters
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

- string에서 따옴표 또는 쌍따옴표를 쓰고 싶을 경우 `escape characters` 사용 가능.     
  ```Javascript
  let text1 = "We are the so-called \"Vikings\" from the north."; // We are the so-called "Vikings" from the north.
  let text2 = 'It\'s alright.';                                   // It's alright.
  let text3 = "The character \\ is called backslash.";            // The character \ is called backslash.
  ```

### Methods
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

### Templates
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

## Symbol
- 유하고 변경 불가능한 원시(Primitive) 값

## object
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

## arrays

## dates

## maps

## sets

## intarrays

## promises

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

## 사용방법
### Modifiers
- 정규식의 옵션이므로 선택적으로 사용 가능. 하나이상의 modifiers 동시에 사용 가능.   
```Javascript
let pattern = /w3schools/i;
```

| **Modifier** | **설명**                                           |
|--------------|---------------------------------------------------|
| `/g`         | 일치하는 모든 것 검색 (**g**lobal match)             |
| `/i`         | 대소문자 구별 없음 (case-**i**nsensitive)            |
| `/m`         | 문자열의 행바 바뀌더라도 검색 (**m**ultiline matching) |


### Brackets
-  찾는 문자열의 범위 지정. 괄호안의 문자들 중 하나.

| **Bracket** | **설명**                                                 |
|-------------|---------------------------------------------------------|
| `[abc]`     | brackets 안의 문자 중 하나라도 있는지 확인                   |
| `[^abc]`    | brackets 안의 문자 중 단 하나도 포함되지 않는지 확인          |
| `[0-9]`     | brackets 범위 안의 숫자 중 하나라도 있는지 확인              |
| `[^0-9]`    | brackets 범위 안의 숫자 중 단 하나도 포함되지 않는지 확인      |
| `(x\|y)`    | x나 y 둘중에 하나라도 만족하는게 있는지 확인                  |

### 메타문자 (Metacharacters)
| **Character** | **설명**                                                                                     |
|---------------|-----------------------------------------------------------------------------------------------------|
| `.`           | 모든 문자열 (줄바꿈 X)                                         |
| `\w`          | 문자 (영어 알파벳, 숫자, 언더스코어(_))                                                                               |
| `\W`          | \w 외의 모든 문자                                                                           |
| `\d`          | Find a digit                                                                                       |
| `\D`          | Find a non-digit character                                                                          |
| `\s`          | 공백                                                                         |
| `\S`          | 공백이 아닌 문자                                                                     |
| `\b`          | 단어의 처음 시작 또는 끝이 매칭 (e.g., `\bHI` HI로 시작, `HI\b` HI로 끝)                |
| `\B`          | Find a match, but not at the beginning/end of a word                                               |
| `\0`          | NULL 문자                                                                               |
| `\n`          | Find a new line character                                                                           |
| `\f`          | Find a form feed character                                                                          |
| `\r`          | Find a carriage return character                                                                    |
| `\t`          | Find a tab character                                                                                |
| `\v`          | Find a vertical tab character                                                                       |
| `\xxx`        | Find the character specified by an octal number `xxx`                                               |
| `\xdd`        | Find the character specified by a hexadecimal number `dd`                                           |
| `\udddd`      | Find the Unicode character specified by a hexadecimal number `dddd`                                 |

https://www.w3schools.com/js/js_regexp.asp
https://www.w3schools.com/jsref/jsref_obj_regexp.asp
https://velog.io/@purplew/Javascript-%EC%A0%95%EA%B7%9C%ED%91%9C%ED%98%84%EC%8B%9D


### 자바스크립트에서의 사용법
- [정규식].test([문자열])
```Javascript
/[a-d]/.test('aefg');      // a-d 까지의 아무 문자 하나가 'aefg'에 있는가?             => true
/[가-다]/.test('다라마바');  // 가-다 까지의 아무 문자 하나가 '다라마바'에 포함되어 있는가? => true
/\S/.test('abcde')         // 특수문자 포함 아무 문자 하나가 'abcde'에 포함되어 있는가?  => true  
```

## 정규식 검사 사이트
- [https://regexr.com/](https://regexr.com/)