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
