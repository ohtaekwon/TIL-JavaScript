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

### :page_facing_up: 4.3. 여러 줄 문자열 생성

---

`ES5`에서 `HTML` 프래그먼트 등에 사용할 여러 줄로 이뤄진 문자열을 다음과 같이 구현했다.

```javascript
// 각 행마다 백슬래시를 삽입해야 함
var text = "hello, \
my name is OHTAEKOWN \
how are you? \";
```

<br>

`ES6`에서는 전체를 **백틱**으로 감싸기만 하면 된다. 

- 더이상 백슬래시를 쓰지 않아도 됨

```javascript
const content = `hello, 
my name is OHTAEKWON
how are you? `;

console.log(content);
/*
hello, 
my name is OHTAEKWON
how are you? 
*/
```

<br>

<br>

### :page_facing_up: 4.4. 중첩 템플릿

---

템플릿 안에 테플릿을 중첩

```javascript
const people = [{
    name : 'OHTAEKWON',
    age : 30,
},{
    name : 'BTS',
    age : 28,
},{
    name : 'Black Pink',
    age : 27,
}];

const markup = `
<ul>
	${people.map(person => `<li> ${person.name}</li>`)}
</ul>
`;

console.log(markup);

/*
<ul>
	<li> OHTAEKWON</li>,<li> BTS</li>,<li> Black Pink</li>
</ul>
*/
```

여기서는 **map** 함수를 사용하여 `people`의 각 원소에 대해 반복 동작을 수행하고 `people` 내에 있는 `name`을 담아 `li` 태그를 표시했다.

<br>

<br>
