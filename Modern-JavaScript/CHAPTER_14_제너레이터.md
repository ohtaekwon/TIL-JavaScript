#  CHAPTER 14

###  :pencil: ***제너레이터***

<br>

### :page_facing_up: 14.1. 제너레이터

----

**제너레이터(generator)** 함수는 원하는 만큼 <u>코드 실행을 시작하거나 중지할 수 있는 함수이다.</u>
중지된 제너레이터 함수를 다시 시작할 때 데이터를 추가로 전달하면서 재시작할 수 있다.

```javascript
function* fruitList(){
    yield 'Banana';
    yield 'Apple';
    yield 'Orange';
}

const fruits = fruitList();

// 제너레이터
fruits.next();	// {value: 'Banana', done: false}
fruit.next();	// {value: 'Apple', done: false}
fruit.next();	// {value: 'Orange', done: false}
fruit.next();	// {value: undefined, done: true}
```

- `function*`을 사용하여 함수를 선언한다.
- 반환할 콘텐츠 앞에 `yield` 키워드를 사용한다.
- `.next()`를 사용하여 함수의 실행을 시작한다.
- 마지막으로 `.next()`를 호출하면 **undefined**값과 **done : true**가 반환된다.

<br>

<br>

### :page_facing_up: 14.2. 제너레이터를 사용하여 배열 반복하기

----

`for of 루프`를 사용하면 제너레이터에 대해 반복하고 각 루프에서 콘텐츠를 **반환(yield)**을 할 수 있다.

```javascript
// 과일 배열을 생성
const fruitList = ['Banana', 'Apple', 'Orange', 'Melon', 'Cherry', 'Mango'];

// 제너레이터를 생성
function* loop(arr){
    for(const item of arr){
        yield `I like to eat ${item}s`;
    }
}

const fruitGenerator = loop(fruitList);

fruitGenerator.next();			// {value: 'I like to eat Bananas', done: false}
fruitGenerator.next();			// {value: 'I like to eat Apples', done: false}
fruitGenerator.next().value;	// 'I like to eat Oranges'
```

- 새로운 제너레이터는 배열을 반복하고 `.next()`를 호출할 때마다 한 번에 하나의 값을 출력한다.
- 단순히 값만 출력하길 원한다면 `.next().value`를 사용하면 된다.
  - 이렇게 하면 제너레이터의 상태는 출력되지 않는다.

<br>

<br>

### :page_facing_up: 14.3. `.return()` 을 사용하여 제너레이터 종료하기

---

`.return()` 을 사용하여 주어진 값을 반환하고 제너레이터를 종료할 수 있다.

```javascript
function* fruitList(){
    yield 'Banana';
    yield 'Apple';
    yield 'Orange';
}

const fruits = fruitList();

fruits.return();		// {value: undefined, done: true}
```

이 경우 `.return()`에 아무것도 전달하지 않았기 때문에 `value : undefined`를 얻었다.

<br>

<br>
