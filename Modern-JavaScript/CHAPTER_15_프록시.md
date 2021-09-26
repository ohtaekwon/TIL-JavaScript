#  CHAPTER 15

###  :pencil: ***프록시***

***프록시 (Proxy)란?***

**프록시** 는 객체의 **속성 접근, 속성 할당, 순회, 함수 호출** 등 객체의 기본적인 동작의 새로운 행동을 정의할 때 사용한다.

**proxy**를 사용하게 되면 기존 객체를 래핑하고 객체의 속성이나 메서드 에 접근하는 어떤 것이든 언터셉트 를 할 수 있다.

- **심지어 사전에 정의된 속성이 아니여도 가능하다.!!** 
- 또한 **Vue 3** 부터는`Object.defineProperty` 이 아닌 `proxy` 로 작업되고 있다.

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
        return target[breed].toUpperCase();	// 대문자 변경
    },
    set(target,breed,value){
        console.log("changing breed to...");
        target[breed] = value;
    },
});

console.log(dogProxy.breed);
// GERMAN SHEPHARD

console.log(dogProxy.breed = "Labrador");
// changing breed to...
// Labrador

console.log(dogProxy.breed);
// LABRADOR
```

- `get`메서드를 호출할 때 정상적인 실행 흐름에 끼어들어서 `breed`의 값을 대문자로 변경했다.
- `set` 메서드로 새 값을 설정할 때도 다시 끼어들어서 값을 설정하기 전에 짧은 메시지를 출력했다.

<br>

