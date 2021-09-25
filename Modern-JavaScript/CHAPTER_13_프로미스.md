#  CHAPTER 13

###  :pencil: ***프로미스***

자바스크립트는 **동기적(synchronous)** 으로 작동한다. 즉, 각 코드 블록이 이전 블록 이후에 실행된다.

```javascript
const data = fetch('your-api-url-goes-here');
console.log('Finnished');	// Finnished
console.log(data);		// undefined
```

여기서 `fetch`를 사용하여 어떤 URL에서 데이터를 가져온다.

동기 코드의 경우, `fetch`작업이 실제로 완료된 후에 다음 행이 호출되라고 예상한다. 

하지만, 실제로는 `fetch`가 호출된 직후 바로 다음 행에 있는 두 `console.log()`도 실행되므로, 마지막 `console.log(data)`는 **undefined**를 출력한다.

이러한 현상이 발생하는 이유는 `fetch`가 **비동기적(asynchronius)**으로 수행되기 때문이다.

- 즉, 해당 행에서 `fetch`가 완료될 때까지 코드 실행을 중지하는 게 아니라 계속해서 다음 행을 실행한다.

이 문제를 해결하기 위해 **콜백** 또는 **프로미스**를 사용하면 `fetch`가 무언가를 반환하는 시점까지 기다리게 할 수 있다.

<br>

<br>

### :page_facing_up: 13.1. 콜백 지옥

---

비동기 코드를 동기식으로 작동하는 것처럼 하기 위해 **콜백(callback)** 으로 여러 코드 블록을 차례로 연결해 작성할 때 발생하는 상황을 **콜백 지옥(callback hell)** 이라고 부른다.

다시 말하자면,

`A`를 하고, `A`가 완료될 때까지 기다렸다가 `B`를 수행하고, `B`가 완료될 때까지 기다렸다가 `C`를 수행하고, 이러한 방식으로 계속한다.

이런 코드에서는 기다리는 사람마다 콜백을 사용해야 하기 때문에 코드가 복잡해진다.

<br>

#### _ex) 콜백 지옥_

피자를 준비하는 각 단계마다 서버에 요청을 보내야 하고 서버가 응답할 때까지 기다렸다가 다음 단계를 수행해야 하는 비동기적인 상황이다.

```javascript
const makePizza = (ingredients, callback) => {
    mixIngredients(ingredients, function(mixIngredients)){
      bakePizza(mixedIngredients, function(backedPizza)){
        console.log('finished');
    }
  }
};
```

이렇게 하면 시각적으로 위에서 아래로 코드가 실행되는 것처럼 보이게 작성할 수는 있지만, 그것 때문에 과도한 **함수 중첩**을 유발한다.

- 콜백 지옥을 개선하는 방법 : https://callbackhell.com  을 참고

<br>

<br>
