#  CHAPTER 00

###  :pencil: ***자바스크립트 기초***

<br>

자바스크립트는 *브렌던 아이크*가 만든 프로그래밍 언어로, **대화형 웹 페이지**를 만들 수 있으며 **웹 어플리케이션**을 만들기 위한 필수적인 언어이다.

`HTML` 페이지에 `Javascript`를 삽입하는 방시은 두 가지이다. 

- `script`태그를 사용하고 그 안에 자바스크립트 코드를 직접 삽입
- 외부 파일을 참조하여 삽입하는 방법

##### _EX) script 태그로 코드를 감싸는 예_

```html
script type="text/javascript"> [YOUR_SCRIPT_HERE] </script>
```

<br>

##### _EX) 외부 파일을 참조 예_

```html
script src="/home/sciprt.js"></script>
```

원하는 만큼 스크립트를 추가할 수 있으며, `절대 경로`, `상대 경로`, `전체 경로` 모두 사용할 수 있다.

```html
<!-- 프로젝트 루트로부터의 절대 경로 -->
<script src="/home/script.js"></script>

<!-- 현재 폴더에 대한 상대 경로 -->
<script src="script.js"></script>

<!-- jquery 라이브러리의 전체 URL -->
<script src"http://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/core.js"></script> 
```

`script` 태그 안에 코드를 작성하기보다는 파일을 넣어서 브라우저가 가져오는 파일 수에 관계 없이 한 번에 다운로드하고 캐시하게 하는 것이 좋다. 

이 방식에서는 **캐시된 버전의 파일을 사용할 수 있으므로 성능상으이 이점이 있다.**

<br>

---

### :page_facing_up: 0.1. 변수

### 0.1.1. 변수란?

**변수(variable)** 는 값을 담기 위한 공간이다. 예를 들어 *사용자 이름*, *주소*, *쇼핑몰 사이트의 상품 항목* 등등의 **값을 저장하기 위해 변수를 사용한다.**

<br>

##### _ES6(ES2015) 이전 변수 선언 방법_

```javascript
var username = "Alberto Mantalesi";
```

<br>

##### _ES6(ES2015) 변수 선언 방법_

```javascript
let username = "Alberto Montalesi";
const username = "Alberto Montalesi";
```

변수를 선언하는 키워드 : `var`, `const`, `let`

- **const** 키워드로 생성된 변수는 이름에서 알 수 있듯 **상수(constant)** 이므로 그 값을 덮어 쓸 수 없다.

```javascript
const age = 26;
age =27;		// Uncaught TypeError: Assignment to constant variable.
```

- **const** 로 선언한 변수에는 새 값을 할당할 수 없다.

<br>

```javascript
let height = 190;
height = 189;	// 189
```

- 이번에는 오류가 발생하지 않는다. 앞의 `var` 키워드와 마찬가지로 변수에 값을 **재할당**할 수 있다.

<br>

### `let`과 `const`의 사용 차이

- `const` : 값을 재할당해야 하는 상황이 아닐 경우
- `let` : 나중에 `const`로 선언한 변수 중 하나를 재할당해야 할 경우

<br>

### 0.1.2. 변수 명명법

변수에 이름을 붙일 때 신경 써야 하는 규칙이 있다. 

```javascript
// 변수명은 숫자로 시작할 수 없다.
let 1apple = "one apple";    // 불가능

// 변수명에는 공백, 기호, 마침표가 들어갈 수 없다.
let hello! = "hello!"; 		// 불가능
```

변수 이름을 선택할 때 가장 권장하는 방식은 변수 이름 자체가 변수를 설명할 수 있게 하는 방식이다.

- 두문자어, 약어, 의미없는 이름 사용 지양

```javascript
// 나쁜 예 1)
let cid = 12;			 // 12 가 무슨의미인지 모름

// 좋은 예 1)
let clientID = 12;		// Client ID를 의미하는 변수

// 나쁜 예 2)
let id = 12;			// 무순 ID? ueserID? dogID? catID?

// 좋은 예 2)
let userID = 12;		// 구체적으로!! USER의 ID
```



