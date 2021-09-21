#  CHAPTER_08_Quiz

###  :pencil: ***배열 메서드***

<br>

---

<br>

### 8.1. 다음 작업을 수행하는 코드를 작성하자. 

##### 다음과 같은 코드에서, 문자열의 각 문자가 배열의 각 원소가 되도록 새 배열을 생성하시오.

```javascript
const apple = "Apple";

const myArr = // 여기에 코드를 추가하자.

console.log(myArr);	// 기대 출력 : ["A", "p", "p", "l", "e"]
```

<br>

#### 풀이

`Array.from()`은 배열처럼 보이지만 배열이 아닌 객체를 받아서 실제 **배열로 변환해 반환**한다.

```javascript
const apple = "Apple";

const myArr = Array.from(apple);

console.log(myArr);	// ['A', 'p', 'p', 'l', 'e']
```

<br>

---

<br>

### 8.2. 다음 코드의 올바른 출력은? 답 : 4

```javascript
const array = [1,2,3,4,5];
let found = array.find(e =>e>3);
console.log(found);
```

`1.`  3

`2.`  5

`3.`  4, 5

`4.`  4

<br>

#### 풀이

`Array.findIndex()`조건과 일치하는 **첫 번째** 원소의 인덱스를 반환한다.

즉, 조건 `e>3`과 만족하는 **첫 번째 원소**는 `4`가 된다.

<br>

---

<br>

### 8.3. 다음 코드의 올바른 출력은? 답 : 4

```javascript
const array = [1,2,3,4,5,6,1,2,3,1];

let arraySome = array.some(e=>e>2);

console.log(arraySome);
```

`1.`  2

`2.`  false

`3.`  3

`4.`  true

<br>

#### 풀이

`.some()`은 **조건과 일치하는 원소**가 있는지 검색하고 첫 번째 일치하는 원소를 찾으면 바로 중지한다.

<br>

---

<br>

### 8.4. 다음 코드의 올바른 출력은? 답 : 2

```javascript
Array.from([1,2,3], x=>x*x);
```

`1.`  [1,2,3]

`2.`  [1,4,9]

`3.`  [1,3,5]

<br>

#### 풀이

# Array.from()

`Array.from()` 메서드는 유사 배열 객체(array-like object)나 반복 가능한 객체(iterable object)를 얕게 복사해 새로운`Array` 객체를 만듭니다.

```javascript
console.log(Array.from('foo'));
// expected output: Array ["f", "o", "o"]

console.log(Array.from([1, 2, 3], x => x + x));
// expected output: Array [2, 4, 6]
```

#### 구문

```javascript
Array.from(arrayLike[, mapFn[, thisArg]])
```

##### 매개변수

- `arrayLike`
  - 배열로 변환하고자 하는 유사 배열 객체나 반복 가능한 객체.
- `mapFn Optional`
  - 배열의 모든 요소에 대해 호출할 맵핑 함수.
- `thisArg Optional`
  - `mapFn`실행시에 `this`로 사용할 값.

```javascript
Array.from([1,2,3], x=>x*x);  // [1, 4, 9]

console.log(Array.from([1,2,3]));			// [1, 2, 3]
console.log(typeof Array.from([1,2,3]));	// object
// 
```

`Array.from([1,2,3], x=>x*x);`했을 때, `1 * 1` , `2 * 2` , `3 * 3`

<br>

---


