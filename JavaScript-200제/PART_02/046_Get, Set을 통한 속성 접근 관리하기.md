# PART 2

###  :pencil: ***입문 046 :  Get, Set을 통한 속성 접근 관리하기***

<br>

객체의 속성에 접근하여 값을 가져오거나 대입할 때 `get` 함수와 `set`함수를 통해 속성 접근을 관리한다.

```javascript
// 1.
let user = {};
Object.defineProperty(user, "age", {
    // 1-1.
    get: function(){
        return this._age;
    },
    // 1-2.
    set: function(age){
        if(age<0){
            console.error('0보다 작은값은 올 수 없습니다.');
        } else {
            this._age = age;
        }
    },
    enumerable:true
});
// 1-3.
user.age=10;						// 10		
console.log(user.age);				// 10
// 1-4.
user.age=-1;						// 0보다 작은값은 올 수 없습니다.

// 2.
let user2 = {
    get name(){
        return this._name;
    },
    set name(val){
        if(val.length < 3){
            throw new Error('3자 이상이어야 합니다.');
        }
        this._name = val;
    }
}
// 2-1.
user2.name = 'TaeKwon';			// 'TaeKwon'
console.log(user2.name);		// TaeKwon
user2.name='OH';				// Uncaught Error: 3자 이상이어야 합니다.
```

- `1.` 속성 기술자를 통해 `user` 객체의 `age`속성을 정의한다. 이때 값에 접근하는 방식을 정의하는 객체를 전달하는데, 이 객체를 **접근 기술자** (**Accessor Descriptor**)라 하고, `get`과 `set`을 메소드로 가진다.
  -  `age` 속성의 접근 기술자의 `get` 메소드는 **속성에 접근**할 때,  `set` 메소드는 **속성에 값을 대입**할 때 호출된다.
- `1-1.` `get` 메소드는 **속성에 접근할 때 호출된다.** 그래서 `user.age`에 접근하면 `user._age`의 결과를 반환한다.
- `1-2.` `set` 메소드는 **속성에 값을 대입할 때 호출된다.** 그래서 `user.age`에 값을 할당할 때 0보다 작은 값을 주면 에러 로그를 출력하고 0보다 큰 값을 주었을 때, `user` 객체의 `_age` 속성에 값을 대입한다.
- `1-3.` `user.age`에 값 10을 대입한다. 
  - 그렇게되면 `age` 속성 접근 기술자의 `set`메소드가 호출되고, `user` 객체의 `_age` 속성에 값 10이 할당된다. 그리고 `user.age` 결과를 콘솔에 출력하는데 이때, 접근 기술자의 `get` 메소드가 호출되면서 `_age` 속성값인 10을 반환한다.
- `1-4.` `user.age`에 값 `-1` 대입한다.
  - **접근 기술자**의 `set`메소드가 호출되면서 *if* (age < 0)에 의해 콘솔에 에러가 출력된다.
- `2.` `user2` 객체를 정의할 때, `name` 속성의 접근 기술자를 정의한다.
  - 객체를 정의할 때 메소드를 정의하는 메소드명 앞에 `get`과 `set`으로 각각의 `get` 메소드와 `set`메소드를 정의할 수 있다.
- `2-1.` `user2` 객체의 `name` 속성에 값을 할당할 때 접근 기술자의 `set`메소드가 호출된다. 마지막 라인에서 `OH`를 할당하면 글자수가 3자 이상이 되지 않아 콘솔에 에러가 출력된다.

---

<br>

:pencil: **참고**

속성 이름에 `_`를 붙이는 것은 암묵적으로 **비공개** (Private) 속성임을 나타낸다. 자바스립트 객체는 속성 접근 제한자가 없어서 모든 속성은 **공개** (Public)이다. 그래서 대체로 이름 규칙을 통해 비공개를 나타낸다.



