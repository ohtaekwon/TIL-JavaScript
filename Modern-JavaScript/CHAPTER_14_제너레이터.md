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
