#  CHAPTER 11

###  :pencil: ***심벌***

`ES6`에서 **심벌(Symbol)**이라는 새로운 원시 자료형이 추가되었다.

<br>

### :page_facing_up: 11.1. 심벌의 고유성

---

심벌은 항상 **고유(unique)**하며 객체 속성의 식별자로 사용할 수 있다.

다음과 같은 코드를 통해 심벌을 생성할 수 있다.

```javascript
const me = Symbol("OHTAEKWON");
console.log(me);	// Symbol(OHTAEKWON)
```

<br>

심벌은 항상 **고유**하다고 했지만, 같은 값을 가진 새로운 심벌을 만들면 차이가 있다.

```javascript
const me = Symbol("OHTAEKOWN");
console.log(me);	// Symbol(OHTAEKWON)

const clone = Symbol("OHTAEKWON");
console.log(clone);	// Symbol(OHTAEKWON)

console.log(me == clone); // false
console.log(me === clone); // false
```

두 심벌의 값은 동일하지만, 각 심벌은 항상 **고유**하므로 다른 심벌과 겹치지 않는다.

