#  _CHAPTER 04_

###  :pencil: ***변수***

<br>

### :page_facing_up: 4.5. 값의 할당

---

변수에 값을 **할당(assignment, 대입, 저장)** 할 때는 할당 연산자`=` 를 사용한다.

-  할당 연산자는 우변의 값을 좌변의 변수에 할당한다.

<br>

###### _[ 예제 04-06 - 변수선언과 값의 할당]_

```javascript
var score;			// 변수 선언
score = 80;			// 값의 할당
```

변수 선언과 값의 할당을 하나의 **문(statement)** 으로 단축 표현할 수 있다.

<br>

###### _[ 예제 04-07 - 변수 선언과 값의 할당 단축 표현]_

```javascript
var score = 80;			// 변수 선언과 값의 할당
```

변수 선언과 값의 할당을 2개의 문으로 나누어 표현한 코드와 변수 선언과 값의 할당을 하나의 문으로 단축 표현한 코드는 정확히 동일하게 동작한다.

- 즉, 자바스크립트 엔진은 변수 선언과 값의 할당을 하나의 문으로 단축 표현해도 변수 선언과 값의 할당을 2개의 문으로 나누어 각각 실행한다.
- 이때, ***주의할 점은 변수 선언과 값의 할당의 실행 시점이 다르다는 것이다.***

변수 선언은 소스코드가 순차적으로 실행되는 시점인 런타임 이전에 먼저 실행되지만, **값의 할당은 소스코드가 순차적으로 실행되는 시점인 런타임에 실행된다.**

<br>

###### _[ 예제 04-08 - 변수 선언 시점과 값의 할당 시점 - 런타임]_

```javascript
console.log(score);		// undefined

var score;		// ① 변수 선언
score = 80;		// ② 값의 할당

console.log(score);		// 80
```

**변수 선언(①)** 은 런타임 이전에 먼저 실행되고 **값의 할당(②)** 은 런타임에 실행된다. 따라서 `score` 변수에 값을 할당하는 시점(②)에는 이미 변수 선언이 완료된 상태이며, 이미 `undefined`로 초기화되어 있다. 

따라서, `score` 변수에 값을 할당하면 `score` 변수에 값은 `undefined` 에서 새롭게 할당한 숫자 값 `80`으로 **변경(재할당)** 된다.

변수 선언과 값의 할당을 하나의 **문(statement)** 으로 단축 표현할 수도 있으므로 앞 예제는 다음 예제와 동일하게 동작한다.

<br>

###### _[ 예제 04-09 - 하나의 문으로 단축 표현]_

```javascript
console.log(score);		// undefined

var score = 80;			// 변수 선언과 값의 할당

console.log(score);		// 80
```

변수의 선언과 값의 할당을 하나의 문장으로 단축 표현해도 자바스크립트 엔진은 **변수의 선언과 값의 할당을 2개의 문으로 나누어 각각 실행한다.** 따라서 변수에 `undefined` 가 할당되어 초기화되는 것은 변함이 없다.

<br>

`4-8` 처럼 변수에 값을 할당할 떄는 이전 값 `undefined`가 저장되어 있던 메모리 공간을 지우고 그 메모리 공간에 할당 값 `80`을 새롭게 저장하는 것이 아니라 **새로운 메모리 공간을 확보하고 그곳에 할당 값 `80`을 저장한다. **

###### _[ 예제 04-10 - 새로운 메모리 공간을 확보하고 할당 값 저장]_

```javascript
console.log(score);		// undefined

score = 80;		// 값의 할당
var score;		// 변수 선언

console.log(score);	// ?? => 80
```

`console.log(score);` 는 `80`이 출력된다.
