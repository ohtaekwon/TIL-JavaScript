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
