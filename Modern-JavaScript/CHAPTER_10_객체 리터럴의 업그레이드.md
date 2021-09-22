#  CHAPTER 10

###  :pencil: ***객체 리터럴의 업그레이드***

<br>

### :page_facing_up: 10.1. 변수를 키와 값으로 하는 객체 만들기

---

```javascript
const name = "TAEKWON";
const surname = "OHT";
const age = 30;
const nationality = "KOREA";
```

이 코드를 이용하여 **객체 리터럴**을 만들기 위해서는 일반적인 방법으로는 다음과 같이 한다.

```javascript
const person = {
    name : name,
    surname : surname,
    age : age,
    nationality : nationality,
};

console.log(person);	
// {name: 'TAEKWON', surname: 'OHT', age: 30, nationality: 'KOREA'}
```

<br>

`ES6`에서는 단수화할 수 있다.

```javascript
const person = {
    name,
    surname,
    age,
    nationality,
};
console.log(person);
// {name: 'TAEKWON', surname: 'OHT', age: 30, nationality: 'KOREA'}
```

변수들의 이름이 코드 내의 속성과 같이 동일하기 때문에 코드 내에서 굳이 두번씩 표기 하지 않아도 된다.

<br>

<br>
