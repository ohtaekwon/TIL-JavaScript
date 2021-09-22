#  CHAPTER 10

###  :pencil: ***객체 리터럴의 업그레이드***

<br>

### :page_facing_up: 10.1. 변수를 키와 값으로 하는 객체 만들기

---

```javascript
const name = "TAEKWON";
const surname = "OHT";
const age = 30;
const nationality = "KOREA";
```

이 코드를 이용하여 **객체 리터럴**을 만들기 위해서는 일반적인 방법으로는 다음과 같이 한다.

```javascript
const person = {
    name : name,
    surname : surname,
    age : age,
    nationality : nationality,
};

console.log(person);	
// {name: 'TAEKWON', surname: 'OHT', age: 30, nationality: 'KOREA'}
```

<br>

`ES6`에서는 단수화할 수 있다.

```javascript
const person = {
    name,
    surname,
    age,
    nationality,
};
console.log(person);
// {name: 'TAEKWON', surname: 'OHT', age: 30, nationality: 'KOREA'}
```

변수들의 이름이 코드 내의 속성과 같이 동일하기 때문에 코드 내에서 굳이 두번씩 표기 하지 않아도 된다.

<br>

<br>

### :page_facing_up: 10.2. 객체에 함수 추가하기

---

`ES5`의 예

```javascript
const person = {
    name : "TAEKWON",
    greet : function(){
        console.log("Hello");
    },
};

person.greet();	// Hello
```

객체에 함수를 추가하려면 `function`키워드를 사용해야 한다. `ES6`에서는 더욱 편리하게 작성한다.

```javascript
const person = {
    name : "TAEKWON",
    greet(){
        console.log("Hello");
    },
};

person.greet();		// Hello
```

`function`키워드가 없고, 코드는 더 짧아졌지만 동일한 동작을 수행한다.

<br>

화살표 함수는 익명 함수

```javascript
// 다음 코드는 작동하지 않는다. 함수에 접근하기 위한 키가 필요하다.
// 화살표 함수를 사용하기 위해서는 키를 써야한다.
const person1 = {
    () => console.log("Hello"),
};
// Uncaught SyntaxError: Unexpected token '('


// 다음 코드는 작동한다.
const person2 = {
    greet : () => console.log("Hello"),
};

person2.greet();	// Hello
```

<br>

<br>
