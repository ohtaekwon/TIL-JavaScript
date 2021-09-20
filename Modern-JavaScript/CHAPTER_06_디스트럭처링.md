#  CHAPTER 06

###  :pencil: ***디스트럭처링***

<br>

### :page_facing_up: 6.1. 기본적인 문자열 메서드

---

예전에는 객체에서 변수를 생성하려면 다음과 같은 방식으로 코드를 작성했다.

```javascript
var person = {
    first : "TAEKWON",
    last : "OH",
};

var first = person.first;
var last = person.last;

console.log(first);			// TAEKWON
console.log(last);			// OH
```

<br>

`ES6`에서는 더 간결하게 다음과 같은 방법을 사용한다.

```javascript
const person = {
    first : "TaeKwon",
    last : "OH",
};

const {first, last} = person;

console.log(first);			// TaeKwon
console.log(last);			// OH
```

디스트럭처링을 이용하여 `person`이 가진 속성에 접근함과 동시에 해당 속성 이름으로 변수 선언이 가능하다.

다음과 같이 **중첩된 객체 형태**로 데이터가 주어진 경우에도 동일한 방법을 적용할 수 있다.

```javascript
const person = {
    name : "TAEKWON",
    last : "OH",
    links : {
        social : {
            github : "https://github.com/ohtaekwon",
        },
        website : "https://tkolab.tistory.com",
    },
};

const {github} = person.links.social;
```

<br>

변수의 이름을 객체의 속성과 동일하게 지정하는 데 그치지 않고, 다음과 같이 변수 이름을 바꿀 수도 있다.

```javascript
const {github : gh} = person.links.social;
// person.links.social.github 프로퍼티를 찾아 git이라는 변수로 명명한다.
console.log(gh);		// https://github.com/ohtaekwon
console.log(github);	// https://github.com/ohtaekwon
```

이 코드는 `const {github : gh}` 식의 문법을 사용하여 `person.links.social` 객체의 속성 `github`을 대상으로 지정하고 `const` 변수를 `gh`라고 명명한다.

  <br>

다음과 같이 기본값을 전달할 수도 있다.

```javascript
// 변수를 gh로 다시 명명하고 기본값을 설정한다.
const {github : gh = "https://github.com/ohtaekwon"} = person.links.social;
```

<br>

<br>
