#  CHAPTER 07

###  :pencil: ***루프***

<br>

### :page_facing_up: 7.1. for of 루프

---

`ES6`는 새로운 유형의 루프인 **for of** 루프를 도입했다.

### 7.1.1. 배열에 대한 반복

배열의 각 원소에 대해 반복하려면 보통의 경우에 다음과 같이 구현해야 했다.

```javascript
var fruits = ['apple', 'banna', 'orange'];
for(var i=0; i<fruits.length; i++){
    console.log(fruits[i]);
}
// apple
// banna
// orange
```

이것은 매 반복 시 `i`가 `fruits.length`보다 작은 한 `i`의 값을 `1` 증가시키는 일반적인 루프이다.

`i`가 `fruits.length`와 같은 값이 되는 시점에서 루프가 중지된다.

<br>

##### _for of 루프를 사용하면 동일한 결과를 얻을 수 있다._

```javascript
const fruits = ['apple', 'banna', 'orange'];
for (const fruit of fruits){
    console.log(fruit);
}

// apple
// banna
// orange
```

<br>

### 7.1.2. 객체에 대한 반복

객체는 **이터러블**(iterable)이 아니다. 그러면 객체의 `키/값 쌍`에 대한 반복은 어떻게 구현할 수 있을까? 

- 먼저, `Object.keys()`를 사용하여 객체의 모든 키를 가져온 후, 키에 대한 반복을 수행하면서 값에 접근하는 것이 가능하다.

```javascript
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

새로운 `ES6` 함수인 `Object.entries()`를 사용하여 객체의 모든 `키/값 쌍`을 가져온 후 , 각 `키/값 쌍`에 대해 반복을 수행하는 방법도 있다.

<br>

<br>

### :page_facing_up: 7.2. for in 루프

---

`ES6`에서 새로 도입된 루프는 아니지만, `for in` 루프를 살펴보고 `for of`루프와 다른 점을 이해할 수 있다.

`for in`루프는 순서 없이 객체의 모든 열거 가능한 속성을 반복하기 때문에 `for of`와 약간 다르다.

- 따라서 반복 중에는 객체의 속성을 **추가**, **수정**, **삭제** 하지 않는 것이 좋다. 
  - 반복 중에 해당 속성을 거칠 것이라는 보장이 없고, 수정 전이나 수정 후에 거칠 것이라는 보장도 없기 때문이다.

```javascript
const car = {
    maker : "BMW",
    color : "red",
    year : "2010",
};

for (const prop in car){
    console.log(prop, car[prop]);
}
// maker BMW (prop은 "maker"가 되고, car[prop] 값은 "BMW"가 된다.)
// color red (prop은 "color"가 되고, car[prop] 값은 "red"가 된다.)
// year 2010 (prop은 "year"가 되고, car[prop] 값은 "2010"가 된다.)
```

<br>

<br>

