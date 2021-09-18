#  CHAPTER_01_Quiz

###  :pencil: ***var, let, const***

<br>

### 1.1. 다음 코드의 올바른 출력은? 답: 2

```javascript
var greeting = "Hello";
greething = "Farewell";

for(var i=0; i<2; i++){
    var greeting = "Good morning";
}

console.log(greeting);
```

`1.`  Hellog

`2.`  Good moring

`3.`  Farewell;

### 풀이

#### *스코프*

```javascript
var greeting = "Hello";	// 전역 스코프
greething = "Farewell"; // Hellog 에서 FareWell로 전환

for(var i=0; i<2; i++){
    var greeting = "Good morning"; // var은 global scope 이기 때문에 접근이 허용
}

console.log(greeting);	// Good morning
```

<br>

---

<br>

### 1.2. 다음 코드의 올바른 출력은? 답: 3

```javascript
let value = 1;

if(true){
    let value = 2;
    console.log(value);
}

value = 3;
```

`1.`  **1**

`2.`  **2**

`3.`  **3**

### 풀이

```javascript
let value = 1;  // 변수 value 에 1이 저장

if(true){
    let value = 2;		// 블록 스코프로 value에 2가 저장
    console.log(value);	// 블록 스코프안의 value값 2가 출력
}

value = 3;		// value 를 3으로 재할당

console.log(value); // 재할당 된 3이 출력된다.
```

<br>

---

<br>

### 1.3. 다음 코드의 올바른 출력은? 답: 2

```javascript
let x = 100;		// 전역 스코프

if(x>50){			// 블록 스코프
    let x = 10;
}

console.log(x); // 전역 스코프에 접근한 값 100이 출력된다.
```

`1.`  **10**

`2.`  **100**

`3.`  **50**

<br>

---

<br>

### 1.4. 다음 코드의 올바른 출력은? 답: 2

```javascript
console.log(constant);

const constant = 1;
```

`1.`  **undefined**

`2.`  **ReferenceError**

`3.`  **1**

### 풀이

let과 const 변수는 정의되기 전에 접근할 수 없다. 따라서 `Uncaught ReferenceError: j is not defined`가 출력된다.

<br>
