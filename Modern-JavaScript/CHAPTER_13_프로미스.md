#  CHAPTER 13

###  :pencil: ***프로미스***

자바스크립트는 **동기적(synchronous)** 으로 작동한다. 즉, 각 코드 블록이 이전 블록 이후에 실행된다.

```javascript
const data = fetch('your-api-url-goes-here');
console.log('Finnished');	// Finnished
console.log(data);		// undefined
```

여기서 `fetch`를 사용하여 어떤 URL에서 데이터를 가져온다.

동기 코드의 경우, `fetch`작업이 실제로 완료된 후에 다음 행이 호출되라고 예상한다. 

하지만, 실제로는 `fetch`가 호출된 직후 바로 다음 행에 있는 두 `console.log()`도 실행되므로, 마지막 `console.log(data)`는 **undefined**를 출력한다.

이러한 현상이 발생하는 이유는 `fetch`가 **비동기적(asynchronius)**으로 수행되기 때문이다.

- 즉, 해당 행에서 `fetch`가 완료될 때까지 코드 실행을 중지하는 게 아니라 계속해서 다음 행을 실행한다.

이 문제를 해결하기 위해 **콜백** 또는 **프로미스**를 사용하면 `fetch`가 무언가를 반환하는 시점까지 기다리게 할 수 있다.

<br>

<br>

### :page_facing_up: 13.1. 콜백 지옥

---

비동기 코드를 동기식으로 작동하는 것처럼 하기 위해 **콜백(callback)** 으로 여러 코드 블록을 차례로 연결해 작성할 때 발생하는 상황을 **콜백 지옥(callback hell)** 이라고 부른다.

다시 말하자면,

`A`를 하고, `A`가 완료될 때까지 기다렸다가 `B`를 수행하고, `B`가 완료될 때까지 기다렸다가 `C`를 수행하고, 이러한 방식으로 계속한다.

이런 코드에서는 기다리는 사람마다 콜백을 사용해야 하기 때문에 코드가 복잡해진다.

<br>

#### _ex) 콜백 지옥_

피자를 준비하는 각 단계마다 서버에 요청을 보내야 하고 서버가 응답할 때까지 기다렸다가 다음 단계를 수행해야 하는 비동기적인 상황이다.

```javascript
const makePizza = (ingredients, callback) => {
    mixIngredients(ingredients, function(mixIngredients)){
      bakePizza(mixedIngredients, function(backedPizza)){
        console.log('finished');
    }
  }
};
```

이렇게 하면 시각적으로 위에서 아래로 코드가 실행되는 것처럼 보이게 작성할 수는 있지만, 그것 때문에 과도한 **함수 중첩**을 유발한다.

- 콜백 지옥을 개선하는 방법 : https://callbackhell.com  을 참고

<br>

<br>

### :page_facing_up: 13.2. 프로미스

---

MDN에서는 **프로미스(promise)** 를 다음과 같이 정의한다.

​	프로미스는 비동기적 작업의 최종 성공 또는 실패를 나타내는 객체이다.

```javascript
const myPromise = new Promise((resolve, reject)=>{
    // 여기에 코드를 작성
});
```

이런 방식으로 프로미스를 만든 후, 프로미스의 성공을 알리기 위해서는 `resolve`를,

실패를 알리기 위해서는 `reject`를 호출하면 된다.

<br>

프로미스 안에서 즉시 `resolve`를 호출하면 어떤 값이 반환될까?

```javascript
const myPromise = new Promise((resolve, reject) =>{
   resolve("The value we get from the promise"); 
});

myPromise.then(
	data =>{
        console.log(data);
    });
// The value we get from the promise
```

`resolve` 함수의 첫 번째 매개변수로 전달된 값이 콘솔에 출려고디는 것을 확인할 수 있다.

`setTimeout()`을 사용하면 `resolve`가 호출되기 전까지 일정 시간을 기다릴 수 있다.

```javascript
const myPromise = new Promise((resolve, reject)=>{
   setTimeout(()=>{
       resolve("The value we get from the promise");
   }, 3000); 
});

myPromise.then(
	data => {
    	console.log(data);
});

// 3초가 지난 후에 
// The value we get from the promise
```

