#  CHAPTER 01

###  :pencil: ***var, let, const***

<br>

`ES6`부터 **let**과 **const**가 도입되었고, 필요에 맞게 변수를 정의하는 것이 더 용이해졌다. 

<br>

<br>

### :page_facing_up: 1.1. var, let, const의 차이

---

### 1.1.1. var

**var** 키워드로 선언된 변수는 함수 스코프에 **종속된다.** 반면, **for**루프 (블록 스코프) 내에서 **var**키워드로 변수를 선언하면 이 변수를 **for 루프 밖에서도 사용할 수 있다.**

#### _EX1) var을 이용한 스코프에서 활용_

```javascript
// 1.for 외부에서 접근
for (var i=0; i<10; i++){
    var leak = "I am available outside of the loop";
}
console.log(leak);			// I am available outside of the loop

// 2.함수 내에 접근
function myFunc(){
    var functionScoped = "I am available inside this function";
    console.log(functionScoped);
}
myFunc();	// I am available inside this function
console.log(functionScoped); // ReferenceError: functionScoped is not defined

```

- `1.` 첫 번째에서는 `var`의 값이 **블록 스코프**를 벗어나도 **for**루프 외부에서 접근할 수 있다.
- `2.` 두 번째에서는 `var`가 함수 스코프 내에 제한되어 함수 외부에서 접근할 수 없다.

<br>

### 1.1.2. let

**let**(및 **const**) 키워드로 선언된 변수는 **블록 스코프**로 종속된다. 즉, ***변수가 선언된 블록과 그 하위 블록 내에서만 사용할 수 있다.***

#### _EX2) let을 이용한 블록 스코프 내에서 활용_

```javascript
// 1. let 사용의 예
let x = "global";

if(x === "global"){
    let x = "block-scoped";
    
    console.log(x);	// block scoped
}

console.log(x);		// global

// 2. var 사용의 예
var y = "global";

if(y==="global"){
    var y = "block-scoped"
    console.log(y);	// block-scoped
}

console.log(y);	// block-scoped
```

- `1.` 이처럼 **블록 스코프** 내에서 **let**으로 선언한 변수에 새 값을 할당했을 때 블록 바깥에서는 그 값이 변경되지 않았다.

- `2.` 반면, `var`로 선언된 변수에 대해 동일한 작업을 하면 블록 스코프 외부에서 접근이 가능하므로 바깥에서도 값이 변경이 된다. 

<br>

### 1.1.3. const

**let**과 마찬가지로 **const**로 선언되 변수도 **블록 스코프에 종속**되지만, 차이점이 있다.

- **재할당**을 통해 값이 변경될 수 없고 다시 선언될 수 도 없다.

#### _EX3) const의 예 - 재할당x_

```javascript
const constant = "I am a constant";
constant = "I can't be ressigned";	// Uncaught TypeError: Assignment to constant variable.

```

- 하지만, `const`로 선언된 변수가 불변이라는 의미는 아니다.

<br>

### 1.1.4. const에 객체가 담겼다면?

```javascript
const person = {
    name : "OHTAEKWON",
    age : 30,
};

person.age = 28;
console.log(person.age);			// 28
```

- 이 경우에서 변수 전체를 재할당하는 것이 아니라, 그 **속성 중 하나**만 재할당하는 것이므로 문제가 없다.

- 그러나 객체의 내용을 변경할 수 없게 `const` 객체를 고정할 수는 있다. 
  - 하지만 객체의 값을 변경하려고 시도할 때 자바스크립트가 오류를 던지지는 않는다.

```javascript
const person = {
    name : "ohtaekwon",
    age : 30,
};

person.age = 28;

console.log(person.age);		// 28

Object.freeze(person);			// {name: 'ohtaekwon', age: 28}

person.age = 30;				// 30

console.log(person.age);		// 28
```

<br>

<br>

### :page_facing_up: 1.2. TDZ

---

**TDZ** 란 **일시적 비활성 구역, Temporal dead zone**을 의미한다. 

```
console.log(i);
var i = "I am a variable";			// undefined

console.log(i);						// I am a variable

console.log(j);
let j = "I am a let";				// Uncaught ReferenceError: j is not defined

```

**var** 는 **정의되기 전에** 접근할 수 있지만, 그 **값**에는 접근할 수 없다. **let**과 **const**는 **정의되기 전에 접근할 수 없다.**

var, let, const 모두 다른 소스에서 읽을 수 있는 내용임에도 불구하고 **호이스팅(Hoisting)**의 대상이 된다. 즉, 코드가 실행되기 전에 처리되고 해당 스코프(글로벌 or 블록) 상단으로 올라간다.

- **var**가 가지는 가장 큰 **차이점**은 **정의되기 전에도 접근할 수 있다는 점**이다. 
  - 즉, 정의되기 전에 **undefined** 값을 가지게 된다. 
- 반면, **let**은 변수가 선언될 때까지 **일시적으로 비활성 구역**, 즉, **TDZ**에 있게 된다. 
  - 따라서 초기화 전에 변수에 접근하면 오류가 발생한다.
  - **undefined** 값을 얻는 것보다 오류가 발생하는 편이 코드 디버깅이 더 쉽다.

<br>

<br>
