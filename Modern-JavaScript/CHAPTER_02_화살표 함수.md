#  CHAPTER 02

###  :pencil: ***화살표 함수***

<br>

<br>

### :page_facing_up: 2.1. 화살표 함수

---

`ES6` 에서 뚱뚱한 화살표`=>`를 사용해서 함수를 선언하는 방법인 **화살표 함수**가 처음 도입되었다. 

<br>

1) `ES5`에서 일반적으로 함수를 선언하는 방법은 다음과 같다.

```javascript
const greeting = function(name){
    return "hello" + name;
};	// undefined
```

<br>

2) 이를 화살표 함수 문법으로 바꾸면

```javascript
var greeting = (name) => {
    return `hello ${name}`;
};
```

<br>

3) **매개변수가 하나**만 있으면 괄호를 생략할 수 있다.

```javascript
var greeting = name => {
    retrun `hello ${name}`;
};
```

<br>

4) 매개변수가 전혀 없으면 빈 괄호를 써야 한다.

```javascript
var greeting = () => {
    return "hello";
};
```

<br>

<br>

### :page_facing_up: 2.2. 암시적 반환

---

화살표 함수를 사용하면 명시적인 반환을 생략하고 다음과 같이 반환할 수 있다.

```javascript
const greeting = name => `hello ${name}`;	// undefined
```

`ES5`의 함수와 비교

```javascript
const oldFunction = function(name){
    return "hello" + name;
};

// 두 함수 모두 결과는 같지만, 화살표 함수를 사용하면 코드가 더 간결해진다.
const arrowFunction = name => `hello ${name}`;
```

`ES6`_의 문법을 숙지하지 못했을 때_

```javascript
const arrFunction = (name) => {
    return `hello ${name}`;
};
```

_객체 리터럴을 암시적으로 반환할 때_

```javascript
const race = "100m dash";
const runners = ["Usain Bolt", "Justin Gatlin", "Asafa Powell"];

const results = 
      runners.map((runner, i) => ({name : runner, race, place : i+1}));

console.log(results);

/*

[
    {
        "name": "Usain Bolt",
        "race": "100m dash",
        "place": 1
    },
    {
        "name": "Justin Gatlin",
        "race": "100m dash",
        "place": 2
    },
    {
        "name": "Asafa Powell",
        "race": "100m dash",
        "place": 3
    }
]

*/
```

이 예에서는 **map** 함수를 사용하여 `runners`배열에 대한 **반복(순회, iteration)**을 구현한다. 

- 첫 번째 인수 `runner`는 **배열의 현재 원소**이다. 
- 두 번째 인수  `i`는 **배열의 인덱스**이다. 

배열의 각 원소에 대해 `name`, `race`, `place` 속성을 포함하는 객체를 `results`에 추가한다.

중괄호`{}` 안에 있는 것이 암시적으로 반환하려는 **객체 리터럴**임을 자바스크립트에 알리기 위해서는 전체를 괄호`()` 안에 감싸야 한다. 

여기서 `race`를 쓰나 `race : race`를 쓰나 모두 결과는 동일하다.

<br>

#### _map메서드_

map 메서드는 다음과 같이 사용한다. `배열.map((요소, 인덱스, 배열) => { return 요소 });`

map의 기본원리는 **반복문을 돌며 배열 안의 요소들을 1대1로 짝지어 주는 것**이다. 그래서 이름이 map이다. 즉, **매핑****한다고 표현한다. 어떻게 짝지어줄 것인가 정의한 함수를 메서드의 인자로 넣어주면 된다.

```javascript
const oneTwoThree = [1, 2, 3];
let result = oneTwoThree.map((v) => {
  console.log(v);
  return v;
});
// 콘솔에는 1, 2, 3이 찍힘
oneTwoThree; // [1, 2, 3]
result; // [1, 2, 3]
oneTwoThree === result; // false
```

_각 요소에 1씩 더한 값을 반환_

```jsx
result = oneTwoThree.map((v) => {
  return v + 1;
});
result; // [2, 3, 4]
```

<br>

<br>

### :page_facing_up: 2.3. 화살표 함수는 익명 함수

---

화살표 함수는 익명 함수이다. 참조할 이름이 필요하다면 함수를 변수에 할당하면 된다.

```javascript
const greeting = name => `hello ${name}`;
greeting("TAEKWON");		// 'hello TAEKWON'
```

<br>

<br>

