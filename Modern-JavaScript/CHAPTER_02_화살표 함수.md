#  CHAPTER 02

###  :pencil: ***화살표 함수***

<br>

<br>

### :page_facing_up: 2.1. 화살표 함수

---

`ES6` 에서 뚱뚱한 화살표`=>`를 사용해서 함수를 선언하는 방법인 **화살표 함수**가 처음 도입되었다. 

<br>

1) `ES5`에서 일반적으로 함수를 선언하는 방법은 다음과 같다.

```javascript
const greeting = function(name){
    return "hello" + name;
};	// undefined
```

<br>

2) 이를 화살표 함수 문법으로 바꾸면

```javascript
var greeting = (name) => {
    return `hello ${name}`;
};
```

<br>

3) **매개변수가 하나**만 있으면 괄호를 생략할 수 있다.

```javascript
var greeting = name => {
    retrun `hello ${name}`;
};
```

<br>

4) 매개변수가 전혀 없으면 빈 괄호를 써야 한다.

```javascript
var greeting = () => {
    return "hello";
};
```

<br>

<br>
