#  CHAPTER_07_Quiz

###  :pencil: ***루프***

<br>

---

<br>

### 7.1. ES6에 새로 도입된 루프는 무엇인가? 답 : 2

`1.`  while

`2.`  for of

`3.`  for in

<br>

#### 풀이

`ES6`는 새로운 유형의 루프인 **for of** 루프를 도입했다.

`for of`를 활용하여 배열의 각 원소에 대해 반복하는 방법을 더 쉽게 만들었다.

```javascript
// 기존의 배열 방법
var fruits = ['apple', 'banna', 'orange'];
for(var i=0; i<fruits.length; i++){
    console.log(fruits[i]);
}
// apple
// banna
// orange

const fruits = ['apple', 'banna', 'orange'];
for (const fruit of fruits){
    console.log(fruit);
}

// apple
// banna
// orange
```

또한 `for of`를 활용하여 객체에 대한 반복하는 방법도 편리해졌다.

```javascript
// for of를 활용한 객체에 대한 반복 방법
const car = {
    maker : "BMW",
    color : "red",
    year : "2020",
};

for (const prop of Object.keys(car)){
    const value = car[prop];
    console.log(prop,value);
}

// maker BMW
// color red
// year 2020
```

<br>

---

<br>

### 7.2. 다음 코드의 올바른 출력은? 답 : 3

```javascript
let people = ["Tom", "Jerry", "Mickey"];

for(let person of people){
    console.log(person);
}
```

`1.`  Tom Jerry

`2.`  Tom

`3.`  Tom Jerry Mickey

`4.`  Mickey

<br>

#### 풀이

```javascript
let people = ["Tom", "Jerry", "Mickey"];

for(let person of people){
    console.log(person);
}

// Tom
// Jerry
// Mickey
// for of를 통해서 배열에 대한 값들을 반환한다. 
```

