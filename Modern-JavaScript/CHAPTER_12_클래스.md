#  CHAPTER 12

###  :pencil: ***클래스***

<br>

MDN에서 **클래스(class)** 를 다음과 같이 설명한다.

​	**클래스**는 일차적으로 자바스크립트의 기존 **프로토타입(prototype)기반** 상속에 대한 문법적 설탕(syntax sugar)이다. 클래스 문법이 자바스크립트에 새로운 객체 지향 상속 모델을 도입하는 것은 아니다.

#### _ex) 프로토타입 상속_

```javascript
function Person(name, age){
    this.name = name;
    this.age = age;
}

Person.prototype.greet = function(){
    console.log("Hello, my name is " + this.name);
}

const OHTAEKWON = new Person("OHTAEKWON", 26);
const BTS = new Person("BTS", 26);

OHTAEKWON.greet();
// Hello, my name is OHTAEKWON

BTS.greet();
// Hello, my name is BTS
```

`Person` 의 프로토타입에 새 메서드를 추가해서 `Person` 객체의 인스턴스들이 접근할 수 있도록 설정했다.

<br>

<br>

### :page_facing_up: 12.1. 클래스 생성

---

클래스를 만드는 방법에는 두 가지가 있다. 

- 클래스 선언
- 클래스 표현식

```javascript
// 클래스 선언
class Person {
    
}

// 클래스 표현식
const person = class Person{
    
};
```

클래스 선언 및 클래스 표현식은 **호이스팅되지 않는다.** 클래스에 접근하기 전에 클래스를 선언하지 않으면 `ReferenceError`가 발생한다.

<br>

**생성자 메서드**를 추가한 것을 제외하면 프로토타입 방식과 큰 차이가 없다. 

- 생성자를 하나만 추가해야 함에 주의해야 한다.
- 클래스에 생성자 메서드가 두 개 이상 포함된 경우 `SyntaxError`가 발생한다.

```javascript
class Person {
    constructor(name, age){
        this.name = name;
        this.age = age;
    }
    greet(){
        console.log(`Hi, my name is ${this.name} and I'm ${this.age} years old`);
    }	// 메서드와 메서드 사이에는 쉼표가 없다.
    fareWell(){
        console.log("Gooooood bye bro~");
    }
}

const OHTAEKWON = new Person("OHTAEKWON", 30);

OHTAEKWON.greet();	// Hi, my name is OHTAEKWON and I'm 30 years old

OHTAEKWON.farewell();	// Gooooood bye bro~
```

모든 것이 이전과 동일하게 작동한다. 즉, 클래스는 프로토타입 방식을 대신하는 문법적 설탕이라 할 수 있다.

<br>

<br>

### :page_facing_up: 12.2. 정적 메서드

---

앞의 예시에서 추가한 `greet()`와 `farewell()` 메서드는 `Person 클래스`의 모든 인스턴스에서 접근할 수 있다. 

하지만, `Array.of()`처럼 클래스의 인스턴스가 아닌 클래스 자체에서 접근할 수 있는 **정적 메서드**는 다음과 같이 정의한다.

```javascript
class Person{
    constructor(name, age){
        this.name = name;
        this.age = age;
    }
    static info(){
        console.log("I am a Person class, nice to meet you");
    }
}

const TAEKWON = new Person("TAEKWON", 30);

TAEKWON.info(); // TypeError: TAEKWON.info is not a function

Person.info();	// I am a Person class, nice to meet you
```

- **static** 키워드는 클래스의 정적 메서드를 정의한다. 따라서, 클래스의 인스턴스 없이 호출하며 클래스가 인스턴스화되면 호출할 수 없다.

<br>

# static

**static** 키워드는 클래스의 정적 메서드를 정의한다. 

정적 메서드는 클래스의 인스턴스 없이 호출이 가능하며 클래스가 인스턴스화되면 호출할 수 없다. 정적 메서드는 종종 어플리케이션의 유틸리티 함수를 만드는데 사용된다.

<br>

<br>

### :page_facing_up: 12.3. set와 get

---

**세터(setter)** 와 **게터(getter)** 메서드를 사용하여 클래스 내에 값을 설정하거나 가져올 수 있다.

```javascript
class Person{
    constructor(name, surname){
        this.name = name;
        this.surname = surname;
        this.nickname = "";
    }
    
    set nicknames(value){
        this.nickname = value;
        console.log(this.nickname);
    }
    get nicknames(){
        console.log(`Your nickname is ${this.nickname}`);
    }
}

const TAEKWON = new Person("TaeKwon", "OH");

// 세터를 호출
TAEKWON.nickname = "TK";		// 'TK'

