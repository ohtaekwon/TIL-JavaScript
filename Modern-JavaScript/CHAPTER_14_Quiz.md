#  CHAPTER_14_Quiz

###  :pencil: ***제너레이터***

<br>

---

<br>

### 14.1. 제너레이터 함수의 올바른 문법은? 답 : 3

`1.`  `generator function(){....}`

`2.`  `new generator(){...}`

`3.`  `function*(){...}`

<br>

---

<br>

### 14.2. 제너레이터의 주요 특징은 무엇인가? 답 : 4

`1.`  실행을 멈출 수 없다.

`2.`  다른 함수들을 생성할 수 있다.

`3.`  덮어 쓰는 것이 불가능하다.

`4.`  실행을 멈추거나 재시작할 수 있다.

<br>

#### 풀이

***제너레이터란?***

**제너레이터(generator)** 함수는 원하는 만큼 <u>코드 실행을 시작하거나 중지할 수 있는 함수이다.</u>
중지된 제너레이터 함수를 다시 시작할 때 데이터를 추가로 전달하면서 재시작할 수 있다.

<br>

---

<br>

### 14.3. 다음 코드의 올바른 출력은? 답 : 4

```javascript
function* fruitList(){
    yield 'Banana';
    yield 'Apple';
    yield 'Pomelo';
    yield 'Mangosteen';
    yield 'Orange';
}

const fruits = fruitList();
fruits.next();
fruits.next();
fruits.next();
```

`1.`  `{value : 'Banna', done : false}`

`2.`  `{value : "Pomelo", done : true}`

`3.`  `{value : "Magosteen", done : false}`

`4.`  `{value : "Pomelo", done : false}`

<br>

#### 풀이

- `function*`을 사용하여 함수를 선언한다.
  - `fruitList()`
- 반환할 콘텐츠 앞에 `yield` 키워드를 사용한다.
- `.next()`를 사용하여 함수의 실행을 시작한다.
- 만약 `.next()`를 호출이 마지막이라면,  **undefined** 값과 **done : true**의 값이 반환된다.
- 그렇지 않은 경우, **done : false** 가 된다.

<br>

---

<br>

### 14.4. 다음 코드의 올바른 출력은? 답 : 4

```javascript
function* fruitList(){
    yield 'Banana';
    yield 'Apple';
    yield 'Orange';
}

const fruits = fruitList();
fruits.return();
```

`1.`  `{value : 'Banana', done : true}`

`2.`  `{value : undefined, done : false}`

`3.`  `{value : "Banana", done : false}`

`4.`  `{value : undefined, done : true}`

<br>

#### 풀이

`.return()` 을 사용하여 주어진 값을 반환하고 제너레이터를 종료할 수 있다.

```javascript
function* fruitList(){
    yield 'Banana';
    yield 'Apple';
    yield 'Orange';
}

const fruits = fruitList();
fruits.return();			// {value: undefined, done: true}
```

만약 일부 출력을 한 후에 `.return()`을 사용한다면?

```javascript
function* fruitList(){
    yield 'Banana';
    yield 'Apple';
    yield 'Orange';
}

const fruits = fruitList();
fruits.next();		// {value: 'Banana', done: false}
fruits.return();	// {value: undefined, done: true}
```