<br>

---

### :page_facing_up: 0.2. 자료형

###  0.1.1. 자료형

자바스크립트는 **동적 언어**(**dynamic language**) 이다. 즉, 정적언어와 다릴 **변수를 정의할 때 자료형을 정의할 필요가 없다.**

```javascript
// 문자열일까? 숫자일까?
var userID;

userID = 12;					// 숫자를 할당해보자.
console.log(typeof userID);		// number
userID = 'user1';				// 문자열을 할당해보자.
console.log(typeof userID);		// string
```

자료형을 정의할 필요가 없다는 것은 처음에 편리하지만, 대규모 프로젝트에서 작업할 때는 **문제의 원인**이 될 수 있다.

- 대규모 프로젝트시, 자바스크립트를 엄격한 자료형을 준수하는 **강타입 언어**(**강형 언어, 엄격한 타입 언어**)로 탈바꿈시키는 **타입스크립트**가 유용하다.
- 자바스크립트에는 총 **7개의 자료형**이 있고, 6개는 **원시 자료형**이고 나머지 하나는 **객체**이다.

<br>

###  0.1.2. 원시 자료형

**원시 자료형**(primitive)은 객체가 아닌 자료형으로, 메서드를 가지지 않는다. 다음과 같이 자료형이 원시 자료형에 해당한다.

- **string** : **문자열**
- **number** : **숫자**
- **boolean** : **불리언**
- **null** : **널**
- **undefined** : **정의되지 않음**
- **symbol** : **심벌** (`ES6`에서 추가 됨. )

<br>

_**각 자료형의 사용**_

1) **string**은 텍스트 데이터를 나타내는 데 사용된다.

   - ex) 이름, 주소 등

   ```javascript
   let userName = "OHTAEKWON";
   console.log(userName);				// OHTAEKWON
   ```

<br>

2. **number**는 숫자로 된 값을 나타내는 데 사용된다.

   - 자바스크립트에는 **정수**만을 따로 표현하는 자료형이 따로 없다.

   ```javascript
   let age = 25;
   ```

<br>

3. **boolean**은 *true*(참) 또는 *false*(거짓) 값을 나타내는 데 사용된다.

   ```javascript
   let married = false;
   married			// false
   ```

<br>

4. **null** 은 **'값이 없음'**을 나타낸다.

<br>

5. **undefined**는 **'정의되지 않은 값'**을 나타낸다.

<br>

6. **symbol**(심벌)은 고유하고 변경할 수 없는 값을 나타낸다.
   - `ES6`에 추가된 자료형으로, `원시 자료형` 중 가장 최근에 추가된 것이다.

<br>

###  0.1.3 객체



6개의 원시 자료형은 **null** 값이든, **true**든, **false**든 하나의 값만 담을 수 있지만, **객체(object)**는 **여러 속성의 모음을 저장**하는데 사용할 수 있다.

```javascript
const car = {
    wheels : 4,
    color : "red",
};
```

**차(car)**의 속성을 저장하는 데 사용하는 간단한 객체이다.

각 속성에서는 **키**(첫 행의 경우 **wheels** )와 **값**(첫 행의 경우 4)이 있다.
**키**의 자료형은 **string 자료형**이지만 **값**은 **모든 자료형**이 될 수 있으며, 심지어 함수가 될 수도 있다.

**값**이 함수이면 **메서드**를 호출하는 셈이 된다.

```javascript
const car = {
    wheel : 4,
    color : "red",
    drive : function(){
        console.log('wroom wroom')
    },
};

console.log(Object.keys(car)[0]);			// wheels
console.log(Object.keys(car)[1]);			// color
console.log(Object.keys(car)[2]);			// drive

console.log(typeof Object.keys(car)[0]);	// string

car.drive();								// wroom wroom
```

이와 같이 `car` 객체에서 `drive` 함수를 호출할 수 있다.

