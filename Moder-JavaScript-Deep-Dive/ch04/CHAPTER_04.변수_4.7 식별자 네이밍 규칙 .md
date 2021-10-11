#  _CHAPTER 04_

###  :pencil: ***변수***

<br>

### :page_facing_up: 4.7. 식별자 네이밍 규칙

---

**식별자(identifier)** 는 어떤 값을 구별해서 식별해낼 수 있는 고유한 이름을 말한다. 

_식별자는 다음과 같은 네이밍 규칙을 준수해야한다._

- 식별자는 특수문자를 제외한 문자, 숫자, 언더스코어(`_`), 달러 기호(`$`) 를 포함할 수 있다.
- 단, 식별자는 특수문자를 제외한 문자, 언더스코어(`_`), 달러 기호(`$`)로 시작해야 한다. 숫자로 시작하는 것은 허용하지 않는다. 
- 예약어는 식별자로 사용할 수 없다.

<br>

#### :file_folder: 1) 예약어(reserved word)

예약어는 프로그래밍 언어에서 사용되고 있거나 사용될 예정인 단어를 말한다. 

##### _자바스크립트 예약어_

| await          | break        | case            | catch      | class        | const          |
| -------------- | ------------ | --------------- | ---------- | ------------ | -------------- |
| **continue**   | **debugger** | **default**     | **delete** | **do**       | **else**       |
| **enum**       | **export**   | **extends**     | **false**  | **finally**  | **for**        |
| **function**   | **if**       | **implements*** | **import** | **in**       | **instanceof** |
| **interface*** | **let***     | **new**         | **null**   | **package*** | **private***   |
| **protected*** | **public***  | **return**      | **super**  | **static***  | **switch**     |
| **this**       | **throw**    | **true**        | **try**    | **typeof**   | **var**        |
| **void**       | **while**    | **with**        | **yield*** |              |                |

- `*` 식별자로 사용 가능하나 `strict mode` 에서는 사용 불가

<br>

변수 이름도 식별자이므로 위 네이밍 규칙을 따라야 한다. 예를 들어, 다음과 같은 식별자는 변수 이름으로 사용할 수 있다. 참고로 변수는 **쉼표** (`,`)로 구분해 하나의 문에서 여러 개를 한번에 선언할 수 있다. 하지만 가독성이 나빠지므로 권장하지 않는다.

<br>

###### _[ 예제 04-12 - 다양한 식별자  ]_

```javascript
var person, $elem, _name, first_name, val1;
```

`ES5` 부터 식별자를 만들 때 유니코드 문자를 허용하므로 알파벳 외의 한글이나 일본어 식별자도 사용할 수 있다. 하지만 알파벳 외의 유니코드 문자로 명명된 식별자를 사용하는 것은 바람직하지 않으므로 권장하지 않는다.

<br>

###### _[ 예제 04-13 ]_

```javascript
var 이름;
```

식별자는 명명 규칙에 위배되므로 변수 이름으로 사용할 수 없다.

<br>

###### _[ 예제 04-14 ]_

```javascript
var first-name;		// Uncaught SyntaxError: Unexpected token '-'
var 1st;			// Uncaught SyntaxError: Invalid or unexpected token
var this;			// Uncaught SyntaxError: Unexpected token 'this'
```

자바스크립트는 대소문자를 구별하므로 다음 변수는 각각 별개의 변수다.

<br>

###### _[ 예제 04-15 ]_

```javascript
var firstname;
var firstName;
var FIRSTNAME;
```

변수 이름은 변수의 존재 목적을 쉽게 이해할 수 있도록 의미를 명확히 표현해야 한다. 좋은 변수 이름은 코드의 가독성을 높인다.

<br>

###### _[ 예제 04-16 ]_

```javascript
var x = 3;			// NG. X변수가 의미하는 바를 알 수 없다.
var score = 100;	// OK. score 변수는 점수를 의미한다.
```

변수 선언에 별도의 주석이 필요하다면 변수의 존재 목적을 명확히 드러내지 못하는 것이다

<br>

###### _[ 예제 04-17 ]_

```javascript
// 경과 시간, 단위는 날짜다.
var d;		// NG

var elapsedTimeInDays;		// OK
```

**네이밍 컨벤션(naming convention)** 은 하나 이상의 영어 단어로 구성된 식별자를 만들 때 가독성 좋게 단어를 한눈에 구분하기 위해 규정한 명명 규칙이다. 

네이밍 컨벤션을 잘 지키면 읽기 좋은 이름을 만들 수 있다. 다음과 같은 4가지 유형의 네이밍 컨벤션이 자주 사용된다.

###### _[ 예제 04-18 ]_

```javascript
// 카멜 케이스(camelCase)
var firstName;

// 스네이크 케이스(snake_case)
var first_name;

// 파스칼 케이스(PascalCase)
var FirstName;

// 헝가리언 케이스(typeHungarinaCase)
var strFirstName;
var $elem = document.getElementById('myId');		// DOM 노드
var observable$ = fromEvent(document, 'click');		// RxJs 옵저버블
```

일관성을 유지한다면 어떤 네이밍 컨벤션을 사용해도 좋지만 자바스크립트에서는 일반적으로 변수나 함수의 이름에는 카멜 케이스를 사용하고, 생정자 함수, 클래스의 이름에는 파스칼 케이스를 사용한다.

`ECMAScript` 사양에 정의되어 있는 객체와 함수들도 카멜 케이스와 파스칼 케이스를 사용하고 있다. 따라서 코드 전체의 가독성을 높이려면 카멜 케이스를 따르는 것이 유리하다.

<br>
