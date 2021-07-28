# _APPENDIX 01 - 생성자와 new_

### :one: 객체

_객체란 서로 연관된 변수와 함수를 그룹핑한 그릇이라고 할 수 있다._

 객체 내의 변수를 프로퍼티(property) 함수를 메소드(method)라고 부른다. 다음, 객체를 만들어보자.

```javascript
var person = {} // {} 이것은 비어있는 객체를 만드는 것이거, object라는 이름의 object를 만드는 것이다.

// 함수안에 담겨 있는 변수 = 프로퍼티
person.name = 'OHTAEKWON';

// 프로퍼티에 함수가 담겨있다. = 메소드
person.introduce = function(){ 
    return 'My name is ' + this.name;
}
document.write(person.introduce());
```

- object는 객체랑 같은 말 
  - 객체는 어떠한 데이터를 담을 수 있는 비어있는 상자라고 보면 된다.
- 객체에 담겨져 있는 변수를 프로퍼티라 한다.

<br>

집중도가 떨어지는 문제를 해결할 방법은



```javascript
var person = {
    'name' : 'OHTAEKWON',
    'introduce' : function(){
        return 'My name is ' + this.name;
    }
}
document.write(person.introduce());
```







person을 여러개 만들 때 

person1, person2, .....

중복이 발생 = 가독성이 떨어짐 = 유지보수 어려워짐

```javascript
var person = {
    'name' : 'KIM',
    'introduce' : function(){
        return 'My name is ' + this.name;
    }
}
document.write(person.introduce());

var person = {
    'name' : 'LEE',
    'introduce' : function(){
        return 'My name is ' + this.name;
    }
}
document.write(person.introduce());
```



해결방법 

생성자 NEW



생성자(constructor)는 객체를 만드는 역할을 하는 함수다. 자바스크립트에서 함수는 재사용 가능한 로직의 묶음이 아니라 객체를 만드는 창조자라고 할 수 있다.

![image-20210728045058067](C:\Users\태권\AppData\Roaming\Typora\typora-user-images\image-20210728045058067.png)

https://opentutorials.org/module/532/6570

