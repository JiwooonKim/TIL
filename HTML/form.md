# `<form>`

사용자로부터 입력 받을 수 있는 HTML 입력폼을 정의할 때 사용한다.

## `<form>`의 속성

- ### `action`

  폼 데이터를 서버로 보낼 때, 해당 데이터가 도착할 URL을 명시한다.

  > **URL**

  ```
   <form action="https://www.naver.com/">
  ```

- ### `method`

폼 데이터가 서버로 전송될 때 사용되는 HTTP 메서드를 명시한다.

> **get** | **post**

- GET 방식은 URL에 폼 데이터를 추가하여 서버로 전달하는 방식. (기본 값)
  쿼리 문자열에 포함되어 전송되므로 길이의 제한이 있고 보안상 취약점이 존재한다.
  >
- POST 방식은 폼 데이터를 별도로 첨부하여 서버로 전달하는 방식.
  이 방식의 HTTP 요청은 브라우저 히스토리에 남지 않고 데이터의 길이에 제한이 없으며 GET 방식보다 보안성이 높다.

- ### `target`
  폼 데이터를 서버로 제출한 후 받는 응답이 열릴 위치를 명시한다.
  > **\_self** | **\_blank** | **\_parent** | **\_top **
  - \_self : 기본 값, 서버로부터 받은 응답을 링크가 위치한 현재 프레임에서 보여준다.
  - \_blank : 새로운 윈도우나 탭에서 보여준다.
  - \_parent : 현재 프레임의 부모 프레임에서 보여준다.
  - \_top : 현재 윈도우 전체에서 보여준다.
- ### `name` | text

  해당 폼의 이름을 명시한다.

- ### `accept-charset` | 문자셋
  폼 데이터를 서버에 보낼 때 사용되는 문자 인코딩 방식을 명시한다.
  기본값은 UNKNOWN으로 설정되며, 이 값은 form 요소가 포함되어 있는 HTML 문서의 문자 인코딩과 같음을 나타낸다.
  > 문자 인코딩 : 사용자가 입력한 문자나 기호들을 컴퓨터가 이용할 수 있는 신호로 만드는 것.
- ### `enctype`
  폼 데이터가 서버로 제출될 때 해당 데이터가 인코딩되는 방법을 명시한다.
  > **application/x-www-form-urlencoded** | **multipart/form-data** | **text/plain**
- application/x-www-form-urlencoded : 기본값, 모든 문자들은 서버로 보내기 전에 인코딩 된다.
- multipart/form-data : 모든 문자를 인코딩하지 않는다.
- text/plain : 공백문자는 "+" 기호로 변환하지만 나머지 문자는 모두 인코딩 되지않는다.

---

# `<form>`의 자식으로 올 수 있는 태그들

## `<fieldset>`

`<form>`에서 관련된 요소를 그룹화할 때 사용한다.
관련 요소 주위에 박스 모양 선을 그려준다.

## `<legend>`

`<fieldset>`에 대한 설명 역할.
`<fieldset>`의 상자 테두리 가운데에 위치한다.

## `<input>`

사용자로부터 입력을 받을 수 있는 입력 필드를 정의할 때 사용한다.
type 속성에 따라 성질이 달라진다.

`<label>` 태그와 주로 같이 사용된다. 명시적 방식과 암시적 방식이 있는데
명시적 방식은 label의 for 과 input의 id를 연결시킨다.

암시적 방식은 label 태그 안에 input을 넣어 for 속성을 명시하지 않더라도 암묵적으로 이해할 수 있다.

오래된 기기일 경우 암시적 방식을 지원하지 않으므로 명시적 방식을 더 선호한다.

```
<!-- 명시적 방식 -->
<label for="age">나이</label>
<input type="number" id="age">

<!-- 암시적 방식 -->
<label>
	나이
	<input type="number" id="age">
</label>
```

radio나 checkbox의 경우 같은 그룹끼리 input의 name 속성을 같게 맞춰서 사용한다.

```
<label for="age-20">20대</label>
<input type="radio" name="age" id="age-20" value="20">

<label for="age-30">30대</label>
<input type="radio" name="age" id="age-30" value="30">

<label for="age-40">40대</label>
<input type="radio" name="age" id="age-40" value="40">
```

- ### `type=""`

  > " **text** | **password** | **email** | **tel** | **radio** | **checkbox** | **submit** | **button** | **number** | **file** | **color** | **search** | **url** | **date** "

- text : 한 줄의 텍스트 입력을 받는다.
- password : 비밀번호를 입력을 받는다. 입력 시, \*로 표기
- email : 이메일 입력을 위한 필드를 만든다.
- number : 숫자만 입력할 수 있는 필드를 만든다.
- radio : 단일 선택을 할 수 있는 라디오 버튼을 만든다.
- checkbox : 다중 선택이 가능한 체크박스를 만든다.
- submit : 제출 버튼을 만든다.
- button : 클릭 이벤트로 조작하는 버튼을 만든다.
- file : 파일 제출을 위한 필드를 만든다. 클릭하면 원하는 파일형식을 삽입하라는 메시지가 나타난다.
- color : 색상을 선택할 수 있는 필드를 만든다.
- search : 검색을 위한 필드를 만든다. `type="text"`와 같아보이지만 입력을 시작하면 취소 버튼이 나타나는 점이 다르다.

## `<label>`

사용자 인터페이스 (UI) 요소의 어떤 값을 넣어야하는지 이름을 붙이는 요소

## `<button>`

- ### `type=""`
  > " **submit** | **reset** | **button** "
- submit: 폼을 제출하는 이벤트를 발생 (기본값)
- reset : 폼 안에 작성된 내용을 초기화
- button : 자체로는 아무런 이벤트가 없으나 click 이벤트와 연결시켜 자바스크립트 이벤트 실행

> ### button vs input type="submit"
>
> 둘은 폼 전송 기능을 하므로 기능적으로는 동일하다.
> `<button>`은 닫는 태그가 있고 input은 닫는 태그가 없다.

- ### `form="id"`
  button 요소가 포함될 form 요소를 명시한다.
  form 요소의 id 값이어야한다.

```
<form action="" method="get" id="loginForm">
	<label for="login-id">아이디</label>
	<input type="text" id="login-id">
</form>
<button type="submit" form="loginForm">제출</button>
```