// 게터를 호출
TK.nickname;					// Your nickname is TK
```

- `getter 메서드`는 `TAEKWON.nicknames`을 사용해 프로퍼티를 읽으려고 할 때 실행됩니다.
- `setter 메서드`는 `TAEKWON.nicknames=vlaue`으로 프로퍼티에 값을 할당하려 할 때 실행됩니다.

<br>

<br>

### :page_facing_up: 12.4. 클래스 상속하기

---

기존 클래스로부터 상속된 새로운 클래스를 만들려면 `extends` 키워드를 사용한다.

```javascript
// 기존 클래스
class Person{
    constructor(name,age){
        this.name = name;
        this.age = age;
    }
    greet(){
        console.log(`Hi, my name is ${this.name} and I'm ${this.age} years old`);
    }
}

// 상속을 통해 만든 새 클래스
class Adult extends Person{
    constructor(name, age, work){
        this.name = name;
        this.age = age;
        this.work = work;
    }
}

const TK = new Adult("TAEKWON", 30, "softWare developer");

// ReferenceError: Must call super constructor in derived class before accessing 'this' or returning from derived constructor
```

`Person`을 상속하는 `Adult` 클래스를 만들었지만 이 코드를 실행하려고 하면 오류가 발생한다.

```
ReferenceError: Must call super constructor in derived class before accessing 'this' or returning from derived constructor
```

오류 메시지는 새로운 클래스에서 `this`를 사용하기 전에 `super()`를 호출하라는 내용이다. 

- 즉, `Adult`를 만들기에 앞서 `Person`을 만들어야 한다는 것이다. 
- 생성자 내부에서 `super()`를 호출하면 `Person`이 만들어진다.

```javascript
class Adult extends Person{
    constructor(name, age, work){
        super(name, age);
        this.work = work;
    }
}
```

여기서 _왜 `super(name, age)` 형태로 호출하였을까?_

- `Adult` 클래스는 `Person`으로 부터 이름과 나이를 상속받기 때문에 `Person`을 다시 선언하고 초기화할 필요가 없다. `super()` 생성자가 하는 일이 바로 그것을 의미한다.

<br>

#### _수정된 코드_

```javascript
// 기존 클래스
class Person{
    constructor(name,age){
        this.name = name;
        this.age = age;
    }
    greet(){
        console.log(`Hi, my name is ${this.name} and I'm ${this.age} years old`);
    }
}

// 상속을 통해 만든 새 클래스

class Adult extends Person{
    constructor(name, age, work){
        super(name, age);
        this.work = work;
    }
}

const TK = new Adult("TAEKWON" , 30, "softWare Developer");

console.log(TK.name);	// TAEKWON
console.log(TK.age);	// 30
console.log(TK.work);	// softWare Developer
TK.greet(); 			// Hi, my name is TAEKWON and I'm 30 years old
```

`Adult` 는 `Person` 클래스의 모든 속성과 메서드를 상속했음을 볼 수 있다.

<br>

<br>

### :page_facing_up: 12.5. 배열 확장하기

---

배열과 비슷하게 생겼지만 첫 번째 값은 교실 이름이고 나머지는 학생 이름과 학생 점수를 나타내는 `Classroom`이라는 새로운 클래스를 만들어 보시오. 이 클래스는 다음과 같이 사용할 수 있어야 한다.

```javascript
const myClass = new Classroom('1A',
     {name : "Tim", mark : 6},
     {name : "Tom", mark : 3},
     {name : "Jim", mark : 8}.
     {name : "John", mark : 10},
);
```

이러한 요구 사항을 만족시키는 새로운 클래스는 다음과 같이 **배열을 상속받아서 만들 수 있다.**

```javascript
class Classroom extends Array{
    // 레스트 연산자를 사용해 가변 인수로 입력 받은 학생들의 정보를
    // 배열 형태로 students에 할당한다.
    constructor(name, ...students){
        // 스프레드 연산자를 사용해 배열 원소들을 다시 풀어헤쳐 생성자를 호출한다.
        // 스프레드 연산자를 사용하지 않으면
        // '학생들의 정보가 들어 있는 배열'을 원소로 가진 Array가 생성될 것이다.
        super(...students);
        this.name = name;
    }
    
    // 학생을 추가하기 위한 새로운 메서드를 추가
    add(student){
        this.push(student);
    }
}

const myClass = new Classroom('1A',
     {name : "Tim", mark : 6},
     {name : "Tom", mark : 3},
     {name : "Jim", mark : 8},
     {name : "John", mark : 10},
);

// 새로운 학생 추가
myClass.add({name : "Timmy", mark 7});
myClass[4];	// {name: 'Timmy', mark: 7}

// for of 루프를 사용하여 반복 가능
for(const student of myClass){
    console.log(student);
}
// {name: 'Tim', mark: 6}
// {name: 'Tom', mark: 3}
// {name: 'Jim', mark: 8}
// {name: 'John', mark: 10}
// {name: 'Timmy', mark: 7}
```