<br>

###  0.1.4  빈 객체 생성하기

객체를 생성할 때에는 속성을 선언할 필요가 없다.

빈 객체를 만드는 방법은 **두 가지**가 있다.

```javascript
// 1.
const car = new Object();

// 2.
const car = {} 
```

- `2.` 방식이 더 일반적으로 사용되는데, 이를 **객체 리터럴**(object literal)이라고 부른다. 

비어 있는 새 `car` 객체가 있으므로, 새 속성을 추가할 수 있다.

```javascript
car.color = 'red';
console.log(car);			// {color: 'red'}
```

**점 표기법**(**dot notation**)을 사용하여 **객체** `car`에 새 속성을 추가한다.

<br>

_객체의 속성에 접근할 때는 **점 표기법**과 **대괄호 표기법**이 있다._

```javascript
const car = {
    wheels : 4,
    color : 'red',
};

console.log(car.wheels);			// 4

console.log(car['color']);			// red
```

**점 표기법**과 **대괄호 표기법**은 완전히 동일한 것이 아니다. 

- 여러 단어로 이뤄진 속성의 경우 **점 표기법**을 사용할 수 없다.

```javascript
const car = {
    wheels : 4,
    color : 'red',
    "goes fast": true 
};

console.log(car.goes fast);			// SyntaxError
console.log(car['goes fast']);		// true
```

여러 단어로 된 속성을 사용하려면 해당 이름을 **따옴표**로 묶어야 하기 때문에, **대괄호 표기법**으로만 접근할 수 있다.

대괄호 표기법을 사용하는 또 다른 경우는 **키**를 사용해서 **객체**의 속성에 접근해야 할 때이다.

애플리케이션이 사용자로부터 입력을 받은 다음, 입력받은 값을 객체에 접근하는데 사용할 변수에 저장하는 경우

- 예를 들어, 사용자가 자동차를 찾고 있을 때, 애플리케이션에서는 사용자에게 좋아하는 자동차 브랜드를 알려달라고 요청한다.
- 사용자가 선택한 브랜드는 적절한 모델을 출력하기 위한 **키**가 된다.

```javascript
const cars = {
    ferrari : "california",
    porsche : "911",
    bugatti : "veyron",
};

// 사용자 입력
const key = "ferrari";
console.log(cars.key)			// undefiend

console.log(cars['key']);		// undefined

console.log(cars[key]);			// california
// 이와같이, 변수에 저장된 키를 통해 객체의 속성에 접근하려면 대괄호 표기법을 사용해야 한다.
console.log(cars[key][0]);		// c
```

_**key**는 문자열이 아닌 변수 이름이므로 따옴표 표기를 해서는 안 된다._

<br>

###  0.1.5 객체의 복사

원시 자료형과는 달리 객체를 복사할 떄는 **참조 방식**이 쓰인다.

```javascript
let car = {
    color : 'red',
};

let secondCar = car;
```

여기서 `secondCar`는 그 자체로 객체가 아니라 `car`에 대한 참조, 즉 **주소(address)**를 저장한다.

```javascript
// car 객체 생성
let car = {
    color : 'red',
};

// secondCar에 car에 대한 주소 저장
let secondCar = car;

// car 객체에 wheels 속성 추가 : 키(wheels)/ 값(4)
car.wheels = 4;

console.log(car);		// {color: 'red', wheels: 4}
console.log(secondCar)	// {color: 'red', wheels: 4}
```

결과를 보면 `secondCar`는 단순히 `car`에 대한 참조만 저장하기 때문에 `car`를 수정하면 `secondCar`도 변경된다.

```javascript
console.log(car == secondCar);			// true
console.log(car === secondCar);			// true
```

**행동 연산자(equality)** `==`를 사용하든, **완전 행동 연산자(strict equality)** `===` 를 사용하든 **true**가 반환된다. 

- 두 객체가 동일하다는 의미이다.
- 동일한 객체를 비교할 때에만 **true**가 반환된다.

