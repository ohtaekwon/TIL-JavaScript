# PART 1

###  :pencil: ***입문 014 :  반복문 배우기 - for in***

<br>

**for-in 반복문**은 앞에서 살펴본 *for* 반복문과 비슷하게 ***키워드*** 를 사용한다.  단, 순회조건과 내부 요소에 접근하는 방법에 차이가 있다. 

**for-in** 반복문은 **in** 키워드를 사용한다. **in** 키워드를 사이에 두고 오른쪽에는 반복할 대상 변수를, 왼쪽에는 속성명을 작성한다.

```javascript
for(속성명 in 반복할 대상){
    
}
```

##### :pencil: ​풀이

반복문을 통해 내부 요소를 하나씩 순회할 때마다, 각 요소의 키(Key) 정보가 *for in*에서 정의한 속성명으로 선언과 동시에 할당된다. 

```javascript
//-----※1. 변수 store에 리터럴 변수 선언
var store = {snack : 1000, flower : 5000, beverage : 2000};


//------※2. for in문 선언
for(var item in store){
    //-------※3. 
    if(!store.hasOwnProperty(item)) continue;
    //-------※4. 
    console.log(item + '는 가격이 ' + store[item] + ' 입니다.')
}

// snack는 가격이 1000 입니다.
// flower는 가격이 5000 입니다.
// beverage는 가격이 2000 입니다.
```

- `※1`, *store* 변수에 객체값을 할당한다.
- `※2`, *store* 객체를 순환하는 *for-in* 반복문이다. 변수 *item*은 *store* 객체의 요소를 접근하는 속성이다. 
- `※3`, *for-in* 반복문으로 내부 요소 정보가 전달되어 코드가 실행된다. 매 반복마다 `hasOwnProperty`를 이용하여 *store* 객체에 *item* 키 정보가 있는지 확인한다. 
  - 없으면, **continue**를 통해 아래 코드는 실행하지 않고 다음 순서로 넘어간다. 
  - *for-in*반복문을 사용할 때는 `hasOwnProperty`를 통해 객체 안에 속성이 있는지 한 번 더 확인한다. 
- `※4`, 정상적으로 접근한 요소에 대해 출력한다. *item*에는 순회하며 접근한 각 요소의 속성명(키 정보)이 순서대로 `snack`, `flower`, `beverage`가 할당된다.

<br>

---

<br>

### _:diamond_shape_with_a_dot_inside: 참고_

# Object.prototype.hasOwnProperty()

`hasOwnProperty()` 메소드는 객체가 특정 프로퍼티를 가지고 있는지를 나타내는 불리언 값을 반환한다.

```javascript
const object1 = {};
object1.property1 = 42;

console.log(object1.hasOwnProperty('property1'));
// expected output: true

console.log(object1.hasOwnProperty('toString'));
// expected output: false

console.log(object1.hasOwnProperty('hasOwnProperty'));
// expected output: false

```

##### :pencil: ​구문

```javascript
obj.hasOwnProperty(prop)
```

<br>

##### :pencil: ​매개변수

##### 1.**prop**

: 테스트하려는 프로퍼티의 명칭

<br>

##### :pencil: ​설명

모든 객체는 `hasOwnProperty` 를 상속하는 `Object`의 자식이다. 이 메소드는 객체가 특정 프로퍼티를 자기만의 직접적인 프로퍼티로서 소유하고 있는지를 판단하는데 사용된다.  `in`연산과는 다르게, 이 메소드는 객체의 프로토타입 체인을 확인하지는 않는다.

