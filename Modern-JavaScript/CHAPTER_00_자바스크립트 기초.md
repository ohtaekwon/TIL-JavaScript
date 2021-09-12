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
   ```

   



