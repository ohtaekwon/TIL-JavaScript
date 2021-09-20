#  CHAPTER_06_Quiz

###  :pencil: ***디스트럭처링***

<br>

---

<br>

### 6.1. 다음 작업을 수행하는 코드를 작성하자 

#### 디스트럭처링을 사용하여 두 변수의 값을 교체하라.

```javascript
let hungry = "yes";
let full = "no";

// 여기에 코드를 작성하자.

console.log(hungry);	// no
console.log(full);		// yes
```

<br>

#### 풀이

```javascript
let hungry = "yes";
let full = "no";

// 여기에 코드를 작성하자.
[hungry, full] = [full, hungry];

console.log(hungry);	// no
console.log(full);		// yes
```

<br>

---

<br>

### 6.2. 다음 작업을 수행하는 코드를 작성하자 

#### 한 줄의 코드로 다음 배열의 각 값을 저장하는 변수를 선언하자.

```javascript
let arr = ["one", "two", "three"];

// 여기에 코드를 작성하자.

// 예상 결과
console.log(one);		// one
console.log(two);		// two
console.log(three);		// three
```

<br>

#### 풀이

```javascript
let arr = ["one", "two", "three"];

// 여기에 코드를 작성하자.
let [one, two, three] = arr;

// 예상 결과
console.log(one);		// one
console.log(two);		// two
console.log(three);		// three
```

<br>

