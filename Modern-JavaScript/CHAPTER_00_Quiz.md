#  CHAPTER_00_Quiz

###  :pencil: ***자바스크립트 기초***

<br>

### 0.1. 다음 중 변수 이름 지정 방법이 잘못된 것은? 답: 3

`1.`  var very_important  = "very_important";

`2.`  var important_999 = "important_999";

`3.`  var important! = "important!";

`4.`  var VeRY_ImP_orTant = "VeRY_ImP_orTant";

### 풀이

#### *변수 명명법*

```javascript
// 변수명은 숫자로 시작할 수 없다
let 1apple = "one apple";    // 불가능

// 변수명에는 공백, 기호, 마침표가 들어갈 수 없다.
let hello! = "hello!"; 		// 불가능
```



<br>

---

<br>

### 0.2. 다음 중 원시 자료형이 아닌 것은? 답: 4

`1.`  **symbol**

`2.`  **boolean**

`3.`  **null**

`4.`  **object**

### 풀이

#### *원시자료형*

**원시 자료형**(primitive)은 객체가 아닌 자료형으로, 메서드를 가지지 않는다. 다음과 같이 자료형이 원시 자료형에 해당한다.

- **string** : **문자열**
- **number** : **숫자**
- **boolean** : **불리언**
- **null** : **널**
- **undefined** : **정의되지 않음**
- **symbol** : **심벌** (`ES6`에서 추가 됨. )

**object**는 객체로 원시자료형이 아니다.

<br>

---

<br>

### 0.3. 다음 중 객체를 정의하는 올바른 방법은? 답: 3

`1.`  const car : {color : 'red'};

`2.`  const car = {color = "red"};

`3.`  const car = {color: "red"};

`4.`  const car : {color = "red"};

### 풀이

#### *변수와 객체의 표기법*

```javascript
const car = new Object();

// 2.
const car = {} 
```

<br>

---

<br>

### 0.4. 다음 코드의 올바른 출력은 무엇인가?  답: 3

```javascript
const obj1 = {a:1};
const obj2 = {a:1};

console.log(obj1 === obj2);
```

`1.`  true

`2.`  undefined

`3.` false

`4.`  null

### _풀이_

#### *빈 객체끼리 비교 vs. 동일한 속성을 가진 객체끼리 비교*

```javascript
const emptyObj1 = {};
const emptyObj2 = {};

emptyObj1 == emptyObj2;			// false
emptyObj1 === emptyObj2; 		// false

const obj1 = {a:1};
const obj2 = {a:1};

obj1 == obj2;					// false
obj1 === obj2;					// false

obj1 == obj1;					// true
```

- 동일한 객체를 비교할 때만 **true**를 반환받을 수 있다.

<br>

---

<br>

### 0.5. 다음 코드의 올바른 출력은 무엇인가?  답: 1

```javascript
const fruitBasket = ['apple', 'banna', 'orange'];
fruitBasket.unshift('melon');
console.log(fruitBasket);
```

`1.` ["apple", "banna", "orange", "melon"]

`2.`  ["melon"]

`3.`  ["apple", "banna", "orange", "pear", "melone"]

`4.`  ["melon", "apple", "banna" , "orange"]

### _풀이_

##### *배열에 대해 호출할 수 있는 메서드*

```javascript
const fruitBasket = ['apple', 'banna', 'orange'];

// 배열의 길이 확인
console.log(fruitBasket.length);	// 3

// 배열의 끝에 새 값을 추가
fruitBasket.push('pear');			// 4
console.log(fruitBasket);			// (4) ['apple', 'banna', 'orange', 'pear']

// 배열의 시작에 새 값을 추가
fruitBasket.unshift('melon');		// 5
console.log(fruitBasket);			// (5) ['melon', 'apple', 'banna', 'orange', 'pear']

// 배열의 끝에서 값 하나를 제거
fruitBasket.pop();					// 'pear'
console.log(fruitBasket);			// (4) ['melon', 'apple', 'banna', 'orange']

// 배열의 시작에서 값 하나를 제거
fruitBasket.shift();				// 'melon'
console.log(fruitBasket);			// (3) ['apple', 'banna', 'orange']
```

<br>

----





