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

### :page_facing_up: 4.5. 삼항 연산자 추가하기

---

**삼항 연산자** (**ternary operator**)를 사용하면 템플릿 문자열 내에 로직을 쉽게 추가할 수 있다.

```javascript
const isDiscounted = false;

function getPrice(){
    console.log(isDiscounted ? "$10" : "$20");
}

getPrice();		// $20
```

- `?` 앞의 조건이 **true**이면 첫 번째 값이 반환되고, 그렇지 않으면 `:` 뒤에 있는 값이 반환된다.

<br>

```javascript
// name, age와 함께 artist를 생성

const artist = {
    name : "BTS",
    age : 28,
};

// artist 객체에 song프로퍼티가 있을 때만 문장에 추가하고,
// 없으면 아무것도 반환하지 않음

const text = `
	<div>
		<p> ${artist.name} is ${artist.age} years old ${artist.song ? `and wrote the song ${artist.song}` : ''}
		</p>
	</div>
`;
console.log(text);
/*
	<div>
		<p> BTS is 28 years old 
		</p>
	</div>
*/

const artist = {
    name : "Black Pink",
    age : 25,
    song : 'Butter',
};

console.log(text);

/*
	<div>
		<p> Black Pink is 25 years old and wrote the song Butter
		</p>
	</div>
*/
```

<br>

<br>

### :page_facing_up: 4.6. 템플릿 리터럴에 함수 전달하기

---

필요하면 템플릿 리터럴 내에 함수를 전달할 수도 있다.

- `${groceryList(groceries.others)}` 부분

```javascript
const groceries = {
    meat : "pork chop",
    veggie : "salad",
    fruit : "apple",
    others : ['mushrooms', 'instant noodles', 'instant soup'],
};

// groceries 의 각 값에 대해 map()을 수행하는 함수
function groceryList(others){
    return `
		<p>
		  ${others.map(other => `<span> ${other}</span>`).join('\n')}
		</p>
	`;
}

// p 태그 내 모든 groceries 를 출력. 마지막은 **others** 배열의 모든 원소를 포함
const markup = `
    <div>
        <p>${groceries.meat}</p>
    	<p>${groceries.veggie}</P>
		<p>${groceries.fruit}</P>
    	<p>${groceryList(groceries.others)}</p>
    </div>
`;

console.log(markup);
/*
    <div>
        <p>pork chop</p>
    	<p>salad</P>
		<p>apple</P>
    	<p>
		<p>
		  <span> mushrooms</span>
		  <span> instant noodles</span>
		  <span> instant soup</span>
		</p>
	</p>
    </div>
*/
```

- 마지막 `p`태그에서 함수 `groceryList`를 호출하여 다른 모든 `others`를 인수로 전달했다.
- 함수 내에서 `p`태그를 반환하고 `map`을 사용하여 `groceries`의 각 원소에 대해 반복하여 각 원소를 담은 `<span>` 태그 배열을 반환한다.
- 다음으로, `.join('\n')`을 사용하여 각 `<span>` 뒤에 새 행을 추가한다.

<br>

<br>

### :page_facing_up: 4.7. 태그된 템플릿 리터럴

---

함수를 **태그**(tag)하여 템플릿 리터럴을 실행하면 템플릿 내부에 있는 모든 항목이 태그된 함수의 인수로 제공된다.

- 작동 방식
  - 함수 이름을 가져다 실행할 템플릿 앞에 쓰면 된다.

```javascript
let person = "OHTAEKOWN";
let age = 25;

function myTag(strings, personName, personAge){
    // strings : ["That ", " is a ", "!"]
    let str = strings[1];	// " is a"
    let ageStr;
    
    personAge > 50 ? ageStr = "grandpa" : ageStr = "youngster";
    
    return personName + str + ageStr;
}

let sentence = myTag`That ${person} is a ${age}!`;
console.log(sentence);		// OHTAEKWON is a youngster
```

이 코드의 함수는 `age` 변수의 값을 받아서 **삼항 연산자**를 사용하여 출력할 할목을 결정한다.
함수에서 첫 번째 인수 `strings`는 `let sentence`문의 전체 문자열 중 템플릿 리터럴 변수를 제외한 문자열들이 담긴 배열로 설정되고, 템플릿 리터럴 변수들이 나머지 인수가 된다.

`strings` 배열의 각 원소는 템플릿 리터럴에 포함된 변수들을 구분자로 삼아 문자열을 나눈 결과와 같다.
이 예에서 문자열은 `That, ${person}, is a , ${age}, !` 다섯 부분으로 나뉘므로 여기서 변수를 제외한 `["That ", " is a ", "!"]`가 **strings**가 된다.

배열 표기법을 사용하여 다음과 같이 중간에 있는 문자열에 접근할 수 있다. 

```javascript
let str = strings[1];	// is a
```


