# PART 1

###  :pencil: ***입문 015 :  반복문 배우기 - while***

<br>

**while 반복문**은 지시어 *while*로 시작한다. 그 다음 `소괄호()` 안에 조건식이 들어가는데, 이 조건식의 결과값은 *true* 또는 *false*만 가능하다. 그리고 조건식이 *true*를 만족하는 경우에만 `중괄호{}`안의 문장들이 실행된다. 

조건식이 *false*가 되면 더이상 반복 실행하지 않는다. *while*반복문에서도 **break**와 **continue**문을 사용할 수 있다. 

```javascript
while(조건식){
    반복하게 될 문장
}
```

<br>

**do-while 반복문**은 맨 앞에 위치한 지시어 *do*의 사전적 의미 그대로, 처음은 조건 결과와 상관없이 무조건 문장을 실행(**do**)합니다. 그리고 조건식의 결과값을 확인하고 다음의 흐름은 이전 *while*과 동일하다.

```javascript
do{
    반복하게 될 문장
} while(조건식) 
```

<br>

#### while의 활용

```javascript
// 1. 변수 hometown 선언
var hometown = [
    {name : '진', city: '과천'},
    {name : '남준', place:'일산', city:'고양'},
    {name : '호석', place:'광주', city:'전라도'},
    {name : '지민', place:'부산', city:'경상도'},    
];


// 2. 함수를 변수로 선언한다. 
var isHometown = function(h, name){
    console.log(`함수가 실행되었습니다. ${h.city} 도시에서 ${name}을 찾습니다.`);
    
    if(h.name === name){
        console.log(`${h.name}의 고향은 ${h.city} ${h.place} 입니다.`);
        return true;
    }
    return false;
}


// 3.
var h;
while (h=hometwon.shift()){ // shift()는 배열의 앞에서부터 값을 하나씩 빼내오는 함수이다.
    if(!h.name||!h.place||!h.city) continue;
    
    var result = isHometown(h, '호석');
    if(result) break;
}


var i = 0;
var names = ['남준', '정국', ' 윤기', '호섭'];
var cities = ['경기', '부산', '대구', '광주'];
do{
    hometown[i]={name:names[i], city:cities[i]};
    i++;
} while(i<4);

console.log(hometown);
```

- `1`. 변수 hometown을 선언한다. 변수에는 객체 자료형 요소가 4개 들어 있는 배열을 할당한다. 

- `2`. 인자값을 *h* 와 *name*을 받는 함수 `isHometown`을 선언한다.
  - 객체인 *h*의 *name*과 인자로 받은 *name*이 다른 경우, *false*를 반환하며 함수를 종료시킨다. 
  - 값이 동일하면 `console.log`를 출력하고 *true*를 반환한다.

- `3`. *shift()*는 배열의 앞에서부터 값을 하나씩 빼내오는 함수이다. 

  - ex) `[1,2]` 배열에 *shift()*가 실행되어 `1`이 방출되면, 해당 배열은 `[2]` 가 된다.

  *h* 변수에 `hometown.shiift()`로 반환된 값을 핳당하는 것과 동시에 할당된 값을 확인한다. *hometown*의 요소는 객체로 채워져 있어 값이 유효한 경우 **true**, 유효하지 않으면 **false**를 반환하고 이를 통해 반복문을 실행한다.


