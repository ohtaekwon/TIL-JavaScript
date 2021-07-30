# _CHAPTER 1-4_

###  :pencil: ​_문제 035 :  Factory 함수 사용하기_

2제곱, 3제곱, 4제곱을 할 수 있는 Factory 함수를 만들려고 합니다.

<br>

:desktop_computer: ***<pass> 에 코드를 작성하여 two함수를 완성하시오***

```javascript
function one(n){
    function two(){
        // pass
    }
    return two;
}
const a = one(2);
const b = one(3);
const c = one(4);

console.log(a(10));
console.log(b(10));
console.log(c(10));
```

<br>

:ballot_box_with_check: **풀이 코드  : 소스**

```javascript
function one(n){
    function two(x){
        // pass
        // 제곱의 결과를 반영해주는 메소드 : Math.pow()
        return Math.pow(x, n);
        
    }
    return two;
}
const a = one(2);
const b = one(3);
const c = one(4);

console.log(a(10));			// 100
console.log(b(10));			// 1000
console.log(c(10));			// 10000
```



- 매개변수를 통해서 다른 기능을 하는 factory함수
