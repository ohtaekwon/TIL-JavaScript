#  CHAPTER 04

###  :pencil: ***템플릿 리터럴***

<br>

### :page_facing_up: 4.1. 문자열 삽입

---

`ES5`에서 문자열을 삽입하기 위한 코드

```javascript
var name = "OHTAEKWON";
var greeting = "Hello my name is " + name;

console.log(greeting);	// Hello my name is OHTAEKWON
```

<br>

`ES6`에서는 **백틱(backtick)** (**`**)을 사용하여 코드를 쉽게 작성한다.

```javascript
let name = "OHTAEKWON";
const greeting = `Hello my name is ${name}`;

console.log(greeting);		// Hello my name is OHTAEKWON
```

<br>

<br>

### :page_facing_up: 4.2. 표현식 삽입

---

표현식을 삽입하려면 `ES5`에서는 다음과 같이 작성했다.

```javascript
var a = 1;
var b = 10;
console.log('1 * 10 is ' + (a*b));	
// 1 * 10 is 10
```

<br>

`ES6`에서는 **백틱**(`)을 사용하여 코드를 작성한다.

```javascript
var a = 1;
var b = 10;
console.log(`1 * 10 is ${a * b}`);	
// 1 * 10 is 10
```

<br>

<br>
