#  CHAPTER 18

###  :pencil: ***ES2017 : 문자열 패딩, Object.entries(), Object.values()***

`ES2017`에서는 많은 기능들이 추가 되었다.

<br>

### :page_facing_up: 18.1. 문자열 패딩

---

문자열 끝 부분 또는 시작 부분에 **패딩(padding)** 을 추가할 수 있다. 각각 `padEnd()`와 `padStart()` 를 쓴다.

```javascript
"hello".padStart(6);	// ' hello'

"hello".padEnd(6);	// 'hello '
```

여기서 패딩으로 `6`을 지정했는데 두 경우 모두 `1`개의 공간만 확보된 이유는 무엇인가?

- `"hello"`는 5글자이고 패딩은 `6` 으로 지정되었기 때문에 빈 공간이 `1`개만 남는다.
- `"hello".padStart(6);` 에서는 시작부분에 빈 공간 1개 채워 넣게 된다.
- `"hello".padEnd(6);` 에서는 마지막 부분에 빈 공간 1개 채워 넣게 된다.

<br>

```javascript
// 10 - 2 = 8 스페이스
"hi".padStart(10);			// '        hi'

// 10 - 6 = 4스페이스
"welcome".padStart(10);		// '   welcome'
```

<br>
