#  CHAPTER 05

###  :pencil: ***문자열 메서드***

<br>

### :page_facing_up: 5.1. 기본적인 문자열 메서드

---

자바스크립트에는 문자열에 사용할 수 있는 많은 메서드가 있다. 

<br>

#### 1) indexOf()

문자열에서 지정된 값이 처음 나타나는 위치를 반환한다. 

```javascript
const str = "this is a short sentence";
str.indexOf("short");		// 10
```

<br>

#### 2) slice()

문자열의 지정된 부분을 새 문자열로 반환한다. 

```javascript
const str ="pizza, orange, cereals";
str.slice(0,5);	// pizza
```

<br>

#### 3) toUpperCase()

문자열 내의 모든 문자를 대문자로 바꾼다.

```javascript
const str = "i ate an apple";
str.toUpperCase();	// 'I ATE AN APPLE'
```

<br>

#### 4) toLowerCase()

문자열의 모든 문자를 소문자로 바꾼다.

```javascript
const str = "I ATE AN APPLE";
str.toLowerCase();	// 'i ate an apple'
```

<br>

이것들 이외에도 많은 메서드들이 있다. 메서드 등에 대한 자세한 설명은 **MDN** 문서에서 확인할 수 있다.

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String

<br>





