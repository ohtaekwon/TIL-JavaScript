#  CHAPTER_11_Quiz

###  :pencil: ***심벌***

<br>

---

<br>

### 11.1. 심벌이란? 답 : 3

`1.`  원시인

`2.`  속성

`3.`  원시자료형

`4.` 함수의 일종

<br>

#### 풀이

***심벌이란?***

`ES6`에서 심벌(Symbol)이라는 새로운 **원시 자료형**이 추가되었다.

<br>

---

<br>

### 11.2. 심벌의 주요 특징은? 답 : 3

`1.`  값을 다시 할당하려고 하면 오류가 발생한다.

`2.`  for 루프 내에서 작동하지 않는다.

`3.`  고유성을 지닌다.

`4.` 정수가 아닌 문자열만 담을 수 있다.

<br>

#### 풀이

***심벌의 고유성***

심벌은 항상 고유하며 객체 속성의 식별자로 사용할 수 있다.

또한 각 심벌은 항상 고유하므로 다른 심벌과 겹치지 않는다.

<br>

---

<br>

### 11.3. 다음 코드의 올바른 출력은? 답 : 4

```javascript
const friends = {
    "Tom" : "bff",
    "Jim" : "brother",
    "Tom" : "cousin",
};

for(friend in friends){
    console.log(friend);
}
```

`1.`  Jim, Tom

`2.`  Error

`3.`  Tom Jim Tom

`4.` Tom Jim

<br>

#### 풀이

심벌을 사용하지 않으면 속성의 이름이 중복되는 것을 피할 수 없다.

```javascript
const friends = {
    "Tom" : "bff",
    "Jim" : "brother",
    "Tom" : "cousin",
};

for(friend in friends){
    console.log(friend);
}
// Tom
// Jim
```

<br>

---

<br>

### 11.4. 다음 코드의 올바른 출력은? 답 : 1

```javascript
const family = {
    [Symbol("Tom")] : "father",
    [Symbol("Jane")] : "mother",
    [Symbol("Tom")] : "brother",
};

const symbols = Object.getOwnPropertySymbols(family);
console.log(symbols);
```

`1.`  Symbol(Tom) Symbol(Jane) Symbol(Tom)

`2.`  Symbol(Tom) Symbol(Jane)

`3.`  undefined

`4.` Symbol(Jane) Symbol(Tom)

<br>

#### 풀이

***객체 속성에 대한 식별자***

심벌은 열거 기능을 하지 않기 때문에 심벌에 대해 반복하려고 하면 **undefined**가 출력된다. 즉 ,`for in`으로 심벌에 대해 반복할 수 없다.

여기서 객체 속성의 배열을 얻기 위해서는 `Object.getOwnPropertySymbol()`를 사용한다.

```javascript
const family = {
    [Symbol("Tom")] : "father",
    [Symbol("Jane")] : "mother",
    [Symbol("Tom")] : "brother",
};

const symbols = Object.getOwnPropertySymbols(family);
console.log(symbols);

// (3) [Symbol(Tom), Symbol(Jane), Symbol(Tom)]
// 0: Symbol(Tom)
// 1: Symbol(Jane)
// 2: Symbol(Tom)
```

