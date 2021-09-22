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

위의 예시에서 변수 `newVeggie`를 배열 `veggie`의 복사본으로 만들기 위해, 우선 `newVeggie`에 배열을 할다앟고 그 내부에 **스프레드 연산자**를 통해 `veggie` 변수의 모든 원소를 넣었다.

<br>

### 9.1.3. 함수와 스프레드 연산자

인수들을 원소로 가지는 배열에 스프레드 연산자를 사용하면 함수를 쉽게 호출할 수 있다.

```javascript
// 기존 방식
function doStuff(x, y, z){
    console.log(x+y+z);
}

var args = [0, 1, 2];

// 함수 호출, 인수 전달
doStuff.apply(null, args);

// 스프레드 문법 사용

doStuff(...args);	// 3 (0 + 1 + 2);
console.log(args);	// [0, 1, 2]
```

이 예제에서 `doStuff`함수는 3개의 매개변수를 받는다. `doStuff`함수를 호출할 때 `args`배열을 `...args`와 같이 써서 스프레드 연산자와 함께 함수에 전달할 수 있다.

- 굳이 `.apply()` 사용에 의존하지 않아도 된다.

<br>

```javascript
const name = ["TAEKWON" , "OH"];

function greet(first, last){
    console.log(`Hello ${first} ${last}`);
}

greet(...name);		// Hello TAEKWON OH
```

배열의 두 값은 함수의 두 인수에 자동으로 할당된다.

<br>

_지정된 인수보다 더 많은 값을 제공하게 된다면?_

```javascript
const name = ["TAEKWON", "BTS", "OH"];

function greet(first, last){
    console.log(`Hello ${first} ${last}`);
}

greet(...name);		// Hello TAEKWON BTS
```

이 예에서는 배열 내에 **세 개**의 값을 제공했지만 함수에는 두 개의 인수만으로 있으므로 마지막 인수는 **제외**된다.

<br>

### :diamond_shape_with_a_dot_inside: 참고:diamond_shape_with_a_dot_inside:

#### _Function.prototype.apply()_

`apply()` 메서드는 주어진 `this` 값과 배열 (또는 [유사 배열 객체](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide#working_with_array-like_objects)) 로 제공되는 `arguments` 로 함수를 호한다.

- **참고:** 이 함수의 구문은 거의 `call()` 구문과 유사하다. 근본적인 차이점은 `call()` 은 함수에 전달될 **인수 리스트**를 받는데 비해, `apply()` 는 **인수들의 단일 배열**을 받는다는 점입니다.

```javascript
const numbers = [5, 6, 2, 3, 7];

const max = Math.max.apply(null, numbers);

console.log(max);
// expected output: 7

const min = Math.min.apply(null, numbers);

console.log(min);
// expected output: 2
```

#### 구문

```javascript
func.apply(thisArg, [argsArray])
```

#### 매개변수

- `thisArg`
  - 옵션. `func` 를 호출하는데 제공될 `this` 의 값. `this` 는 메소드에 의해 실제로 보여지는 값이 아닐 수 있음을 유의한다. 메소드가 [non-strict mode](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Strict_mode) 코드의 함수일 경우, `null` 과 `undefined`가 전역 객체로 대체되며, 기본 값은 제한됩니다.
  - 즉, 현재 객체로 사용될 객체

- `argsArray`
  - 옵션. `func`이 호출되어야 하는 인수를 지정하는 유사 배열 객체, 함수에 제공된 인수가 없을 경우 `null`또는 `undefined`. 
  - ECMAScript 5 의 시작으로 이러한 인수들은 배열 대신 제네릭 유사 배열 객체로 사용될 수 있습니다.
  - 함수에 전달될 인수 집합

<br>

### 9.1.4. 객체 리터럴과 스프레드(ES2018)

 `ES2018`에 도입된 객체에 대한 스프레드 연산자

```javascript
let person = {
    name : "TAEKWON",
    surname : "OH",
    age : 30,
};

let clone = {...person};

console.log(clone);	// {name: 'TAEKWON', surname: 'OH', age: 30}
```

<br>

<br>

### :page_facing_up: 9.2. 레스트 매개변수

----

**레스트(rest)** 문법은 점 3개로 이뤄졌다는 점에서 스프레드 문법과 똑같지만 기능적으로 그 반대이다. `스프레드`는 배열을 **'확장'** 하는 반면, `레스트`는 여러 원소를 하나의 원소로 **'압축'**한다.

```javascript
const runners = ["Tom", "Paul", "Mark", "Luke"];
const [first, second, ...losers] = runners;

console.log(...losers);		// Mark Luke
console.log(first);			// Tom
console.log(second);		// Paul
```

처음 두 값은 **first**와 **second** 변수에 저장하고, 나머지 원소는 `레스트`연산자를 사용하여 **losers** 변수에 배열로 담았다. 마지막에는 이 배열을 스프레드 연산자로 풀어서 `console.log()`로 넘겼다.
