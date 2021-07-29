# _CHAPTER 1-4_

###  :pencil: ​_문제 034 :  sort 구현하기_

태권이는 체육부장으로 체육시간이 되면 반 친구들이 제대로 키 순서대로 모였는지를 확인해야 한다, 그런데 요즘 태권이는 그것이 너무 번거롭게 느껴져 한 번에 확인하고 싶어한다.

**태권이를 위해 키가 주어지면 순서대로 제대로 섰는지 확인하는 프로그램**을 작성해보자.
(단, 키는 공백으로 구분하여 입력된다.)

<br>

:desktop_computer: ***1.1. 입력***

```javascript
176 156 155 165 166 169
```

:desktop_computer: ***1.2. 출력***

```javascript
NO
```

<br>

 ***1.1. 입력***

```javascript
155 156 165 166 169 176
```

:desktop_computer: ***1.2. 출력***

```javascript
YES
```

<br>

:ballot_box_with_check: **풀이 코드  : 소스**

```javascript
// 1. 입력받을 변수를 선언
const unsorted = "176 156 155 165 166 169";

// 2. 정렬시킬 변수를 선언
let sorted = ""; // 정렬이 되고 난 후의 데이터를 초기화 바뀔 것이기 때문에 let으로 선언

// 3. 
console.log(unsorted.split(" "));	// (6) ['176', '156', '155', '165', '166', '169']

// 4. 
console.log(unsorted.split(" ").sort()); // (6) ['155', '156', '165', '166', '169', '176']

// 5.
unsorted.split(" ").sort(function(a,b){
   console.log(a,b);
    return a - b;
});
```





<br>

---

<br>

### :diamond_shape_with_a_dot_inside: 추가 학습

###  :one: String.prototype.toUpperCase()

