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
