#  CHAPTER 19

###  :pencil: ***ES2017 : async 와 await***

`ES2017`에서는 `async/await` 키워드를 이용한 새로운 프로미스 작업 방식이 도입되었다.

<br>

### :page_facing_up: 19.1. 프로미스 다시 보기

---

_프로미스를 사용하는 일반적인 방식_

```javascript
// 깃허브에서 사용자 정보 조회
fetch('https://api.github.com/users/AlbertoMontalesi').then(res=>{
    // 응답을 json 형식으로 반환
    return res.json();
}).then(res=>{
    // 성공시 데이터를 출력
    console.log(res);
}).catch(err=>{
    // 실패 시 오류 출력
    console.log(err);
});
```

이것은 깃허브 API로 특정 깃허브 사용자에 대한 정보를 가져와서 콘솔에 출력하는 매우 간단한 프로미스 코드이다.

<br>

```javascript
function walk(amount){
    return new Promise((resolve, reject) => {
        if(amount < 500){
            reject ("the value is too small");
        }
        setTimeout(()=> resolve(`you walked for ${amount}ms`),amount);
    });
}

walk(1000).then(res=>{
    console.log(res);
    return walk(500);
}).then(res=>{
    console.log(res);
    return walk(700);
}).then(res=>{
    console.log(res);
    return walk(800);
}).then(res=>{
    console.log(res);
    return walk(100);
}).then(res=>{
    console.log(res);
    return walk(400);
}).then(res=>{
    console.log(res);
    return walk(600);
});

// you walked for 1000ms
// you walked for 500ms
// you walked for 700ms
// you walked for 800ms
// Uncaught (in promise) the value is too small
```

<br>

<br>

### :page_facing_up: 19.2. async/await

---

```javascript
function walk(amount){
    return new Promise((resolve, reject) => {
        if(amount<500){
            reject ("the value is too small");
        }
        setTimeout(()=>resolve(`you walked for ${amount}ms`), amount)
    });
}

// 비동기 함수 선언
async function go(){
    // 프로미스가 완료될 때까지 기다리기 위해 await 키워드를 사용
    const res = await walk(500);
    console.log(res);
    
    const res2 = await walk(900);
    console.log(res2);
    
    const res3 = await walk(600);
    console.log(res3);
    
    const res4 = await walk(700);
    console.log(res4);
    
    const res5 = await walk(400);
    console.log(res5);
    console.log("finished");
}

go();

// you walked for 500ms
// you walked for 900ms
// you walked for 600ms
// you walked for 700ms
// Uncaught (in promise) the value is too small
```

- 비동기 함수를 만들려면 함수 앞에 `async` 키워드를 넣어야 한다.
- 해당 키워드는 자바스크립트에게 항상 **프로미스**를 반환하도록 지시한다.
- 비동기 함수 내에서 프로미스가 아닌 값을 반환하게 작성하면 자바스크립트가 해당 값을 자동으로 프로미스로 감싼 후에 반환한다.
- `await` 키워드는 비동기 함수 내에서만 작동한다.
- 이름에서 알 수 있듯이 `await` 키워드는 프로미스가 결과를 반환할 때까지 기다리도록 자바스크립트에 지시한다.

<br>

_비동기 함수가 아닌 곳에서 `await`를 사용하려고 한다면?_

```javascript
// 일반 함수에서 await 키워드를 사용한 경우
function func(){
    let promise = Promise.resolve(1);
    let result = await promise;
}
func();
// SyntaxError: await is only valid in async functions and the top level bodies of modules
```

`await` 는 비동기 함수 내에서만 사용할 수 있다.

<br>

<br>

### :page_facing_up: 19.3. 오류 처리

---

일반적인 프로미스에서는 `.catch()` 를 사용하여 프로미스가 반환하는 오류들을 처리한다. `async/await` 문법을 사용할 떄도 크게 다르지 않다.

```javascript
async function asyncFunc(){
    try{
        let response = await fetch('your-url');
    } catch(err){
        console.log(err);
    }
}

asyncFunc();
// TypeError: Failed to fetch
```

보통은 `try..catch` 구문을 사용하여 오류를 처리하지만, 해당 구문 없이도 다음과 같이 오류를 처리할 수 있다.

```javascript
async function asyncFunc(){
    let response = await fetch('your-url');
}
asyncFunc();
// Uncaught (in promise) TypeError: Failed to fetch

asyncFunc().catch(console.log);
// TypeError: Failed to fetch
```
<br>

<br>

### :large_blue_diamond: 참고 :large_blue_diamond:

---

<br>

# 1. Promise.prototype.then()

`then()` 메서드는 `Promise` 를 리턴하고 두 개의 콜백 함수를 인수로 받습니다. 하나는 `Promise`가 **이행**했을 때, 다른 하나는 **거부**했을 때를 위한 콜백 함수이다.

```javascript
const promise1 = new Promise((resolve, reject) => {
  resolve('Success!');
});

promise1.then((value) => {
  console.log(value);
  // expected output: "Success!"
});

```

<br>

### _1.1 구문_

```javascript
p.then(onFulfilled, onRejected);

p.then(function(value) {
  // 이행
}, function(reason) {
  // 거부
});
```

<br>

### _1.2 매개변수_

- **onFulfilled**
  - `Promise`가 수행될 때 호출되는 `Function`으로, **이행 값(fulfillment value)** 하나를 인수로 받습니다.

- **onRejected**
  - `Promise`가 거부될 때 호출되는 `Function`으로, **거부 이유(rejection reason)** 하나를 인수로 받습니다.

<br>

### `then` 메서드 사용

```javascript
var p1 = new Promise(function(resolve, reject) {
  resolve("성공!");
  // 또는
  // reject("오류!");
});

p1.then(function(value) {
  console.log(value); // 성공!
}, function(reason) {
  console.log(reason); // 오류!
});
```



