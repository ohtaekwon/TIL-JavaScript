#  CHAPTER 17

###  :pencil: ***ES2016의 새로운 기능***

`ES2016`에서는 두 가지 기능이 새롭게 도입되었다.

- `Array.prototype.includes()`
- 지수연산자(**)

<br>

### :page_facing_up: 17.1. Array.prototype.includes()

---

`includes()` 메서드는 배열에 특정 원소가 포함되어 있으면 `true`를 반환하고 그렇지 않으면 `false`를 반환한다.

```javascript
let array = [1,2,3,4,5];

array.includes(2);		// true
array.includes(6);		// false
```

<br>

### 17.1.1. `includes()`를 인덱스와 함께 사용하기

`includes()`에 인덱스를 추가해서 원소를 검색할 수 있다. 기본값은 `0`이지만 음수를 전달할 수도 있다.

`includes()` 에 전달하는 첫 번째 값은 검색할 원소이고, 두 번째 값이 검색을 시작할 인덱스이다.

```javascript
let array = [1,3,5,7,9,11];

// 인덱스 1부터 시작해서 숫자 3을 찾기
array.includes(3,1);			// true

// 인덱스 4부터 시작해서 숫자 5를 찾기
array.includes(5,4);			// false

// 배열 끝에서 첫 번째 인덱스부터 숫자 1을 찾기
array.includes(1,-1);			// false

// 배열 끝에서 세 번째 인덱스부터 숫자 11을 찾기
array.includes(11,-3);			// true
```

- `array.includes(5,4);` 는 `false`를 반환했다. 배열은 실제로 인덱스 `2`에 숫자 `5`를 포함하고 있지만 인덱스 `4`부터 찾기 시작했기 때문이다.
- `array.includes(1,-1);` 는 인덱스 `-1`, 즉 배열의 마지막 원소부터 찾기 시작했기 때문에 `false`를 반환했다.
- `array.includes(11,-3);`는 인덱스 `-3`, 즉 배열의 마지막 원소부터 3번째 원소(7)부터 시작했기 때문에 `11`을 찾을 수 있었고 따라서 `true`를 반환했다.
  - 반면, 예를들어 `5`를 인덱스 `-3` 부터찾는다면 `array.includes(5, -3);` 는 `false`를 반환할 것이다.

<br>

<br>
