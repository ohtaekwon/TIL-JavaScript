#  CHAPTER_09_Quiz

###  :pencil: ***스프레드 연산자와 레스트 매개변수***

<br>

---

<br>

### 9.1. 배열의 값을 확장하기 위한 스프레드의 올바른 문법은? 답 : 3

`1.`  [.]

`2.`  (...)

`3.`  [...]

`4.`  {...}

<br>

#### 풀이

***배열에서의 스프레드 문법 예시***

```javascript
const veggie = ["tomato", "cucumber", "beans"];
const meat = ["pork","beef","chicken"];

const menu = [...veggie, "pasta", ...meat];
console.log(menu);
// (7) ['tomato', 'cucumber', 'beans', 'pasta', 'pork', 'beef', 'chicken']
```

<br>

---

<br>

<br>

### 9.2. 다음 작업을 코드를 작성하자. 답 : 4

### veggie와 meat가 주어졌을 때, 다음을 포함하는 menu라는 새 배열을 생성하시오.

- veggie의 모든 값
- 'pasta' 값을 가지는 새 문자열
- meat의 모든 값

```javascript
const veggie = ["tomato", "cucumber", "beans"];
const meat = ["pork", "beaf", "chicken"];
```

<br>

#### 풀이

```javascript
const veggie = ["tomato", "cucumber", "beans"];
const meat = ["pork", "beaf", "chicken"];

const menu = [...veggie, "pasta", ...meat];
console.log(menu);
// (7) ['tomato', 'cucumber', 'beans', 'pasta', 'pork', 'beaf', 'chicken']
```

<br>

---

<br>

<br>

### 9.3. 다음 작업을 코드를 작성하자. 

### 다음과 같이 배열 runners 가 주어졌을 때, 처음 2개 이후의 모든 값을 포함하는 losers라는 새 배열을 생성하자.

```javascript
const runners = ["Tom", "Paul", "Mark", "Luke"];
```

<br>

#### 풀이

***레스트 연산자 사용하기***

```javascript
const runners = ["Tom", "Paul", "Mark", "Luke"];

const [first, second, ...losers] = runners;
console.log(losers);	// ['Mark', 'Luke']
console.log(first);		// Tom
console.log(second);	// Paul
```

<br>

---

<br>

<br>

### 9.4. 다음 코드의 올바른 출력은? 답 : 3

```javascript
let arr = [1, 2, 3, 4];

let arr2 = arr;

arr2.push(5);
console.log(arr);
```

`1.`  [1, 2, 3, 4]

`2.`  [1, 2, 4, 5]

`3.`  [1, 2, 3, 4, 5]

`4.`  "1, 2, 3, 4, 5"

<br>

#### 풀이

***배열의 복사***

```javascript
const veggie = ["tomato","cucumber", "beans"];
const newVeggie = veggie;

// veggie 배열의 복사본을 생성한 것처럼 보이지만, 다음을 보자.

veggie.push("peas");	// 4

console.log(veggie); // (4) ['tomato', 'cucumber', 'beans', 'peas']

console.log(newVeggie);	// (4) ['tomato', 'cucumber', 'beans', 'peas']
```

- **기존 배열(veggie)**을 수정하자 **새 배열(newVeggie)** 도 변경되었다.

왜냐하면 실제로 복사본을 만든 것이 아니라, 새 배열은 단순히 이전 배열을 **참조**하였기 때문이다.

<br>

---

<br>

<br>
