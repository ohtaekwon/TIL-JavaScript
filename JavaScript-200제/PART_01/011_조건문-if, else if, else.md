# PART 1

###  :pencil: ***입문 011 :  조건문 배우기 - if, else if, else***

<br>

**else if**와 **else**는 if의 결과값이 `false`일 때 추가 실행되는 조건문이다.

`==`는 **동등 연산자**이다. `==`를 가운데 두고 왼쪽과 오른족의 값을 비교한다. 동등 여부에 따라 결과값은 **true** 혹은 **false**를 반환한다.

<br>

```javascript
var number = 2;	//----------(※1)
if(number==1){	//----------(※2)
    console.log(`number는 ${number}입니다.`);
} else if (number==2){
    console.log(`number는 ${number}입니다.`);
} else if (number==3){
    console.log(`number는 ${number}입니다.`);
} else {
    console.log(`number는 1, 2, 3중 해당되는 값이 없습니다.`);
}

// number는 2입니다.
```

- `※1` , 변수 number에 숫자 2를 대입하여 선언한다.
- `※2`,  변수 number가 숫자 1과 동일하면 3라인을 실행하는 **if 조건문**이다
- `else if`로 첫 번째 조건문을 충족하지 않는 경우 다른 조건문을 추가할 수 있다. 변수 number에 대입된 값이 2이기 때문에 `number == 2`인 조건문은 *true*를 충족하고 다음 라인이 실행된다. 
- 변수 *number*의 값이 3과 동일하면 `number==3`이 실행된다. 하지만, 이미 `number==2`의 조건문을 충족했기 때문에 실행되지 않는다.

<br>

```javascript
if(표현식1){
    명령문1
} else if(표현식2){
    명령문2
} else if(표현식3){
    명령문3
} else {
    명령문4
}
```

`else if`는 *if 조건문* 외에 추가적으로 조건식을 추가하고 싶을 떄, if의 조건문 뒤에 덧붙여 사용한다.
