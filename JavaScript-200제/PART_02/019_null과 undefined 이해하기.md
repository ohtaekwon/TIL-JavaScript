# PART 2

###  :pencil: ***입문 019 :  null고 undefined 이해하기***

<br>

*null*과 *undefined*를 보이는 그대로 해석하면 **'빈 값,' , '없는 값'** 을 의미하는 것처럼 보이지만 **차이점이 존재한다.**

```javascript
var value = null;
console.log(value);				// null
console.log(typeof value);		// undefined
var value;						// undefined
console.log(value);				// null
console.log(typeof value);		// object
```

**null**은 **비어 있는, 존재하지 않는 값**을 의미한다. 

- 즉 , **null**은 값의 부재를 의미하며, **원시 자료형 null로 분류된다.**
- 단, *typeof*로 자료형을 확인할 때 **object(객체)**를 반환하는데, 이는 자바스크립트 기존 이슈로 인한 결과이다.
- **주의 : null이 객체형이라 오해하지 말것**

<br>

**undefined**는 변수가 정의되었지만, **아무 값도 할당받지 않은 상태**를 의미한다. 예를 들어, 함수에서 명시적으로 값을 반환하지 않을 때 또는 변수에 어떠한 값고 대입하지 않고 정의했을 때 **undefined**가 반환된다.

*undefined*는 *undefined* 원시 자료형으로 분류된다.


