# PART 2

###  :pencil: ***입문 019 :  null고 undefined 이해하기***

<br>

*null*과 *undefined*를 보이는 그대로 해석하면 **'빈 값,' , '없는 값'** 을 의미하는 것처럼 보이지만 **차이점이 존재한다.**

```javascript
// 1.
var value = null;

// 2.
console.log(value);				// null

// 3.
console.log(typeof value);		// undefined

// 4.
var value;						// undefined

// 5.
console.log(value);				// null


// 6.
console.log(typeof value);		// object
```

**null**은 **비어 있는, 존재하지 않는 값**을 의미한다. 

- 즉 , **null**은 값의 부재를 의미하며, **원시 자료형 null로 분류된다.**
- 단, *typeof*로 자료형을 확인할 때 **object(객체)**를 반환하는데, 이는 자바스크립트 기존 이슈로 인한 결과이다.
- **주의 : null이 객체형이라 오해하지 말것**

<br>

**undefined**는 변수가 정의되었지만, **아무 값도 할당받지 않은 상태**를 의미한다. 예를 들어, 함수에서 명시적으로 값을 반환하지 않을 때 또는 변수에 어떠한 값고 대입하지 않고 정의했을 때 **undefined**가 반환된다.

*undefined*는 *undefined* 원시 자료형으로 분류된다.

위의 예제에서 *typeof*는 우측에 있는 값이 어떤 자료형인지 확인하고, 확인된 자료형 정보를 문자형으로 반환한다. 

- `1`, *value* 변수에 `null`값을 할당한다. 
- `2`, 대입된 변수값 그대로 `null`이 출력된다.
- `3`, *value* 변수의 자료형을 확인하면 `object(객체)`로 출력된다/
- `4`, *value* 변수를 아무것도 할당하지 않고 정의한다.
- `5`, *value* 변수를 출력하면 할당된 값이 없기 때문에 `undefined`가 출력된다
- `6`, *value* 변수의 자료형을 확인하면 `undefined`가 출력된다.

<br>

**동등 연산자** `==`인 경우에는 자료형 비교까지 이루어지지 않기 때문에 *true*를 반환한다. 반면 자료형 변환이 없는 엄격한 **일치 연산자** `===`로 확인하면, *null* 과 *undefined*의 자료형이 다르기 때문에 *false*가 반환된다.

연산자에 따라 *null*과 *undefined*의 비교결과가 다르게 반한될 수 있다는 것을 유의해야한다. 
