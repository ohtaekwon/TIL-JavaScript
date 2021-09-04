# PART 2

###  :pencil: ***입문 042 :  const로 상수 선언하기***

<br>

`ES6`에서 추가된 **const** 키워드는 *let* 키워드와 마찬가지로 **블록 단위**로 스코프를 정의할 수 있다. 하지만 *let*과의 큰 차이점은 **선언 시 값을 할당해야 하고 이후에 재할당을 할 수 없다.**

```javascript
const URL = 'http://js.com';
// 1.
URL = 'http://js.com';

// 2.
if (true) {
    const URL2 = 'http://js.com';
}
console.log(URL2);
```

- `1.` *const* 로 정의된 **URL** 상수에 새로운 문자열을 할당하면 *Uncaught TypeError: Assignment to constant variable.* 에러가 발생한다.
  그리고 *const*는 관례적으로 변하지 않는 값을 정의하기 때문에 **대문자**로 작성한다.

- `2.` *if* 문 블록 안에서 *const* 로 정의된 **URL2** 변수는 블록 밖에서 접근할 경우 에러가 발생한다.
  *const* 키워드로 정의된 상수에 객체를 할당하면 **불변 객체** (**Immutable Object**)가 되지 않는다. 
  - 불변 객체는 정의된 후에 그 상태를 바꿀 수 없는 객체를 의미한다.

<br>

```javascript
// 1.
const CONST_USER = {name : 'jay', age: 30};
console.log(CONST_USER.name, CONST_USER.age);		// jay 30

CONST_USER.name = 'jay2';
CONST_USER.age = 31;
console.log(CONST_USER.name, CONST_USER.age);		// jay2 31

// 2.
CONST_USER = {name : 'bbo'};	// Uncaught TypeError: Assignment to constant variable.
```

- `1.` *const* 로 정의된 **CONST_USER**는 **불변 객체**가 아니라서 *name* 속성에 다른 값을 할당할 수 있다. 마찬가지로 *age* 속성도 변경 가능하다. 
  객체의 내부 상태가 변경 가능하기 때문에 *const*로 **배열을 선언하여도 새로운 요소를 추가하거나 변경할 수 있다. **
- `2.` *const*로 정의되었기 때문에 **재할당만 되지 않는다.**
  - ***즉, 새로운 객체로 할당은 못하고 객체 내부의 상태만 변경할 수 있다.***