### :page_facing_up: 2.4. 화살표 함수와 this 키워드

---

화살표 함수 내부에서 `this` 키워드를 사용할 때는 **일반 함수와 다르게 동작**하므로 주의해야한다.

***화살표 함수를 사용할 때 `this` 키워드는 상위 스코프에서 상속된다.***

##### 1) HTML

```html
<div class = "box open">
    This is a box
</div>
```

##### 2) CSS

```css
.opening{
    background-color : red;
}
```

##### 3) JS

```javascript
// box 클래스를 가진 div를 가져온다.
const box = document.querySelector(".box");

// click 이벤트 핸들러를 등록
box.addEventListener("click", function(){
    // div에 opening 클래스를 토글
    this.classList.toggle("opening");
    
    setTimeout(function(){
        // 클래스를 다시 토글
        this.classList.toggle("opening");
    }, 500);   
});
```

이 코드의 문제는, 첫 번째 `this`가 **const box** 에 할당되었지만, 

**setTimeout** 내부의 두 번째 `this`는 **Window**객체로 설정되어 오류가 발생한다.

<br>

화살표 함수가 **부모 스코프**에서 `this`의 값을 상속한다는 것을 인지하면 다음과 같이 함수를 다시 작성할 수 있다.

```javascript
const box = document.querySelector(".box");
// click 이벤트 핸들러 등록
box.addEventListener("click", function(){
    // div에 opening 클래스를 토글
    this.classList.toggle("opening");
    
    setTimeout(()=>{
        // 클래스를 다시 토글
        this.classList.toggle("openong");
    }, 500);
});
```

여기서 두 번째 `this`는 부모로부터 상속되며 `const box`로 설정된다.

<br>

<br>

### :page_facing_up: 2.5. 화살표 함수를 피해야 하는 경우

---

#### _ex) 화살표 함수에서 this를 주의해서 사용해야 하는 경우_

```javascript
const button = document.querySelector("btn");
button.addEventListenner("click", ()=>{
    // 오류 : 여기서 this는 Window 객체를 가리킴
    this.classList.toggle("on");
});
```

<br>

#### _ex) 화살표 함수와 일반 함수의 차이_

```javascript
const person1 = {
    age:10,
    grow: function(){
        this.age++;
        console.log(this.age);
    },
};

person1.grow(); // 11
console.log(person1); // {age: 11, grow: ƒ}

const person2 = {
    age : 10,
    grow : () => {
        // 오류 : 여기서 this는 Window 객체를 가리킨다. 
        this.age++;
        console.log(this.age);
    },
};

person2.grow();		// NaN
```

이처럼 화살표 함수에서 `this`를 사용시에 주의를 해야한다.

<br>

그리고 화살표 함수와 일반 함수의 또 다른 차이점이 있다.

- **arguments** 객체에 대한 접근 방식이다. 

**arguments** 객체는 함수 내부에서 접근할 수 있는 **배열 객체**이며, 해당 함수에 전달된 인수의 값을 담고 있다.

```javascript
function example(){
    console.log(arguments[0])
}

example(1,2,3);		// 1
```

이와 같이 배열 표기법 **arguments[0]**을 사용하면 **첫 번째 인수에 접근**할 수 있다. 

`this` 키워드와 비슷하게, 화살표 함수에서 **arguments**객체는 **부모 스코프의 값을 상속**한다. 

```javascript
const showWinner = () => {
    const winner = arguments[0];
    console.log(`${winner} was the winner`);
};

showWinner("BTS", "IU", "Black Pink", "Iron Man", "Hulk");

// Uncaught ReferenceError: arguments is not defined
```

함수에 전달된 모든 인수에 접근하려면, 기존 함수 표기법이나 스프레드 문법을 사용한다. 

<br>

#### 화살표 함수와 일반 함수의 arguments 에 접근

#### _1) 화살표 함수로 arguments에 접근하기_

```javascript
const showWinner = (...args) => {
    const winner = args[0];
    console.log(`${winner} was the winner`);
};

showWinner("BTS", "IU", "Black Pink", "Iron Man", "Hulk"); 	// BTS was the winner
```

<br>

#### _2) 일반 함수로 arguments에 접근하기_

```javascript
const showWinner = function(){
    const winner = arguments[0];
    console.log(`${winner} was the winner`);
};

showWinner("BTS", "IU", "Black Pink", "Iron Man", "Hulk"); 	// BTS was the winner
```


