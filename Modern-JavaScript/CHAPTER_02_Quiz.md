#  CHAPTER_02_Quiz

###  :pencil: ***화살표 함수***

<br>

### 2.1. 다음 중 화살표 함수의 문법에 맞게 활용한 예는? 답 : 2

```javascript
let arr = [1, 2, 3];

// a)
let func = arr.map(n -> n+1);

// b)
let func = arr.map(n => n+1);	// (3) [2, 3, 4]

// c)
let func = arr.map(n ~> n+1);
```

`1.`  a

`2.`  b

`3.`  c

<br>

---

<br>

### 2.2. 다음 코드의 올바른 출력은? 답 : 1

```javascript
const person = {
    age : 10,
    grow : () => {
        this.age++;
    },
};

person.grow();		// undefined
console.log(person.age); 	// 10
```

`1.`  10

`2.`  11

`3.`  undefined

<br>

#### 풀이

: 화살표 함수를 `this`에서 사용할 때 주의를 해야한다. 부모스코프 값을 상속한다.

```javascript
const person = {
    age : 10,
    grow : function(){
        this.age++;
    },
};

person.grow();	// undefined
console.log(person.age);	// 11
```

<br>

---

<br>

### 2.3. 화살표 함수 문법을 사용해서 다음 코드를 리팩터링하라.

```javascript
function(arg){
    console.log(arg);
}
```

<br>

#### 풀이

```javascript
(...args) => {
    console.log(args)
}
```

