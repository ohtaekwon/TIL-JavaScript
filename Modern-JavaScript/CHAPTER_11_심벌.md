#  CHAPTER 11

###  :pencil: ***심벌***

`ES6`에서 **심벌(Symbol)** 이라는 새로운 원시 자료형이 추가되었다.

<br>

### :page_facing_up: 11.1. 심벌의 고유성

---

심벌은 항상 **고유(unique)** 하며 객체 속성의 식별자로 사용할 수 있다.

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
<br>

<br>

### :page_facing_up: 11.2. 객체 속성에 대한 식별자

---

**심벌**을 사용하여 객체 속성에 대한 식별자를 만들 수 있다.

```javascript
const office = {
    "Tom" : "CEO",
    "Mark" : "CTO",
    "Mark" : "CIO",
};

for(person in office) {
    console.log(person);
}
// Tom
// Mark
```

사무실 객체가 있고, 그 사무실에는 3명의 사람이 있다. 그중 2명의 이름이 같다. 

- 이럴 때 속성 이름이 **겹치는 것을 피하기 위해** 심벌을 사용한다.

```javascript
const office = {
    [Symbol("Tom")] : "CEO",
    [Symbol("Mark")] : "CTO",
    [Symbol("Mark")] : "CIO",
};

for(person in office){
    console.log(person);
}
// undefined
```

심벌은 열거 기능을 하지 않기 때문에 심벌에 대해 반복하려고 하면 **undefined**가 출력된다.

- 즉 ,`for in`으로 심벌에 대해 반복할 수 없다.

<br>

여기서 객체 속성의 배열을 얻기 위해서는 `Object.getOwnPropertySymbol()`를 사용한다.

```javascript
const office = {
    [Symbol("Tom")] : "CEO",
    [Symbol("Mark")] : "CTO",
    [Symbol("Mark")] : "CIO",
};

const symbols = Object.getOwnPropertySymbols(office);
console.log(symbols);
// (3) [Symbol(Tom), Symbol(Mark), Symbol(Mark)]
// 0: Symbol(Tom)
// 1: Symbol(Mark)
// 2: Symbol(Mark)
```

배열을 얻은 후 속성에 접근하려면 `map`을 사용하면 된다.

```javascript
const symbols = Object.getOwnPropertySymbols(office);
// 배열의 값을 얻었다.

// 속성에 접근하기 위해서는 배열에 map을 사용한다.
const value = symbols.map(symbol => office[symbol]);
console.log(value);
// (3) ['CEO', 'CTO', 'CIO']
// 0: "CEO"
// 1: "CTO"
// 2: "CIO"
```

심벌의 모든 값을 포함하는 배열이 출력된다.
