#  CHAPTER_05_Quiz

###  :pencil: ***문자열 메서드***

<br>

---

<br>

### 5.1. 다음 코드의 올바른 출력은? 답 : 1

```javascript
const code = "ABCDEFGHI";
code.startsWith("DEF", 3);
```

`1.`  true

`2.`  false

<br>

#### 풀이

```javascript
const code = "ABCDEFGHI";
code.startsWith("DEF", 3); 	// true (3개 문자를 지나 검사를 시작한다.)
code.startsWith("DEF", 4); 	// false (4개 문자를 지나 검사를 시작한다. EFGHI이므로 false)
```

<br>

---

<br>

### 5.2. 다음 코드의 올바른 출력은? 답 : 2

```javascript
const code = "ABCDEF";
code.endsWith("def");
```

`1.`  true

`2.`  false

<br>

#### 풀이

```javascript
const code = "ABCDEF";
code.endsWith("def");		// endsWith 메서드는 대소문자 구별한다.
code.endsWith("DEF");		// true
```

<br>

---

<br>

### 5.3. 원하는 값을 출력하도록 코드의 구현을 완성하시오.

```javascript
let str = "Na";
let bat = "BatMan";

let batman = ...
console.log(batman);
// 예상 결과 : NaNaNaNaNaNaNaNaNaNaNaNa Batman
```

<br>

#### 풀이

```javascript
let str = "Na";
let bat = "BatMan";

let batman = str.repeat(10) + " " + bat;
console.log(batman);
// 예상 결과 : NaNaNaNaNaNaNaNaNaNaNaNa Batman
```


