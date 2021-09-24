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
