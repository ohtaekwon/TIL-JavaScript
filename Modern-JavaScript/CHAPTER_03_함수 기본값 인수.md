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


