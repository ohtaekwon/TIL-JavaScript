#  CHAPTER_03_Quiz

###  :pencil: ***함수 기본값 인수***

<br>

<br>

### 3.1. 다음 작업을 수행하는 코드를 작성해보자.

### 다음 코드에서 arg1과 arg2를 변경하여 첫 번째는 tax를 나타내고, 두번 째는 tip의 값을 나타내게 만들어보기.

`tax`에는 기본값 `0.1`을 지정하고 `tip`에는 기본값 `0.05`를 지정하자.

```javascript
function calculatePrice(total, arg1, arg2){
    return total + (total * tax) + (total * tip);
}

calculaterPrice(10);	// 예상 결과 : 11.5
```

<br>

#### 풀이

```javascript
function calculatePrice(total, tax=0.1, tip=0.05){
    return total + (total * tax) + (total * tip);
}

calculatePrice(10);	// 예상 결과 : 11.5
```

<br>

---

<br>

### 3.2. 다음 코드의 올바른 출력은? 답 : 1

```javascript
var b = 3;
function multiply(a, b=2){
    return a * b;
}
console.log(multiply(5));
```

`1.`  2

`2.`  5

`3.`  10

`4.`  15

<br>

#### 풀이

```javascript
var b = 3;	// global scope

function multiply(a, b=2){
    return a * b; // a = 5, b = 2 함수의 인자는 b = 2를 나타내므로 블록범위 내에서는 b = 2
}
console.log(multiply(5));		// 10
```

