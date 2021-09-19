#  CHAPTER 03

###  :pencil: ***함수 기본값 인수***
<br>

### :page_facing_up: 3.1. 함수 인수의 기본값(ES6 이전)

---

`ES6`이전에는 함수 인수의 **기본값**(default value)을 설정하는 것이 쉽지 않았다.

```javascript
function getLocation(city, country, continent){
    if(typeof country === 'undefined'){
        country = 'Italy';
    }
    if(typeof continent === 'undefined'){
        continent = 'Europe';
    }
    console.log(continent, country, city);
}

getLocation('Milan');	// Europe Italy Milan
getLocation('Paris', 'France');	// Europe France Paris
```

위의 함수는 `city`, `country`, `continent` 세 가지 인수를 취한다. 함수 본문에서 `country` 또는 `continent` 가 정의되지 않았는지 확인하고, 정의되지 않은 경우에만 기본값을 제공하는 것이 이 코드의 내용이다.

`getLocation('Milan')`이라고 호출하면 두 번째, 세 번째 매개변수(`country`와 `continent`)는 정의되지 않았으므로 함수의 기본값으로 대체된다.

<br>

_그러나 기본값이 인수 목록의 끝이 아닌 시작 부분에 있도록 하려면 어떻게 해야하나?_

```javascript
function getLocation(continent, country, city){
    if(typeof country === 'undefined'){
        country = 'Italy';
    }
    if(typeof continent === 'undefined'){
        continent = 'Europe';
    }
    console.log(continent, country, city);
}
getLocation(undefined, undefined, 'Milan');		// Europe Italy Milan
getLocation(undefined, 'Paris', 'France');	// Europe Paris France
```

첫 번째 인수를 기본값으로 바꾸기 위한 깔끔한 방법은 없다. 다닞 인수로 **undefined**값을 전달한다. 

그러나 `ES6`에서는 **함수 기본값 인수**(default function argument)를 제공한다.

<br>

<br>

### :page_facing_up: 3.2. 함수 기본값 인수

---

`ES6`에서는 함수 기본값 인수를 쉽게 설정할 수 있다.

```javascript
function calculaterPrice(total, tax = 0.1, tip = 0.05){
    // tax나 tip에 값을 할당하지 않으면 기본값으로 0.1과 0.05가 쓰인다.
    return total + (total*tax) + (total * tip);
}
```

매개변수를 아예 전달하지 않으려면 어떻게 해야할까?

```javascript
// tip에 0.15를 할당하려 했지만, 아래처럼 쓰면 0.15는 두 번째 인수 tax에 할당된다.
calculatePrice(100, 0.15)

// 이렇게 쓰면 tip에 0.15를 할당하게 된다.
calculaterPrice(100, undefined, 0.15); // 125
```

<br>

**디스트럭처링**(destructuring)을 통해 코드를 깔끔하게 바꿀 수 있다.

```javascript
function calculatePrice({total = 0, tax = 0.1, tip = 0.05,} = {}){
    return total + (total * tax) + (total * tip);
}

const bill = calculatePrice({tip:0.15, total: 150});
bill	// 187.5
```

함수의 인수를 **객체**로 만들었다. 함수를 호출하면 매개변수가 주어진 키에 맞춰서 입력되기 때문에 매개변수의 순서에 대해 걱정할 필요가 없다. ]

**tip**의 기본값은 `0.05`지만 `0.15`로 덮어 썼다. **tax**는 값을 덮어 쓰지 않아 기본값인 `0.1`로 유지한다.

<br>

이 코드에서 다음 부분에 주의한다.

```javascript
{total = 0, tax = 0.1, tip = 0.05,} = {}
```

여기서 인수 객체를 **빈 객체**로 설정하지 않고 (즉, = `{}`를 빼고) 선언한 다음 아무 매개변수도 없이 **calculatePrice()**를 실행하면 오류가 발생한다.

- `Cannot destructure property 'total' of 'undefined' or 'null'.`

`={}`를 추가해야 인수를 기본적으로 객체로 설정할 수 있다. 

함수에 매개변수를 어떻게 전달하든 상관없이 인수는 객체가 된다.

```javascript
calculatePrice({});			// 0

calculatePrice();			// 0

calculatePrice(undefined);	// 0
```

인수로 무엇을 전달했든지 상관없이 `total`, `tax`, `tip` 세 가지 기본 속성을 가진 객체로 기본 설정되었다.

<br>

#### _ex) `={}` 가 없는 코드의 결가와 비교._

```javascript
// 1. ={}가 있는 경우
function calculatePrice({total = 0, tax=0.1, tip=0.05,}={}){
    return total + (total*tax) + (total*tip);    
}
calculatePrice({});			// 0
calculatePrice();			// 0
calculatePrice(undefined);	// 0


// 2. ={}가 없는 경우
function calculatePrice({total=0, tax=0.1, tip=0.05,}){
    return total + (total*tax) + (total*tip);
}
calculatePrice({});	// 0
calculatePrice();	
// Cannot read properties of undefined (reading 'total') at calculatePrice
calcuatePrice(undefined);
// ReferenceError: calcuatePrice is not defined
```
<<<<<<< HEAD
=======
>>>>>>> c8df22a37ac640cc6605affd6fe94aad79f6536d