<br>

#### _빈 객체끼리 비교  vs. 동일한 속성을 가진 객체끼리 비교_

```javascript
const emptyObj1 = {};
const emptyObj2 = {};

emptyObj1 == emptyObj2;			// false
emptyObj1 === emptyObj2; 		// false

const obj1 = {a:1};
const obj2 = {a:1};

obj1 == obj2;					// false
obj1 === obj2;					// false
```

- 동일한 객체를 비교할 때만 **true**를 반환받을 수 있다.
- 자바스크립트에서 객체의 복사본을 만드는 방법
  - `Object.assign()`

```javascript
const car = {
    color:'red',
};

// 1.
const secondCar = Object.assign({},car);

car.wheels = 4;

console.log(car);						// {color: 'red', wheels: 4}
console.log(secondCar);					// {color: 'red'}
```

- 이렇게 하면 `car`를 업데이트해도 `secondCar`에는 영향을 주지 않는다.
- `Object.assign()`
  - 첫 번째 인수 : 복사본에 해당하는 객체
  - 두 번째 인수 : 원본에 해당하는 객체

- `1.` 빈 객체를 복사본으로 넣고, `car`를 원본으로 넣는다.

<br>

###  0.1.6  배열

객체는 `키/값 쌍`(key-value pair)에 데이터를 저장한다. **배열**은 순서대로 값을 저장하는 객체이다.

```javascript
const fruitBasket = ['apple', 'banna', 'orange'];
```

- 이렇게 만들어진 배열의 각 항목의 값에 접근할 때는 **인덱스**(**index**)를 사용하면 된다.
  - 배열의 인덱스는 `0`부터 시작한다.

```javascript
const fruitBasket = ['apple', 'banna', 'orange'];
console.log(fruitBasket[0]);						// apple
console.log(fruitBasket[1]);						// banna
console.log(fruitBasket[2]);						// orange
console.log(fruitBasket[3]);						// undefined
```

<br>

##### _배열에 대해 호출할 수 있는 메서드_

```javascript
const fruitBasket = ['apple', 'banna', 'orange'];

// 배열의 길이 확인
console.log(fruitBasket.length);	// 3

// 배열의 끝에 새 값을 추가
fruitBasket.push('pear');			// 4
console.log(fruitBasket);			// (4) ['apple', 'banna', 'orange', 'pear']

// 배열의 시작에 새 값을 추가
fruitBasket.unshift('melon');		// 5
console.log(fruitBasket);			// (5) ['melon', 'apple', 'banna', 'orange', 'pear']

// 배열의 끝에서 값 하나를 제거
fruitBasket.pop();					// 'pear'
console.log(fruitBasket);			// (4) ['melon', 'apple', 'banna', 'orange']

// 배열의 시작에서 값 하나를 제거
fruitBasket.shift();				// 'melon'
console.log(fruitBasket);			// (3) ['apple', 'banna', 'orange']
```

- 이러한 메서드를 사용하여 배열의 시작 또는 끝에서 원소를 쉽게 추가하고 제거할 수 있다.

<br>

#### _typeof 를 사용해서 자료형 확인하기_

`typeof`를 사용해서 변수가 어떤 값을 담았는지 확인할 수 있다.

```javascript
// 1. 문자열
const str = "hello";
typeof(str);					// 'string'

// 2. 숫자
const num = 12;
typeof(num);					// 'number'

// 3. 배열
const arr = [1,2,3];
typeof(arr);					// 'object'

4. 객체
const obj = {prop : 'value'};
typeof(obj);					// 'object'
```

- `3.` 에서 **배열**은 원시 자료형이 아니라 **객체**이다.

<br>

```javascript
typeof(null);					// 'object'
```

- **null**은 원시 자료형이다. 하지만 `typeof`를 했을 때 **object**라는 결과물이 나오는데, 이것은 자바스크립트의 첫 번째 구현에서 발생한 버그이다.
  - http://2ality.com/2013/10/typeof-null.html

<br>
