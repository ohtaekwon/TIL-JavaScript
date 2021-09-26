#  CHAPTER 15

###  :pencil: ***프록시***

<br>

### :page_facing_up: 15.1. 프록시

---

MDN에서는 **프록시(proxy)** 를 다음과 같이 정의한다.

​	프록시(Proxy) 객체는 기본 작업(예 : 속성 조회, 할당, 열거, 함수 호출 등)에 대해 사용자 지정 동작을 추가로 정의하는데 사용된다.

<br>

<br>

### :page_facing_up: 15.2. 프록시 생성

----

프록시를 생성하는 방법

```javascript
var x = new Proxy(target, handler);
```

- `target` 은 객체, 함수, 다른 프록시 등 무엇이든 가능하다.
- `handler`는 작업이 수행될 때 프록시의 동작을 정의하는 객체이다.

<br>

```javascript
// 원본 객체
const dog = {breed: "German Shephard", age: 5};

// 프록시 객체
const dogProxy = new Proxy(dog, {
    get(target, breed){
        return target[breed].toUpper
    }
})
```

