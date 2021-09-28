#  CHAPTER 16

###  :pencil: ***세트, 위크셋, 맵, 위크맵***

<br>

<br>

### :page_facing_up: 16.1. 세트

---

**세트(집합, set)**란 어떠한 자료형의 값이든 각 원소를 **고유하게** 저장하는 객체이다.

```javascript
// 1.세트 생성
const family = new Set();

// 2.세트에 값 추가
family.add("Dad");
console.log(family);		// Set(1) {'Dad'}

// 2-1.
family.add("Mom");			
console.log(family);		// Set(2) {'Dad', 'Mom'}

// 2-2.
family.add("Son");
console.log(family);		// Set(3) {'Dad', 'Mom', 'Son'}

// 2-3. Dad 다시 추가
family.add("Dad");
console.log(family)			// Set(3) {'Dad', 'Mom', 'Son'}

family.keys();				// SetIterator {'Dad', 'Mom', 'Son'}
```

`2-3. `에서 마지막 부분에서 `"Dad"`를 다시 추가하려고 헀지만, `Set`은 고유한 값만 가질 수 있기 때문에 동일하게 유지됨을 볼 수 있다.

또한 `Set`에는 키가 없기 때문에 `.keys()`를 호출하면 `.values()`또는 `.entries()`를 호출하는 것과 동일한 결과를 얻는다.

<br>

##### `Set`에 관한 메서드

```javascript
family.size;		// 3
family.keys();		// SetIterator {'Dad', 'Mom', 'Son'}
family.entries();	// SetIterator {'Dad' => 'Dad', 'Mom' => 'Mom', 'Son' => 'Son'}
family.values();	// SetIterator {'Dad', 'Mom', 'Son'}
family.delete("Dad");
family;				// Set(2) {'Mom', 'Son'}
family.clear;
family;				// Set(0) {size: 0}
```

`Set`에는 **size** 속성이 있으면 **delete** 를 사용해서 하나의 원소를 삭제하거나 **clear**를 사용하여 모든 원소를 삭제할 수 있다.

또한 `Set`에는 키가 없기 때문에 `.keys()`를 호출하면 `.values()` 또는 `.entries()`를 호출하는 것과 동일한 결과를 얻는다.

<br>
