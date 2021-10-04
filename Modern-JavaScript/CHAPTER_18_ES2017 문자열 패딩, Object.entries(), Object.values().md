#  CHAPTER 18

###  :pencil: ***ES2017 : 문자열 패딩, Object.entries(), Object.values()***

`ES2017`에서는 많은 기능들이 추가 되었다.

<br>

### :page_facing_up: 18.1. 문자열 패딩

---

문자열 끝 부분 또는 시작 부분에 **패딩(padding)** 을 추가할 수 있다. 각각 `padEnd()`와 `padStart()` 를 쓴다.

```javascript
"hello".padStart(6);	// ' hello'

"hello".padEnd(6);	// 'hello '
```

여기서 패딩으로 `6`을 지정했는데 두 경우 모두 `1`개의 공간만 확보된 이유는 무엇인가?

- `"hello"`는 5글자이고 패딩은 `6` 으로 지정되었기 때문에 빈 공간이 `1`개만 남는다.
- `"hello".padStart(6);` 에서는 시작부분에 빈 공간 1개 채워 넣게 된다.
- `"hello".padEnd(6);` 에서는 마지막 부분에 빈 공간 1개 채워 넣게 된다.

<br>

```javascript
// 10 - 2 = 8 스페이스
"hi".padStart(10);			// '        hi'

// 10 - 6 = 4스페이스
"welcome".padStart(10);		// '   welcome'
```

<br>

### 18.1.1. padStart()와 오른쪽 정렬

문자열을 오른쪽 정렬하고 싶을 때 `padStart()`를 활용할 수 있다.

```javascript
const strings = ["short", "medium length", "very long string"];

const longestString = strings.sort(str => str.length).map(str => str.length)[0];

console.log(longestString); // 5

strings.forEach(str => console.log(str.padStart(longestString)));
// short
// medium length
// very long string
```

- `string.sort(str => str.length)` : 먼저 가장 긴 문자열을 찾아서 그 길이를 측정했다.

- 그런 다음 가장 긴 문자열의 길이를 기준으로 모든 문자열에 `padStart()`를 적용하면 모든 문자열을 완벽하게 오른쪽으로 정렬할 수 있다.

<br>

### 18.1.2. 패딩에 사용자 지정 값 추가

패딩은 공백을 추가하는 것뿐만 아니라 문자열이나 숫자를 덧붙이는 데에도 사용할 수 있다.

```javascript
"hello".padEnd(17, " OH TAE KWON");			// 'hello OH TAE KWON'

"1".padStart(3,0);			// '001'

"99".padStart(3,0);			// '099'
```
<br>

<br>

### :page_facing_up: 18.2. Object.entries()와 Object.values()

---

객체 내부의 값에 쉽게 접근하느 방법도 도입되었다. 먼저 다음과 같은 객체를 생성한다.

```javascript
const family = {
    father : "BTS",
    mother : "IU",
    son : "AKAMU",
};
```

이전 버전의 자바스크립트에서는 다음과 같은 방법으로 객체 내부의 값에 접근했다.

```javascript
Object.keys(family);	// (3) ['father', 'mother', 'son']

family.father;			// 'BTS'
```

즉 `Object.keys()`는 객체의 키만 반환하기 때문에, 값에 접근하기 위해서는 해당 키를 먼저 얻은 다음 그 키를 통해 값에 접근해야 했다.

<br>

##### `ES2017`에서 새롭게 도입된 객체에 접근 방법

```javascript
Object.values(family);			// (3) ['BTS', 'IU', 'AKAMU']

Object.entries(family);
/* 
  [
	["father", "BTS"],
	["mother", "IU"],
	["son", "AKAMU"]
  ]
*/
```

`Object.values()`는 **모든 값이 담긴 배열**을 반환하고, `Object.entries()`는 **키와 값**을 모두 포함하는 배열의 배열을 반환한다.

<br>

<br>

### :page_facing_up: 18.3. Object.entries()와 Object.values()

---

이 메서드는 객체가 소유한 **모든 속성 설명자**를 반환한다. 

- 속성의 **value, writable, get, set, configurable, enumberable** 등을 반환한다.

```javascript
const myObj ={
    name : "OHTAEKWON",
    age : 25,
    greet(){
        console.log("hello");
    },
};
Object.getOwnPropertyDescriptors(myObj);
// age: {value: 25, writable: true, enumerable: true, configurable: true}

// greet: {writable: true, enumerable: true, configurable: true, value: ƒ}

// name: {value: 'OHTAEKWON', writable: true, enumerable: true, configurable: true}

```

