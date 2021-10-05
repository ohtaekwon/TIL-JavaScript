#  CHAPTER_19_Quiz

###  :pencil: ***ES2017: async와 await***

<br>

---

<br>

### 19.1. 다음 코드의 올바른 출력은? 답 : 4

```javascript
function func(){
    let promise = Promise.resolve(1);
    let result = await promise;
}
func();
```

`1.`  1

`2.`  true

`3.`  undefined

`4.`  SyntaxError

<br>

#### 풀이

`ES2016`에서는 두 가지 기능이 새롭게 도입되었다.

- `Array.prototype.includes()`
- 지수연산자(**)

<br>

---

<br>

### 19.2. 다음 코드의 마지막 출력은? 답 : 3

```javascript
function walk(amount){
    return new Promise((resolve, reject)=>{
        if(amount>500){
            reject ("the value is too big");
        }
        setTimeout(()=> resolve(`you walked for ${amount}ms`), amount);
    });
}

async function go(){
    const res = await walk(500);
    console.log(res);
    
    const res2 = await walk(300);
    console.log(res2);
    
    const res3 = await walk(200);
    console.log(res3);
    
    const res4 = await walk(700);
    console.log(res4);
    
    const res5 = await walk(400);
    console.log(res5);
    console.log("finished");
}

go();
```

`1.`  `"you walked for 700ms"`

`2.`  `"you walked for 400ms"`

`3.`  `uncaught exception : the value is too big`

`4.`  `"finished"`

<br>

#### 풀이



```javascript
// you walked for 500ms
// you walked for 300ms
// you walked for 200ms
// Uncaught (in promise) the value is too big
```

<br>