이처럼 프로미스는 많은 비동기 코드를 수행할 때 유용하다.

위의 예시처럼 간단하게 `resolve`를 호출하여 프로미스가 성공하는 경우만 살폈지만 실제로도 오류가 발생하므로, `reject`를 이용한 오류 처리 방법도 살펴보자.

```javascript
const myPromise = new Promise((resolve, reject)=>{
   setTimeout(()=>{
       reject(new Error("this is our Error"));
   }, 3000); 
});

myPromise
// 프로미스가 성공할 때의 값을 얻을 때
    .then(data =>{
    console.log(data);
})
// 프로미스가 실패할 때의 오류를 처리
	.catch(err => {
    console.error(err);
});

/* 
	Error: this is our Error
    at <anonymous>:3:15 
    (익명) @ VM373:12
	Promise.catch(비동기)
	(익명) @ VM373:11
*/
```

- 프로미스가 성공할 때의 값을 얻는 데에 `.then()`을 사용하고,

- 프로미스가 실패할 때의 오류를 처리하는 데에는 `.catch()`를 사용한다.

출력된 오류 로그를 보면 오류가 발생한 위치를 알 수 있다. 단순히 `reject("this is our Error");`라고 작성하지 않고 `reject(new Error("this is our Error"));`라고 작성했기 때문이다.

<br>

<br>

### :page_facing_up: 13.3. 프로미스 체이닝

---

프로미스의 성공 또는 실패 여부와 무관하게 이전 프로미스에서 반환된 것을 후속 프로미스의 기반으로 사용하여 프로미스를 계속 **체이닝(연결, chainning)** 할 수 있다.

원하는 만큼 많은 프로미스를 연결할 수 있으며, 그 코드는  콜백 지옥의 코드보다 더 읽기 쉽고 간결하다.

```javascript
const myPromise = new Promise((resolve, reject)=>{
    resolve();
});

myPromise
    .then(data => {
    // 새로운 값을 반환
    return 'working...';
})
	.then(data => {
    // 이전 프로미스에서 받은 값을 출력
    console.log(data);
    throw 'failed';
})
	.catch(err => {
    // 프로미스 수행 중 발생한 오류를 받아서 출력
    console.error(err);
    // failed!
});
```

첫 번째, `.then()`이 두 번째 `.then()`으로 값을 전달하여 해당 값이 로그로 출력되었고,
두 번째, `.then()` 에서 발생시킨 오류는 `.catch()` 절로 전달 되어서 오류 로그가 출력되었다.

프로미스가 성공한 경우뿐만 아니라 실패한 경우에도 연쇄적으로 연결하여 사용하는 것이 가능하다.

```javascript
const myPromise = new Promise((resolve, reject)=>{
    resolve();
});

myPromise
	.then(data=>{
    	throw new Error("ooops");
    	console.log("first value");
})
	.catch(()=>{
    	console.log("catched an error");
})
	.then(data=>{
    	console.log("second value");
});
// catched an error
// second value
```

이 코드의 경우 첫 번째 `.then()`에서 오류가 발생했기 때문에 `"first value"`는 출력되지 않고, 
첫 번째 `.catch()`와 마지막 `.then()`을 수행하면서 로그가 출력된다.

<br>

### :diamond_shape_with_a_dot_inside: 참고

# _throw_

`throw`문은 사용자 정의 예외를 발생(throw)할 수 있다. 예외가 발생하면 현재 함수의 실행이 중지되고 (`throw` 이후의 명령문은 실행되지 않는다.)
제어 흐름은 콜스택의 첫 번째 `catch` 블록으로 전달된다. 호출자 함수 사이에 `catch` 블록이 없으면 프로그램이 종료된다.

#### 문법

```javascript
throw expression; 
```

`expression` : 예외를 발생시킬 표현식

<br>

#### 설명

예외를 발생하기 위해 `throw` 문을 사용하시오. 예외를 발생시키면 `expression`은 예외 값을 지정합니다. 다음 각각은 예외를 발생시킵니다:

```javascript
throw 'Error2'; // 문자열 값을 가지는 예외가 발생합니다.
throw 42;       // 42 값을 가진 예외가 발생합니다.
throw true;     // true 값을 가지는 예외가 발생합니다.
```

<br>

<br>
