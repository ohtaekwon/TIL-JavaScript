#  CHAPTER 08

###  :pencil: ***배열 메서드***

<br>

### :page_facing_up: 8.1. Array.from()

---

`Array.from()`은 `ES6`에서 도입한 새로운 **배열 메서드**들 중 첫 번째이다.

`Array.from()`은 배열스러운(arrayish), 즉 배열처럼 보이지만 배열이 아닌 객체를 받아서 실제 배열로 변환해 반환한다.

```html
<div class = "fruits">
    <p>Apple</p>  
    <p>Banna</p>
    <p>Orange</p>
</div>
```

```javascript
const fruits = document.querySelectorAll(".fruits p");
// fruits 는 3개의 p 태그를 포함한 노드 리스트(배열과 비슷한 구조)이다.

console.log(fruits); 	// NodeList(3) [p, p, p]

// 이제 fruits를 배열로 변환하자.
const fruitArray = Array.from(fruits);

console.log(fruitArray);	// [p, p, p]
console.log(typeof fruitArray);	// object

// 이제 배열을 취급하므로 map()을 사용할 수 있다.
const fruitsNames = fruitArray.map(fruit => fruit.textContent);

console.log(fruitsNames);	// ["Apple", "Banna", "Orange"]
```

이와 같이 `fruits`를 배열로 변환했다. 따라서 **map** 등 배열이 제공하는 모든 메서드를 사용할 수 있는 상태가 되었다. 

전체 태그가 아닌 ``p`태그의 `textContent`만 새로운 배열로 만들었다.

<br>

또한, `Array.from()`의 두 번째 인수를 이용해서, 배열에 **map** 함수를 적용한 것과 동일한 기능을 하는 코드를 작성할 수도 있다. 

```javascript
const fruits = document.querySelectorAll(".fruits p");
console.log(fruits); 	// NodeList(3) [p, p, p]

const fruitArray = Array.from(fruits, fruit =>{
    console.log(fruit);
    // <p> Apple </p>
    // <p> Banana </p>
    // <p> Orange </p>
    
    
    // 태그 자체는 제외하고 태그 안의 텍스트 내용만 얻고자 한다.
    // ['Apple', 'Banna', 'Orange']
    return fruit.textContent;
});

console.log(fruitArray);	// ['Apple', 'Banna', 'Orange']
```

이 예시에서는 `map` 역할을 하는 함수를 `.from()` 메서드의 두 번째 인수에 전달하여 동일한 결과를 얻었다.

<br>

<br>

### :page_facing_up: 8.2. Array.of()

---

`Array.of()` 는 전달받은 모든 인수로 배열을 생성한다.

```javascript
const digits = Array.of(1,2,3,4,5);

console.log(digits);		// [1, 2, 3, 4, 5]
```

`Array.of()` 메서드는 인자의 수나 유형에 관계없이 가변 인자를 갖는 새 `Array` 인스턴스를 만듭니다.

`Array.of()`와 `Array` 생성자의 차이는 정수형 인자의 처리 방법에 있습니다. `Array.of(7)`은 하나의 요소 `7`을 가진 배열을 생성하지만 `Array(7)`은 `length` 속성이 7인 빈 배열을 생성한다.

```javascript
Array.of(7);		// [7]
Array.of(1,2,3,4);	// [1,2,3,4]

Array(7);			// [ , , , , , ,] [비어 있음 × 7]
Array(1,2,3);		// [1, 2, 3]
```

<br>

<br>

### :page_facing_up: 8.3. Array.find()

---

`Array.find()`는 제공된 테스트 함수를 충족하는 배열의 **첫 번째 원소**를 반환한다. 충족하는 원소가 없으면 `undefined`를 반환한다.

```javascript
const array = [1,2,3,4,5];

// 배열의 원소 중 3보다 큰 첫 원소를 반환한다.
let found = array.find(e => e>3);
console.log(found);			// 4
```

- `조건( > 3)` 과 일치하는 **첫 번째** 원소를 반환하므로 `5`가 아닌 `4`가 반환된다.

<br>

```javascript
const array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10);

console.log(found); // expected output: 12
```

<br>

<br>

### :page_facing_up: 8.4. Array.findIndex()

---

`Array.findIndex()`조건과 일치하는 **첫 번째** 원소의 인덱스를 반환한다.

```javascript
const greetings = ["hello", "hi", "MUYAHO", "byebye", "goodbye", "hi"];

let foundIndex = greetings.findIndex(element => element === "hi");
console.log(foundIndex);	// 1

let findMuyaho = greetings.findIndex(element => element === "MUYAHO");
console.log(findMuyaho); // 2
```

- 즉, 조건과 일치하는 **첫 번째** 원소의 인덱스만 반환한다.

<br>

<br>
