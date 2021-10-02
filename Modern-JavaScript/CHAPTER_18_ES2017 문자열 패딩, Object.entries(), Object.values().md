#  CHAPTER 18

###  :pencil: ***ES2017 : 문자열 패딩, Object.entries(), Object.values()***

`ES2017`에서는 많은 기능들이 추가 되었다.

<br>

### :page_facing_up: 18.1. 문자열 패딩

---

문자열 끝 부분 또는 시작 부분에 **패딩(padding)** 을 추가할 수 있다. 각각 `padEnd()`와 `padStart()` 를 쓴다.

```javascript
"hello".padStart(6);	// ' hello'

"hello".padEnd(6);	// 'hello '
```

여기서 패딩으로 `6`을 지정했는데 두 경우 모두 `1`개의 공간만 확보된 이유는 무엇인가?

- `"hello"`는 5글자이고 패딩은 `6` 으로 지정되었기 때문에 빈 공간이 `1`개만 남는다.
- `"hello".padStart(6);` 에서는 시작부분에 빈 공간 1개 채워 넣게 된다.
- `"hello".padEnd(6);` 에서는 마지막 부분에 빈 공간 1개 채워 넣게 된다.

<br>

```javascript
// 10 - 2 = 8 스페이스
"hi".padStart(10);			// '        hi'

// 10 - 6 = 4스페이스
"welcome".padStart(10);		// '   welcome'
```

<br>

### 18.1.1. padStart()와 오른쪽 정렬

문자열을 오른쪽 정렬하고 싶을 때 `padStart()`를 활용할 수 있다.

```javascript
const strings = ["short", "medium length", "very long string"];

const longestString = strings.sort(str => str.length).map(str => str.length)[0];

console.log(longestString); // 5

strings.forEach(str => console.log(str.padStart(longestString)));
// short
// medium length
// very long string
```

- `string.sort(str => str.length)` : 먼저 가장 긴 문자열을 찾아서 그 길이를 측정했다.

- 그런 다음 가장 긴 문자열의 길이를 기준으로 모든 문자열에 `padStart()`를 적용하면 모든 문자열을 완벽하게 오른쪽으로 정렬할 수 있다.

<br>

### 18.1.2. 패딩에 사용자 지정 값 추가

패딩은 공백을 추가하는 것뿐만 아니라 문자열이나 숫자를 덧붙이는 데에도 사용할 수 있다.

```javascript
"hello".padEnd(17, " OH TAE KWON");			// 'hello OH TAE KWON'

"1".padStart(3,0);			// '001'

"99".padStart(3,0);			// '099'
```
<br>

<br>

### :page_facing_up: 18.2. Object.entries()와 Object.values()

---

객체 내부의 값에 쉽게 접근하느 방법도 도입되었다. 먼저 다음과 같은 객체를 생성한다.

```javascript
const family = {
    father : "BTS",
    mother : "IU",
    son : "AKAMU",
};
```

이전 버전의 자바스크립트에서는 다음과 같은 방법으로 객체 내부의 값에 접근했다.

```javascript
Object.keys(family);	// (3) ['father', 'mother', 'son']

family.father;			// 'BTS'
```

즉 `Object.keys()`는 객체의 키만 반환하기 때문에, 값에 접근하기 위해서는 해당 키를 먼저 얻은 다음 그 키를 통해 값에 접근해야 했다.

<br>

##### `ES2017`에서 새롭게 도입된 객체에 접근 방법

```javascript
Object.values(family);			// (3) ['BTS', 'IU', 'AKAMU']

Object.entries(family);
/* 
  [
	["father", "BTS"],
	["mother", "IU"],
	["son", "AKAMU"]
  ]
*/
```

`Object.values()`는 **모든 값이 담긴 배열**을 반환하고, `Object.entries()`는 **키와 값**을 모두 포함하는 배열의 배열을 반환한다.

<br>

<br>
