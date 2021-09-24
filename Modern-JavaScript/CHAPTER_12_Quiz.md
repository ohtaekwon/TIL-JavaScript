#  CHAPTER_12_Quiz

###  :pencil: ***클래스***

<br>

---

<br>

### 12.1. 클래스란? 답 : 3

`1.`  새로운 원시 자료형

`2.`  프로ㅌ타입 상속을 수행하기 위한 문법적 설탕

`3.`  새로운 유형의 배열

<br>

#### 풀이

***클래스란?***

**클래스**는 일차적으로 자바스크립트의 기존 **프로토타입(prototype)기반** 상속에 대한 문법적 설탕(syntax sugar)이다.

그러나,  문법이 자바스크립트에 새로운 객체 지향 상속 모델을 도입하는 것은 아니다.

<br>

---

<br>

### 12.2. 클래스를 선언하는 옳은 방법은? 답 : 3

`1.`  `const person = class Person{...};`

`2.` `const person = new class Person{...};`

`3.`  `class Person{....};`

<br>

#### 풀이

***클래스를 만드는 방법***

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

클래스에 접근하기 전에 클래스를 선언하지 않으면 `ReferenceError`가 발생한다.

<br>

---

<br>

### 12.3. 정적 메서드란?? 답 : 3

`1.`  변경할 수 없는 메서드

`2.`  클래스의 모든 인스턴스에 접근할 수 있는 메서드

`3.`  클래스 자체로 접근할 수 있는 메서드

<br>

#### 풀이

***정적메서드란?***

정적 메서드는 클래스의 인스턴스 없이 호출이 가능하며 클래스가 인스턴스화되면 호출할 수 없다. 정적 메서드는 종종 어플리케이션의 유틸리티 함수를 만드는데 사용된다.

<br>

---

<br>

### 12.4. 다음 코드의 올바른 출력은? 답 : 3

```javascript
class Person{
    constructor(name, age){
        this.name = name;
        this.age = age;
    }
}

class Adult extends Person{
    constructor(work){
        this.work = work;
    }
}

const my = new Adult('softwar developer');
console.log(my.work);
```

`1.`  "software developer"

`2.`  Error : age is not defined

`3.`  ReferenceError : Must call super constructor in derived class before accessing 'this'

<br>

#### 풀이

***클래스 상속하기***

클래스를 상속할 때 `super()`를 먼저 호출해야한다. 즉, 생성자 내부에서 `super()`를 호출하면 `Person`이 만들어진다.

```javascript
// 기존 클래스
class Person{
    constructor(name, age){
        this.name = name;
        this.age = age;
    }
}

// 상속을 통해 만든 새 클래스
class Adult extends Person{
    constructor(name, age, work){
        // Adult 클래스는 Person으로부터 이름과 나이를 상속받는다.
        // 따라서, Person을 다시 선언하고 초기화할 필요없다.
        // super() 생성자를 통해서 상속한다.
        super(name, age);
        this.work = work;
    }
}
const my = new Adult(undefined, undefined, "softwar developer");
console.log(my.work);	// softwar developer
```

<br>

---

<br>

### 12.5. 다음 작업을 수행하는 코드를 작성하자. 

#### 다음과 같이 클래스가 주어졌을 때 해당 클래스를 상속하여 work라는 새 속성을 가지는 Adult 클래스를 만들자.

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

// Person을 상속받아 새로운 속성을 추가한 클래스를 만들자
class Adult extends Person{
    constructor(name, age, work){
        super(name, age);
        this.work = work;
    }
}

const me = new Adult('TAEKWON', 30, 'S/W developer');
console.log(me.work);
// S/W developer

me.greet();
// Hi, my name is TAEKWON and I'm 30 years old
```

