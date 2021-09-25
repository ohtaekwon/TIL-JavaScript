#  CHAPTER_13_Quiz

###  :pencil: ***프로미스***

<br>

---

<br>

### 13.1. 프로미스란? 답 : 2

`1.`  새로운 원시 자료형

`2.`  비동기 작업의 최종 성공 또는 실패를 나타내는 객체

`3.`  새로운 유형의 루프

<br>

#### 풀이

***프로미스란?***

MDN에서는 **프로미스(promise)** 를 다음과 같이 정의한다.

​	프로미스는 비동기적 작업의 최종 성공 또는 실패를 나타내는 객체이다.

<br>

---

<br>

### 13.2. 다음 작업을 수행하는 코드를 작성하자.

#### 즉시 성공 처리되어 콘솔에 무언가를 출력하는 간단한 프로미스를 작성하시오.

#### _풀이_

```javascript
const myPromise = new Promise((resolve, reject)=>{
    resolve("성공입니다.");
});

myPromise.then(data =>{
    console.log(data);
});
// 성공입니다.
```

<br>

---

<br>

### 13.3. 다음 프로미스 메서드 중 존재하지 않는 것은? 답 : 2

`1.`  `Promise.race()`

`2.`  `Promise.some()`

`3.`  `Promise.all()`

`4.`  `Promise.reject()`

<br>

#### 풀이

- `Promise.race()` 는  이터러블에 포함된 프로미스들 중 가장 먼저 성공 또는 실패한 결과를 반환한다.

```javascript
const promise1 = new Promise((resolve, reject)=>{
    setTimeout(resolve, 500, 'first value');
});
const promise2 = new Promise((resolve, reject)=>{
    setTimeout(resolve, 1000, 'second value');
});

Promise.race([promise1, promise2]).then(function(value){
    console.log(value);
    // 둘 다 성공하지만 promise1이 더 빨리 성공
});

// first value
```

<br>

- `Promise.all()`은 모든 프로미스가 성공할 경우에만 성공하는 하나의 프로미스를 반환한다.

```javascript
const promise1 = new Promise((resolve, reject) => {
    setTimeout(resolve, 500, 'frist value');
});
const promise2  = new Promise((resolve, reject) => {
    setTimeout(resolve, 1000, 'second value');
});

Promise
	.all([promise1, promise2])
	.then(data=>{
    const [promise1data, promise2data] = data;
    console.log(promise1data, promise2data);
});

// 1000ms 후
// frist value second value
```

<br>

-  `Promise.reject()` 는 프로미스를 즉시 실패하게 하는 메서드이다.

```javascript
// Promise.reject()
Promise.reject(new Error('fail')).then(function(){
    // not called
}, function(error){
    console.log(error);
    // Error : fail
});
```

<br>

---

<br>

### 13.4. 다음 코드의 올바른 출력은?

```javascript
function myPromise(){
    return new Promise((resolve, reject) => {
        reject();
    });
}

myPromise().then(()=>{
    console.log('1');
})
.then(()=>{
    console.log('2');
})
.catch(()=>{
    console.log('3');
})
.then(()=>{
    console.log('4');
});

// 3
// 4
```

`1.`  1, 2, 3, 4

`2.`  2, 3, 1, 2

`3.`  3, 4

`4.`  4

<br>

#### 풀이

```javascript
function myPromise(){
    return new Promise((resolve, reject) => {
        reject();
    });
}
```

위의 함수를 보면 `reject()`를 사용함으로써 실패하는 프로미스를 생성하도록 한다.

```javascript
myPromise().then(()=>{
    console.log('1');
})
.then(()=>{
    console.log('2');
})
.catch(()=>{
    console.log('3');
})
.then(()=>{
    console.log('4');
});
```

따라서 세 번째 `.catch()`부터 시작하여 마지막 `.then()`을 수행하면서 로그가 출력된다.

 <br>

#### 반대로 `reject()`대신 `resolve()`를 적용한다면?

```javascript
function myPromise(){
    return new Promise((resolve, reject) => {
        resolve();
    });
}

myPromise().then(()=>{
    console.log('1');
})
.then(()=>{
    console.log('2');
})
.catch(()=>{
    console.log('3');
})
.then(()=>{
    console.log('4');
});

// 1
// 2
// 4
```

