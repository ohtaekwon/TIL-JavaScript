#  CHAPTER 05

###  :pencil: ***문자열 메서드***

<br>

### :page_facing_up: 5.1. 기본적인 문자열 메서드

---

자바스크립트에는 문자열에 사용할 수 있는 많은 메서드가 있다. 

<br>

#### 1) indexOf()

문자열에서 지정된 값이 처음 나타나는 위치를 반환한다. 

```javascript
const str = "this is a short sentence";
str.indexOf("short");		// 10
```

<br>

#### 2) slice()

문자열의 지정된 부분을 새 문자열로 반환한다. 

```javascript
const str ="pizza, orange, cereals";
str.slice(0,5);	// pizza
```

<br>

#### 3) toUpperCase()

문자열 내의 모든 문자를 대문자로 바꾼다.

```javascript
const str = "i ate an apple";
str.toUpperCase();	// 'I ATE AN APPLE'
```

<br>

#### 4) toLowerCase()

문자열의 모든 문자를 소문자로 바꾼다.

```javascript
const str = "I ATE AN APPLE";
str.toLowerCase();	// 'i ate an apple'
```

<br>

이것들 이외에도 많은 메서드들이 있다. 메서드 등에 대한 자세한 설명은 **MDN** 문서에서 확인할 수 있다.

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String

<br>

<br>

### :page_facing_up: 5.2. 새로운 문자열 메서드

---

`ES6`는 `4가지` 새로운 문자열 메서드를 도입헀다.

- `startsWith()`
- `endsWith()`
- `includes()`
- `repeat()`

<br>

#### 1) startsWith()

이 메서드는 매개변수로 받은 값으로 문자열이 시작하는지 확인한다.

```javascript
const code = "ABCDEFG";

code.startsWith("ABB");			// false
code.startsWith("abc");			// false (startsWith는 대소문자를 구별한다.)
code.startsWith('ABC');			// true
```

매개변수를 추가로 전달하면 메서드가 검사를 시작하는 시작점을 지정할 수도 있다.

```javascript
const code ="ABCDEFGHI";

code.startsWith("DEF", 3);		// true (3개 문자를 지나 검사를 시작한다.)
code.startsWith("EFG", 4); 		// true (4개 문자를 지나 검사를 시작한다.)
```

<br>

#### 2) endsWith()

이 메서드는 `startsWith()`과 유사하게 문자열이 우리가 전달한 값으로 끝나는지 확인한다.

```javascript
const code = "ABCDEF";

code.endsWith("DDD");			// false
code.endsWith("def");			// false (endsWith는 대소문자를 구별한다.)
code.endsWith("DEF");			// true
```

추가 매개변수로 문자열의 얼마만큼으로 확인할지 길이를 전달할 수 있다.

```javascript
const code = "ABCDEFGHI";

code.endsWith("EF", 6);			// true (첫 6개 문자인 ABCDEF만을 고려하며, ABCDEF는 EF로 끝나므로 true가 된다.)

code.endsWith("CD",4);			// true

code.endsWith("GH",5);			// false
```

<br>

#### 3) includes()

이 메서드는 전달한 값이 문자열에 포함되어 있는지 확인하는 메서드이다.

```javascript
const code = "ABCDEF";

code.includes("ABB");			// false
code.includes("abc");			// false (includes는 대소문자를 포함한다.)
code.includes("CDE");			// true
```

<br>

#### 4) repeat()

이 메서드는 문자열을 반복하며 횟수를 인수로 받는다.

```javascript
let hello = "Hi ";

console.log(hello.repeat(10));		// Hi Hi Hi Hi Hi Hi Hi Hi Hi Hi 
```







