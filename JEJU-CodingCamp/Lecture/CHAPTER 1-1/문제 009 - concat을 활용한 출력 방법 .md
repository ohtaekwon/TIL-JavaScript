# _CHAPTER 1-1_

###  :pencil: ​_문제 009 : concat을 활용한 출력 방법_

다음 소스 코드를 완성하여 날짜와 시간을 출력하시오.

:desktop_computer: ***1. 데이터***

```javascript
var year = '2021';
var month = '07';
var day = '27';
var hour = '16';
var minute = '57';
var second = '27';

var result  = 		// 빈칸을 채워라.

console.log(result);
```

:desktop_computer: ***2. 출력***

```
2021/07/27 16:57:27
```

<br>

:ballot_box_with_check: **풀이 코드 : 소스**

``` javascript
var result = year.concat('/',month,'/',day," ",hour,':',minute,':',second);
console.log(result);
```

<br>

---

<br>

### :diamond_shape_with_a_dot_inside: 추가 학습

###  :one: ​concat 메서드

- **concat**은 영어단어 **concatenate라는 동사에서 나왔다.** 이것은 ***무엇과 무엇을 잇다. 또는 연결하다.***의 의미가 있다.

- 즉, concat은 연결하는 의미를 가진 메서드이다.
- concat 메서드는 파라미터로 전달되는 값들을 기존 배열에 합쳐서 새로운 배열을 반환해주는 배열의 메서드들 중 하나이다.
- 한 가지 특별한 점은, 만약 파라미터로 전달되는 인자 값이 배열일 경우에는 해당 배열이 펼쳐지면서 기존 배열에 합쳐진다.
- 그 밖에 배열과 배열을 연결해주는 concat 메서드도 있다.

<br>

###  :two: ​concat 문법

```javascript
const myArr = [1, 2, 3];

// arr.concat(value1, value2, ...)
console.log(myArr.concat(4, 5)); // [1, 2, 3, 4, 5]
console.log(myArr.concat('육', '칠')); // [1, 2, 3, '육', '칠']
console.log(myArr.concat(true, false)); // [1, 2, 3, true, false]
console.log(myArr.concat({name: 'bigtop'})); // [1, 2, 3, {...}]
```

<br>

###  :three: ​concat 과 push의 차이점

이렇게 보면 push와 크게 다를 게 없어 보이지만, 일단 가장 큰 차이점은, **push는 기존 배열의 마지막 요소로 값을 추가**하는 반면, **concat메서드는 slice메서드처럼 기존 배열에 아무런 영향을 주지 않는다는 것**이다.

만약 파라미터에 아무런 값도 전달하지 않을 경우에는 이 부분도 slice와 마찬가지로 **기존의 배열 전체가 그대로 반환**된다.

```javascript
const myArr = [1, 2, 3];

// arr.concat(value1, value2, ...)
console.log(myArr.concat()); // [1, 2, 3]
```

***concat 메서드는 배열에 값을 추가하는 용도 보다는 주로 배열과 배열을 합치는데 사용된다***