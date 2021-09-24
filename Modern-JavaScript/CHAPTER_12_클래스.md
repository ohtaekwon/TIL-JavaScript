#  CHAPTER 12

###  :pencil: ***클래스***

<br>

MDN에서 **클래스(class)**를 다음과 같이 설명한다.

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
