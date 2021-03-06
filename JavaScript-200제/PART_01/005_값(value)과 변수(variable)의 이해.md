# PART 1

###  :pencil: ***입문 005 :  값(value)과 변수(variable)의 이해***

<br>

#### _프로그래밍 언어를 구성하는 기본 단위인 값(value)_

값을 이해하기 위해서는 컴퓨터의 처리과정을 이해해야한다. 컴퓨터가 작업을 처리하기 위해서는 작업에 필요한 모든 것을 **이해할 수 있는 형태**로 구성해야 한다. 또한, 컴퓨터가 스스로 생각하고 처리하는 것이 아니기 떄문에, 모든 것을 **데이터**로 이루고 컴퓨터는 그에 따라 처리한다.

컴퓨터 세계는 `0`과 `1`로 표현한다. 이것을 컴퓨터가 실행할 수 있는 형태로 표현하면 **2진수(1과 0)가 된다.** 즉, **비트(bit, Binary Digit, 2진수)**는 컴퓨터 CPU가 처리하는 데이터의 최소 단위 크기이다. 이렇게 컴퓨터 세계에서 모든 데이터는 `비트(bit)`로 구성된다.

컴퓨터는 `데이터`를 비트로 처리하지만, 프로그래밍에서는 이것들을 **값(value)**로 나타낸다.

- 즉, 숫자, 텍스트 당과 같이 모든 값은 컴퓨터 내부에서 비트로 이루어져 있다.
- 컴퓨터가 동시에 많은 값을 유지하고 처리하려면, 어딘가에 **값**을 `저장`해야한다.
  - 이렇게 **값을 넣어 놓는 공간**을 **변수(variable)**이라고 한다.

<br>

##### _자바스크립트에서 변수에 값을 저장하는 방법_

```javascript
foo = 'bar'
```

이러게 별도의 키워드 없이 변수를 할당하는 방법을 `암시적 선언`이라고 한다. 하지만, 암시적 선언보다 ***키워드를 사용하여 변수를 선언하는 것을 권장한다.***

왜냐하면, **변수가 선언되는 범위(Scope)** 때문이다.

```javascript
var name = "taekwon";
var number = 30;
var isTrue = true;
var nothing = null;
var empty = undefined;
var list = [];
var ref = {};
var func = function(){};
```

- **선언 키워드** : 자바스크립트는 다른 컴파일 언어와 달리 값을 변수로 저장할 때 어떤 유형인지 명시하지 않아도 된다. 그리고 일관된 `var` 키워드를 맨 앞에 작성하여 변수를 선언한다. 
  프로그래밍할때 때 값의 유형을 일일이 명시하지 않으면, 런타임 시 변수의 값에 의해 동적으로 유형이 결정된다. 
  - 이것을 `동적 바인딩(Dynamic Binding)`이라고 한다.

<br>

- **변수명** : 변수를 선언할 때 선언 키워드(var) 다음에 변수명을 작성한다. 자바스크립트에서 이미 사용중인 내장키워드를 사용하면 오류가 발생할 수 있다.

<br>

- **등호(=)** : 등호를 사이에 두고 왼쪽에 변수명과 오른쪽에 값을 작성한다. 
  - _변수명이 정의된 변수 메모리에 값을 대입한다는 의미이다._

<br>

- **값** : 자바스크립트에서 변수에 넣을 수 있는 값은 다양하다.
  - `단일자료형의 값`부터 `표현식`, `함수`등 값으로 대입할 수 있다.

<br>

#### :notebook: 자바스크립트 키워드(Keyword) 종류

```javascript
break case catch class const continue debugger default delete do else export extends finally for function if import in instance of let new return super switch this throw try type of var void while with yield
```

