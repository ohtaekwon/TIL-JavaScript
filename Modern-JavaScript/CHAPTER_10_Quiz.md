#  CHAPTER_10_Quiz

###  :pencil: ***객체 리터럴의 업그레이드***

<br>

---

<br>

### 10.1. 다음 코드를 더 간결하게 리팩터링하시오.

```javascript
const animal = {
    name : name,
    age : age,
    breed : breed,
};
```

<br>

#### 풀이

***변수를 키와 값으로 하는 객체 만들기***

```javascript
const animal = {
    name,
    age,
    breed,
};
```

<br>

---

<br>

### 10.2. 다음 코드의 올바른 출력은? 답 : 2

```javascript
const name = "myname";
const person = {
    [name] : "TAEKWON",
};
console.log(person.myname);
```

`1.`  name

`2.`  "TAEKWON"

`3.`  myname

`4.` "name"

<br>

#### 풀이

***객체의 속성을 동적으로 정의***

```javascript
const name = "myname";
const person = {
    [name] : "TAEKWON",
};
console.log(person.myname);
```

빈 객체를 생성하여 객체를 업데이트하지 않아도 된다.

<br>

---

<br>

### 10.3. 다음 코드의 올바른 출력은? 답 : 3

```javascript
const name = "myname";
const age = 27;
const favoriteColor = "Green";
const person = {
    name,
    age,
    color,
};
console.log(person.color);
```

`1.`  "Green"

`2.`  color

`3.` color is not defined

`4.` favoriteColor

<br>

#### 풀이

***변수를 키와 값으로 하는 객체 만들기***

```javascript
const name = "myname";
const age = 27;
const favoriteColor = "Green";
const person = {
    name,
    age,
    favoriteColor,
};
console.log(person.favoriteColor);	// green
```

키 값을 올바르게 코드해야 한다.

<br>
