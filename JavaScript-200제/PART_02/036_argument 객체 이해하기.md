# PART 2

###  :pencil: ***입문 036 :  arguments 객체 이해하기***

<br>

자바스크립트 함수는 **매개변수**를 가진다. 여기서 **매개변수**와 같이 사용되는 용어가 있는데 바로 **전달 인자** **(argument)**이다. 매개변수가 함수 선언 시 작성되는 변수라면, 전달 인자는 함수가 호출될 때 전달되는 값이다. 

<br>

자바스크립트는 전달 인자의 개수와 매개변수의 개수가 달라도 **에러**를 발생하지 않는다. 그래서 매개변수와 무관하게 함수 호출 시 더 많은 인자를 전달할 수 있다. 매개변수 외에 _함수에서만 사용 가능한 특별한 객체를 제공_한다. 바로 **argument** 객체이다.

<br>

# arguments 객체

`arguments` 객체는 함수에 전달된 인수에 해당하는 `Array` 형태의 객체이다.

```javascript
function func1(a, b, c) {
  console.log(arguments[0]);
  // expected output: 1

  console.log(arguments[1]);
  // expected output: 2

  console.log(arguments[2]);
  // expected output: 3
}

func1(1, 2, 3);
```

<br>

## 설명

`arguments` 객체는 모든 함수 내에서 이용 가능한 **지역 변수**이다. `arguments` 객체를 사용하여 함수 내에서 모든 인수를 참조할 수 있으며, 호출할 때 제공한 인수 각각에 대한 항목을 갖고 있습니다. 항목의 인덱스는 0부터 시작합니다.

예를 들어, 함수가 세 개의 인수를 받은 경우 다음과 같이 접근할 수 있습니다.

```javascript
arguments[0]
arguments[1]
arguments[2]
```

각 인수를 설정하거나 재할당할 수도 있다.

```javascript
arguments[1] = 'new value';
```



<br>

```javascript
// 1.
function sum(){
    var total = 0;
    for(var i=0; i<arguments.length; i++){
        total += arguments[i];
    }
    // 1-1.
    console.log(arguments instanceof Array);
    return total;
}

// 2.
var sumOf1to3 = sum(1, 2, 3);
console.log(sumOf1to3);					// false
										// 6



function testArg(){
    // 3.
    var newArr = Array.prototype.slice.call(arguments);
    console.log(newArr);
    // 3-1.
    console.log(newArr.indexOf('b'));
    // 3-2.
    console.log(arguments.indexOf('b'));
}
testArg('a', 'b');
```

- `1.` `sum`함수를 정의하면서 내부에 **argument** 객체를 통해 전달된 인자의 합을 반환한다. **argument** 객체는 배열과 유사하게 인덱스를 통해 접근할 수 있다. 
  - 하지만, *length* 속성 외에는 배열의 어떠한 속성과 메소드를 가지고 있지 않다. 
- `1-1.` *instanceof* 연산자를 이용하여 *arguments* 객체가 배열이 아닌 것을 확인할 수 있다.
- `2.` `sum` 함수는 매개변수를 정의하고 있지 않지만, 전달 인자로는 `1`, `2` ,`3`을 전달하고 있다. 
  - 이때 별도의 에러가 발생하지 않는다.
- `3.` *arguments* 객체를 배열로 바꾸기 위해 배열의 프로토타입에 정의된 *slice* 메소드를 호출한다. 이렇게 하면 *arguments* 객체의 요소들을 복사하는 새로운 배열이 만들어진다. 
- `3-1.` 배열이기 때문에 *indexOf* 메소드를 사용하면 문자열 `b`의 인덱스를 반환한다. 
- `3-2.` *arguments* 객체는 배열이 아니기 때문에 에러가 발생한다. 




