#  CHAPTER 0

###  :pencil: ***자바스크립트 기초***

<br>

자바스크립트는 *브렌던 아이크*가 만든 프로그래밍 언어로, **대화형 웹 페이지**를 만들 수 있으며 **웹 어플리케이션**을 만들기 위한 필수적인 언어이다.

`HTML` 페이지에 `Javascript`를 삽입하는 방시은 두 가지이다. 

- `script`태그를 사용하고 그 안에 자바스크립트 코드를 직접 삽입
- 외부 파일을 참조하여 삽입하는 방법

##### _EX) script 태그로 코드를 감싸는 예_

```html
script type="text/javascript"> [YOUR_SCRIPT_HERE] </script>
```

<br>

##### _EX) 외부 파일을 참조 예_

```html
script src="/home/sciprt.js"></script>
```

원하는 만큼 스크립트를 추가할 수 있으며, `절대 경로`, `상대 경로`, `전체 경로` 모두 사용할 수 있다.

```html
<!-- 프로젝트 루트로부터의 절대 경로 -->
<script src="/home/script.js"></script>

<!-- 현재 폴더에 대한 상대 경로 -->
<script src="script.js"></script>

<!-- jquery 라이브러리의 전체 URL -->
<script src"http://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/core.js"></script> 
```

`script` 태그 안에 코드를 작성하기보다는 파일을 넣어서 브라우저가 가져오는 파일 수에 관계 없이 한 번에 다운로드하고 캐시하게 하는 것이 좋다. 

이 방식에서는 **캐시된 버전의 파일을 사용할 수 있으므로 성능상으이 이점이 있다.**

