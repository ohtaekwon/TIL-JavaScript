#  CHAPTER_17_Quiz

###  :pencil: ***ES2016의 새로운 기능***

<br>

---

<br>

### 17.1. ES2016에 도입된 새로운 배열 메서드는? 답 : 3

`1.`  `Array.prototype.contains()`

`2.`  `Array.prototype.has()`

`3.`  `Array.prototype.includes()`

`4.`  `Array.prototype.find()`

<br>

#### 풀이

`ES2016`에서는 두 가지 기능이 새롭게 도입되었다.

- `Array.prototype.includes()`
- 지수연산자(**)

<br>

# Set.prototype.has()

`has()` 메서드는 `Set` 객체에 주어진 요소가 존재하는지 여부를 판별해 반환한다.

<br>

# Array.prototype.find()

`find()` 메서드는 주어진 판별 함수를 만족하는 **첫 번째 요소**의 **값**을 반환합니다. 그런 요소가 없다면

<br>

---

<br>

### 17.2. 다음 코드의 올바른 출력은? 답 : 4

```javascript
let array = [1,3,5,7,9,11];

array.includes(5,4);
```

`1.`  4

`2.`  true

`3.`  5

`4.`  false

<br>

#### 풀이

##### Array.prototyoe.includes()

`array.includes(5,4);` 은 인덱스 `4`에서부터 5를 찾는 것이기 때문에, 인덱스 `4`에 해당하는 `9`에서부터 `5`는 찾을 수 없으므로 `false`가 출력된다.

만약 인덱스 조건은 그대로 두며 `true`가 출력되기 위해서는 다음과 같이 한다.

```javascript
array.includes(9,4);		// true
array.includes(11,4);		// true
```

<br>

---

<br>

### 17.3. 다음 작업을 수행하는 코드를 작성해보자.

#### 새로운 지수 연산자를 활용하여 다음 코드를 리팩터링 하자

```javascript
Math.pow(Math.pow(2,2,),2);		// 16
```

<br>

#### 풀이

##### 새로운 지수연산자(`**`)

`Math.pow()` 는 `**`과 같다.

```javascript
2 ** 2 ** 2
```

- `Math.pow(2,2)`는 `2 * 2`와 같다.
- 즉, `Math.pow(Math.pow(2,2),2);` 는  `Math.pow(2**2, 2);` 와 같으므로,
  - 결과적으로 `2 ** 2 ** 2`가 된다.