<br>

<br>

### :page_facing_up: 18.4. 후행 쉼표

---

**후행 쉼표(trailing comma)** 는 사소한 문법 변경에 해당한다. 

이제 객체나 함수를 작성할 때 마지막 매개변수인지 여부에 관계없이 각 매개변수 뒤에 **쉼표**를 찍는 것이 허용된다. 

```javascript
// 기존
const object = {
    prop1 : "prop",
    prop2 : "propop"
};

// 후행 쉼표 허용
const object = {
    prop1 : "prop",
    prop2 : "propop",
};
```

두 번째 속성 끝에 쉼표를 작성하였다. 단, 쉼표를 넣지 않아도 오류가 발생하는 것은 아니다.

하지만 **속성을 추가하거나 변경할 때 실수를 줄이기 위해서 넣는 것이 좋다.**

```javascript
// 내가 작성한 코드
const object = {
    prop1 : "prop",
    prop2 : "propop"
};

// 같이 개발하는 동류가 새로운 속성을 추가
const object = {
    prop1 : "prop",
    prop2 : "propop"
    prop3 : "propopop"
};

// prop2에 후행 쉼표가 없었기 때문에
// 새 속성 prop3를 추가할 때 실수로 위와 같이 잘못된 코드를 작성할 수 있다.
```

<br>

<br>

### :page_facing_up: 18.5. 어토믹스

---

자바스크립트는 기본적으로 웹 브라우저 위에 단일 스레드로 동작하지만, `HTML5 웹 워커(Web worker) API` 도입으로 백그라운드 스레드에서도 코드 실행이 가능해짐에 따라 **멀티 스레드 환경**을 지원하기 위해 공유 메모리 모델과 **어토믹스(atomics)** 가 도입되었다.

**MDN**에서는 어토믹스에 대해 다음과 같이 정의한다.

​	메모리가 공유되면 여러 스레드가 메모리에서 동일한 데이터를 읽고 쓸 수 있다. **Atomics** 를 이용한 작업은 이러한 환경에서도 정확하게 값을 읽고 쓸 수 있게 해준다. 또, **Atomics** 를 이용한 작업은 다음 작업이 시작되기 전에 완료되고, **중단(interrupt)** 되지 않는 것이 보장된다.

​	**Atomics** 는 생성자가 아니며 **Atomics** 의 모든 속성과 메서드는 **정적(static)** 이므로(예를 들어 **Math** 클래스와 마찬기지로), **Atomics**를 `new`연산자와 함께 사용하거나 함수 형태로 호출할 수는 없다.

#### _Atomics의 메서드 중 일부는 다음과 같다._

- `add` / `sub
- `and` / `or` / `xor`
- `load` / `store`

**Atomics**는 범용 고정 길이 바이너리 데이터 버퍼를 표현하는 `SharedArrayBuffer` 객체와 함꼐 사용된다.

<br>

### 18.5.1 Atomics.add(), Atomics.sub(), Atomics.load(), Atomics.store()

**Atomics.add()**는 호출 시에 3개의 인수, 즉 배열, 인덱스, 값을 인수로 받고, 더허가리르 수행하기 전에 해당 인덱스에 존재하던 이전 값을 반환한다.

```javascript
// SharedArrayBuffer를 생성
const buffer = new SharedArrayBuffer(16);

const uint8 = new Unit8Array(buffer);

// 0번 인덱스에 값을 추가
uint8[0] = 10;

console.log(Atomics.add(uint8, 0, 5));


// 10 + 5 = 15
console.log(uint8[0])

console.log(Atomics.load)
```

보다시피 `Atomics.add()`를 호출하면 해당 배열 인덱스에 존재하던 이전 값이 반환된다. 

`unit8[0]`을 넣어 `console.log()`를 다시 호출하면 더하기를 수행한 결과인 `15`를 반환한다.

배열에서 특정 값을 가져오기 위해서는 `Atomics.load()`에 배열과 인덱스를 인수로 전달하면 된다.

`Atomics.sub()` 는 `Atomics.add()` 와 같은 방식으로 동작하지만 값을 뺀다.

```javascript
// SharedArrayBuffer를 생성
const buffer = new SharedArrayBuffer(16);

const uint8 = new Uint8Array(buffer);

// 0번 인덱스에 값을 추가
uint8[0] = 10;

consoloe.log(Atomics.sub(uint8, 0, 5));		// 10

// 10 - 5 = 5
console.log(uint8[0])

// 5
console.log(Atomics.store(uint8, 0, 3));

// 3
console.log(Atomics.load(uint8,0))
```


