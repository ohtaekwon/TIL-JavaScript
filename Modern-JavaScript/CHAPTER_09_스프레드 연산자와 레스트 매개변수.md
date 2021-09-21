#  CHAPTER 08

###  :pencil: ***스프레드 연산자와 레스트 매개변수***

<br>

### :page_facing_up: 9.1. 스프레드 연산자

---

MDN은 **스프레드 문법**(Spread syntax)을 다음과 같이 설명한다.

​	스프레드 문법을 사용하면 `0개` 이상의 인수(함수 호출용) 또는 원소(배열 리터럴용)가 에쌍되는 위치에서 배열 표현식 또는 문자열과 같은 이터러블 항목을 확장하거나 0개 이상의 `키/값 쌍`(객체 리터럴용)이 예상되는 위치에서 객체 표현식을 확장할 수 있다.

<br>

### 9.1.1. 배열의 결합

```javascript
	const veggie = ["tomato", "cucumber", "beans"];
const meat = ["pork","beef","chicken"];

const menu = [...veggie, "pasta", ...meat];
console.log(menu);
// (7) ['tomato', 'cucumber', 'beans', 'pasta', 'pork', 'beef', 'chicken']
```

여기서 `...`이 바로 스프레드 문법으로, `veggie`와 `meat` 배열의 모든 개별 원소를 풀어서 `menu`배열에 넣었고, 동시에 그 사이에 새 항목을 추가했다.

<br>

### 9.1.2. 배열의 복사

스프레드 문법은 배열의 복사본을 생성할 때 매우 유용하다.

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

##### `ES5` 및 이전 버전에서 일반적으로 배열의 복사본을 만드는 방법

```javascript
const veggie = ["tomato","cucumber","beans"];
// 빈 배열을 새로 생성하고 기존 배열의 값을 새 배열에 이어 붙인다.
const newVeggie = [].concat(veggie);
veggie.push("peas");
console.log(veggie);	// (4) ['tomato', 'cucumber', 'beans', 'peas']
console.log(newVeggie);	// (3) ['tomato', 'cucumber', 'beans']
```

<br>

##### 스프레드 문법을 활용

```javascript
const veggie = ["tomato","cucumber","beans"];
const newVeggie = [...veggie];
veggie.push("peas");
console.log(veggie);	// (4) ['tomato', 'cucumber', 'beans', 'peas']
console.log(newVeggie);	// (3) ['tomato', 'cucumber', 'beans']
```

스프레드 연산자의 문법은 `...YourArray`이런 식으로 접근한다. 
