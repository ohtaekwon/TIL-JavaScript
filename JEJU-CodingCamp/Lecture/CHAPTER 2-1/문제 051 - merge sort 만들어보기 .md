# _CHAPTER 1-5_

###  :pencil: ***문제 51 :  merge sort를 만들어보기***

벙합정렬(merge sort)은 대표적인 정렬 알고리즘 중 하나로 다음과 같이 동작한다.

> 1. 리스트의 길이가 0 또는 1이면 이미 정렬된 것으로 본다. 그렇지 않은 경우에는
>
>    
>
> 2.  정렬되지 않은 리스트를 절반으로 잘라 비슷한 크기의 두 부분 리스트로 나눈다 
>
>    
>
> 3.  각 부분 리스트를 재귀적으로 합병 정렬을 이용해 정렬한다.
>
>    
>
> 4.  두 부분 리스트를 다시 하나의 정렬된 리스트로 합병한다.

<br>

다음 코드의 빈칸을 채워 벙협정렬을 완성해 보자

```javascript
function megeSrot(arr){
    if(arr.length<=1){
        return arr;
    }
    const mid = Math.floor
}

```





<br>

:scroll: **풀이 방법**

- 방식 1 : 입력값을 하나하나 돌면서 검사하고 대문자를 소문자로, 소문자를 대문자로 만든다.
  - 
- 방식 2 :  string의 메서드
  - `toUpperCase()`
  - `toLowerCase()`

<br>

:ballot_box_with_check: **풀이 코드  : 소스**