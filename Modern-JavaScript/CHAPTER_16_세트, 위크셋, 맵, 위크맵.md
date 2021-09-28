#  CHAPTER 16

###  :pencil: ***세트, 위크셋, 맵, 위크맵***

<br>

<br>

### :page_facing_up: 16.1. 세트

---

**세트(집합, set)** 란 어떠한 자료형의 값이든 각 원소를 **고유하게** 저장하는 객체이다.

```javascript
// 1.세트 생성
const family = new Set();

// 2.세트에 값 추가
family.add("Dad");
console.log(family);		// Set(1) {'Dad'}

// 2-1.
family.add("Mom");			
console.log(family);		// Set(2) {'Dad', 'Mom'}

// 2-2.
family.add("Son");
console.log(family);		// Set(3) {'Dad', 'Mom', 'Son'}

// 2-3. Dad 다시 추가
family.add("Dad");
console.log(family)			// Set(3) {'Dad', 'Mom', 'Son'}

family.keys();				// SetIterator {'Dad', 'Mom', 'Son'}
```

`2-3. `에서 마지막 부분에서 `"Dad"`를 다시 추가하려고 헀지만, `Set`은 고유한 값만 가질 수 있기 때문에 동일하게 유지됨을 볼 수 있다.

또한 `Set`에는 키가 없기 때문에 `.keys()`를 호출하면 `.values()`또는 `.entries()`를 호출하는 것과 동일한 결과를 얻는다.

<br>

##### `Set`에 관한 메서드

```javascript
family.size;		// 3
family.keys();		// SetIterator {'Dad', 'Mom', 'Son'}
family.entries();	// SetIterator {'Dad' => 'Dad', 'Mom' => 'Mom', 'Son' => 'Son'}
family.values();	// SetIterator {'Dad', 'Mom', 'Son'}
family.delete("Dad");
family;				// Set(2) {'Mom', 'Son'}
family.clear;
family;				// Set(0) {size: 0}
```

`Set`에는 **size** 속성이 있으면 **delete** 를 사용해서 하나의 원소를 삭제하거나 **clear**를 사용하여 모든 원소를 삭제할 수 있다.

또한 `Set`에는 키가 없기 때문에 `.keys()`를 호출하면 `.values()` 또는 `.entries()`를 호출하는 것과 동일한 결과를 얻는다.

<br>

### 16.1.1. `Set`에 대한 루프

`.next()`를 사용하거나 `for of` 루프를 사용하는 두 가지 방법으로 `Set`에 대해 **반복**할 수 있다.

```javascript
// .next() 사용
const iterator = family.values();
iterator.next();		// {value: 'Dad', done: false}
iterator.next();		// {value: 'Mom', done: false}

// for of 루프 사용
for(const person of family){
    console.log(person);
}
// Dad
// Mom
// Son
```

`values()` 메서드는 제너레이터 함수와 비슷하게 `next()`를 호출할 수 있는 `iterator` 객체를 반환한다.

<br>

### 16.1.2. 배열에서 중복 제거하기

고유한 값만 보유할 수 있는 `Set`의 특징을 이용하여 배열에서 중복을 제거할 수 있다.

```javascript
const myArray = ["dad", "mom", "son", "dad", "mom", "daughter"];

const set = new Set(myArray);
console.log(set)			// Set(4) {'dad', 'mom', 'son', 'daughter'}

// Set 를 Array로 변환
const uniqueArray = Array.from(set);
console.log(uniqueArray);	// (4) ['dad', 'mom', 'son', 'daughter']

// 동일 내용을 한 줄로 작성 가능
const uniqueArray = Array.from(new Set(myArray));
console.log(uniqueArray);	// (4) ['dad', 'mom', 'son', 'daughter']
```

결과를 보면 새로운 배열에는 원래 배열의 고유한 원소만 포함한다.

<br>

<br>

### :page_facing_up: 16.2. 위크셋

---

**위크셋(weakSet2)** 은 세트와 유사하지만 **객체**만 **포함**할 수 있다.

```javascript
let dad = {name : "Daddy", age : 50};
let mom = {name : "Mummy", age : 45};

const family = new WeakSet([dad,mom]);

for(const person of family){
    console.log(person);
}
// Uncaught TypeError: family is not iterable
```

`WeakSet`은 이터러블이 아니다. 이 예제처럼 `WeakSet`에 대해 `for of` 루프를 사용하려고 하면 작동하지 않는 것을 확인할 수 있다.

`WeakSet`이 포함하는 객체가 **가비지 컬렉터(garbage collector)** 에 의해 삭제되면 해당 객체는 `WeakSet`에서도 자동으로 삭제된다.

```javascript
let dad = {name : "Daddy", age : 50};
let mom = {name : "Mummy", age : 45};

const family = new WeakSet([dad, mom]);

dad = null;
console.log(family);	// WeakSet {{…}, {…}}

// 몇십 초 정도 기다린 후 다음을 실행하자.
console.log(family);	// WeakSet {{…}}
```

브라우저 콘솔에서 이 예제를 실행하면, `dad = null`이 실행되고 얼마 후에 가비지 컬렉터가 실행되어 `family`에서 `dad` 객체가 제거된 것을 볼 수 있다. 

이는 `dad`를 `null`로 설정했을 때 참조가 손실되었기 때문이다.

<br>

<br>

### :page_facing_up: 16.3. 맵

---

**맵(map)** 은 `Set`와 유사하지만 `키/값` 쌍으로 이루어진다.

```javascript
const family = new Map();

family.set("Dad", 40);
family.set("Mom", 50);
family.set("Son", 20);

family;			// Map(3) {'Dad' => 40, 'Mom' => 50, 'Son' => 20}

family.size;	// 3

family.forEach((val,key)=>console.log(key,val));
// Dad 40
// Mom 50
// Son 20
```

`Set`은 `for of` 루프로만 반복할 수 있지만, `Map`은 반복을 위해 `for of` 루프와 `forEach` 함수 둘다 사용할 수 있다.

<br>

<br>


