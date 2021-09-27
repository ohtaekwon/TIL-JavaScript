#  CHAPTER 15

###  :pencil: ***프록시***

<br>

들어가기전...

## 프록시 (Proxy)

**프록시** 는 객체의 **속성 접근, 속성 할당, 순회, 함수 호출** 등 객체의 기본적인 동작의 새로운 행동을 정의할 때 사용한다.

**proxy**를 사용하게 되면 기존 객체를 래핑하고 객체의 속성이나 메서드 에 접근하는 어떤 것이든 언터셉트 를 할 수 있다.

- **심지어 사전에 정의된 속성이 아니여도 가능하다.!!** 
- 또한 **Vue 3** 부터는`Object.defineProperty` 이 아닌 `proxy` 로 작업되고 있다.

<br>

## 사용방법

```javascript
new Proxy(target, handler);
```

**target** 은 **proxy**로 래핑할 객체를 넣어준다. 기본객체가 될수도 있고 **proxy**를 넣어줄 수도 있습니다. 

**handler** 는 객체의 기본적인 동작(접근, 할당, 순회 등등) 의 작업이 수행될때 **Proxy**의 동작을 정의하는 함수 객체를 넣어줍니다. 여기서 지정가능한 함수 객체는 13개로 다음과 같습니다.

<br>

## handler 정의 함수

- get
- set
- has
- defineProperty
- deleteProperty
- construct
- apply
- getPrototypeOf
- setPrototypeOf
- isExtensible
- preventExtensions
- getOwnPropertyDescriptor
- ownKeys

<br>
물론 이것은 다음과 같이 `세터`의 이름을 다른 이름으로 변경하여 얻을 수 있는 효과와 동일하다.

```javascript
set rename(newName){
    this.name = newName;
}
```

<br>

`name`과 `age`라는 두 가지 속성이 있으며 각각에 대해 `게터`와 `세터`를 만들어야 했다.

여기서 `breed`와 같이 객체에 존재하지 않는 속성에 접근하려고 하면 `undefined`가 반환된다.

```javascript
const dog = {
    name : 'pup',
    age : 7,
};

const handler = {
    get : (target, property) => {
        property in target ? console.log(target[property]) : console.log('property not found');
    },
    set : (target, property, value) => {
        target[property] = value;
        console.log(target[property]);
    },
};

const dogProxy = new Proxy(dog, handler);

dogProxy.name;			// pup
dogProxy.age;			// 7
dogProxy.name = 'Max';	// 'Max'
dogProxy.age = 8;		// 8
dogProxy.breed; 		// property not found
```

`dog` 객체를 만들었지만 객체 내부에 `게터`와 `세터`를 따로 정의하지 않았다. 대신, 하나의 `게터`와 `세터`로 모든 속성을 처리할 수 있게 `handler`를 만들었다.

- `게터`는 객체와 속성 두 인수를 받아 **해당 객체에 해당 속성이 존재하는지 확인** 하고, 존재하지 않으면 사용자가 지정한 메시지를 출력한다.

- `세터`는 세 인수(`target, property, value`) 를 받는다.
  - 여기에 특별한 부분은 없지만, 속성을 새 값으로 설정하고 출력한다.

<br>

이와 같이 프록시를 사용하여 **더 짧고 깔끔한 코드** 와 **사용할 수 없는 속성에 접근할 때 사용자 지정 메시지를 출력** 하는 두가지를 얻을 수 있다.
>>>>>>> fa8ac57c6ccb1485e932e41233d88e28d0cb2d82

<br>

<br>

### :page_facing_up: 15.1. 프록시

---

MDN에서는 **프록시(proxy)** 를 다음과 같이 정의한다.

​	프록시(Proxy) 객체는 기본 작업(예 : 속성 조회, 할당, 열거, 함수 호출 등)에 대해 사용자 지정 동작을 추가로 정의하는데 사용된다.

<br>

<br>
