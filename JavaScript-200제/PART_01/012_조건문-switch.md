# PART 1

###  :pencil: ***입문 012 :  조건문 배우기 - switch***

<br>

```javascript
switch(표현식){
    case 값1:
        명령문1
        break;
    case 값2:
        명령문2
        break;
    default:
        명령문3
}
```

<br>

 *if 조건문은 여러 조건문들이 중첩되어 사용된다.* 경우에 따라 **switch**를 사용하면 정돈된 코드를 만들 수 있다. 

**switch** 표현식 다음으로 **중괄호** `{}`로 뚤러싸인 블록안에는 `case`가 있다. switch의 표현식은 `case`의 값과 일치 여부를 확인하며, 이때 `===`일치 연산자를 사용한다.

`===`일치 연산자는 값과 자료형을 모두 비교하고, 결과값으로 *true* 또는 *false*를 반환한다.

여러개의 `case`가 있는 경우, 위에서부터 순차적으로 일치한 값이 나올 때까지 `case`값을 확인하며 내려간다. 그리고 `case`값이 일치하면 해당 명령문을 실행한다. `break`는 그 다음의 코드들을 더이상 실행하지 않고 `switch` 조건문을 끝내는 역할을 수행한다. 

만약 일치하는 `case`값이 없는 경우 마지막 `default`로 선언된 명령문이 실행된다.

<br>

```javascript
var subject ='자바스크립트';

switch(subject){
    case 'C언어':
        console.log(`과목은 ${subject} 입니다.`);
        break;
    case '자바스크립트':
        console.log(`과목은 ${subject} 입니다.`);
        break;
    case '파이썬':
        console.log(`과목은 ${subject} 입니다.`);
        break;
    default:
        console.log(`요청하신 ${subject}가 없습니다.`)
        break;
}
// 과목은 자바스크립트 입니다.
```


