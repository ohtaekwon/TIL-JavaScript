# _CHAPTER 1-1_

###  :pencil: ​_문제 006 : False_

다음은 자바스크립트 문법 중에서 False로 취급하는 것들 이다.

False로 취급하지 않는 것이 하나 존재한다. True를 찾아보시오.

> **1 ) NaN**
>
> **2 ) 1**
>
> **3 ) ""**
>
> **4 ) 0**
>
> **5 ) undefined**

<br>

:ballot_box_with_check: **풀이 해석**

```javascript
console.log(!); 
/* 
	!뒤에 있는 값이 ture이면, false를 반환하고,
	!뒤에 있는 값이 false이면, true를 반환한다.
	거꾸로 true인지 false인지 반환한다.
*/
            
console.log(!1234); 	// false를 반환 즉, true (자바스크립트에서 숫자값은 true값)
console.log(!0); 		// true를 반환 즉, false (자바스크립트에서 0은 false값)
console.log(!"");		// true를 반환 즉, false
console.log(!NaN); 		// true를 반환 즉, false
console.log(!false);	// true를 반환 즉, false (boolean값은 false)
console.log(!null);   	// true를 반환 즉, false
console.log(!undefined);// true를 반환 즉, false        
```

<br>

---

<br>

### :diamond_shape_with_a_dot_inside: 추가 학습

###  :one: ​NaN 과 isNaN 메서드

- `NaN`은 Not a number의 약자 즉, 숫자가 아니다라는 말이다.
- 숫자가 아닌 것을 알 수 있는 방법으로는 isNaN()이라는 메서드를 활용한다.
  - 의미로는 "숫자가 아닌 것이 맞지?"라는 의미이다.
  - 즉, 숫자가 맞으면 false를 반환
  - 숫자가 아니면 true를 반환
  - EX) console.log(isNaN(1)); 은 false를 반환한다.