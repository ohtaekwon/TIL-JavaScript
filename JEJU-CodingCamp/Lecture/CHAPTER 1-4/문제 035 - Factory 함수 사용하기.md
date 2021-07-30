# _CHAPTER 1-4_

###  :pencil: ​_문제 035 :  Factory 함수 사용하기_

2제곱, 3제곱, 4제곱을 할 수 있는 Factory 함수를 만들려고 합니다.

:desktop_computer: ***<pass> 에 코드를 작성하여 two함수를 완성하시오***

```javascript
function one(n){
    function two(){ // 함수가 함수를 리턴
        // pass
    }
    return two;
}
const a = one(2);
const b = one(3);
const c = one(4);

console.log(a(10));
console.log(b(10));
console.log(c(10));
```

<br>

:ballot_box_with_check: **풀이 코드  : 소스**

```javascript
function one(n){ // n으로 받고 있기 때문에
    function two(x){ // two함수에서는 n을 이용해주면 된다.
        // pass
        
        // 제곱의 결과를 반영해주는 메소드 : Math.pow()
        return Math.pow(x, n); // x의 n 제곱을 나타내는 메소드
        
    }
    return two;
}
// 매개변수를 통해서 제곱이 제곱인지 세제곱인지 네제곱인지 결정해야한다.
const a = one(2);			
const b = one(3);
const c = one(4);

console.log(a(10));			// 100
console.log(b(10));			// 1000
console.log(c(10));			// 10000
```



- 매개변수를 통해서 다른 기능을 하는 factory함수

<br>

---

<br>

### :diamond_shape_with_a_dot_inside: 추가 학습

# 자바스크립트에서 팩토리 함수

### :one: Factory Function

_**팩토리 함수**는 (새로운)객체를 리턴하는 함수이다._ 그러나 클래스나 생성자 함수는 아니다. JavaScript에서는 모든 함수가 객체를 리턴할 수 있다. 이 때, `new` 키워드가 없으면 팩토리 함수이다.

JavaScript에서 팩토리 함수는 클래스와 `new` 키워드의 복잡함 없이 객체 인스턴스를 쉽게 생성 할 수 있다. JavaScript는 매우 유용한 객체 리터럴 구문을 제공합니다. 다음과 같습니다.

```javascript
const user = {  
  userName: 'echo',  
  avatar: 'echo.png'  
};
```

자바 스크립트의 객체 리터럴 표기법은 JSON과 마찬가지로 `:` 의 ***왼쪽은 속성의 이름이고 오른쪽은 값입니다.*** 점 표기법으로 속성에 액세스 할 수 있습니다.

```javascript
console.log(user.userName); // "echo"
```

