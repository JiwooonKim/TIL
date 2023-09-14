HTML을 작성할 때 `<header>` 안에는 항상 `<meta>` 가 들어간다.
일상적으로 사용하다 보니 이 태그가 왜 들어가는지, 어떤 역할을 하는지에 대해 정확히 알지못하고 지나가게 되는 경우가 많은 것 같다.

```
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>---</title>
    <link rel="stylesheet" href="./assets/css/style.css">
    <script src="./assets/js/main.js"></script>
</head>
```

---

# 📌 `<meta>` 태그란?

---

해당 문서에 대한 정보, 메타데이터를 정의할 때 사용되며
웹 서버와 웹 브라우저간에 상호 교환되는 정보를 정의하는데 사용한다.

이 메타데이터는 브라우저나 검색 엔진, 다른 웹서비스에서 사용하게 된다.

> ## 💡meta 와 metadata의 차이

- 메타데이터 (MetaData)
  웹페이지에 대한 정보(사이트에 대한 설명, 키워드 등)를 위해 만들어진 데이터
  검색엔젠 등에 제공하기 위해 데이터를
  해당 정보가 누락되면 검색엔진 입장에서 해당 페이지가 어떤 정보를 담고 있는지 알 수 없게 된다.

---

- 메타 태그
  HTML 문서 내에 메타데이터를 제공하는 역할

---

# 📌 `<meta>` 태그의 속성

---

## `charset`

: 해당 문서의 문자 인코딩 방식을 명시한다.

> ### 속성값

- 문자셋

```
<meta charset="utf-8">
```

## `http-equiv`

: HTTP 헤더에 정보 또는 값을 제공하는 content 속성.

> ### 속성값

- `X-UA-Compatible` : 페이지를 렌더링 할 Internet Explorer 버전을 선택할 수있는 문서 모드 메타 태그.

```
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```

- `cotent-type` : 해당 문서의 문자 인코딩 방식을 명시함.

```
<meta http-equiv="content-type" content="text/html; charset=UTF-8">
```

- `default-type` : 우선적으로 적용할 스타일시트를 명시함.

```
<meta http-equiv="default-style" content="preferred stylesheet">
```

- `refresh` : 해당 문서를 새로고침 할 시간 간격을 명시함.

```
 <meta http-equiv="refresh" content="30">
```

## `name`

: 메타데이터를 위한 이름을 지정한다.
지정하지 않으면 http-equiv 와 같은 기능을 한다.

> ### 속성값

- `author` : 해당 문서의 저자를 명시함.

```
<meta http-equiv="content-type" content="text/html; charset=UTF-8">
```

- `description` : 웹 페이지에 대한 설명을 명시함. 검색엔진이 검색 결과에 이 설명을 함께 표시.

```
<meta http-equiv="default-style" content="preferred stylesheet">
```

- `generator` : 해당 문서를 생성하는데 사용되는 소프트웨어 패키지 중 하나를 명시함. (수동으로 생성된 페이지에는 사용하지 않음)

```
<meta name="generator" content="Frontweaver 8.2">
```

- `keywords` : 검색엔진을 위해 웹페이지와 관련된 키워드 목록을 명시함. 콤마(,)로 구분.

```
<meta name="keyword" content="HTML, meta, tag, element">
```

- `viewport` : 사용자가 볼 수 있는 영역인 뷰포트를 제어함. 브라우저에게 해당 페이지의 면적과 비율을 어떻게 제어할지에 대한 지침을 제공.

```
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
```

## `content`

: meta 정보의 내용을 지정한다.
(`name` 속성이나 `http-equiv` 속성과 관련된 값(value)을 명시)

> ### 속성값

- 메타데이터의 값

```
<meta name="keyword" content="HTML, meta, tag, element, reference">
<meta name="description" content="HTML meta tag page">
<meta name="author" content="TCPSchool">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

---

# 📌 자주 사용되는 코드

---

## (1) 브라우저 호환성 지정하기

```
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```

- `http-equiv="X-UA-Compatible"`
  : 마이크로 소프트에서 만든 익스플로러 브라우저는 호환성 보기 모드가 존재하는데 사용자가 지원하는 브라우저에 따라 오래된 브라우저에서 정상적으로 출력되지 않는 이슈가 발생할 수 있기 때문에 브라우저 호환성을 지정한다.

* `content="IE=edge"`
  : IE 최신버전으로 렌더링한다.

```
<meta http-equiv="X-UA-Compatible" content="IE=9; IE=8; IE=7">
```

위 처럼 세미콜론으로 여러 브라우저를 한 번에 쓸 수도 있다.

```
<meta http-equiv="X-UA-Compatible" content="IE=Edge; chrome=1">
```

- `content="IE=Edge; chrome=1"`
  : 크롬프레임을 사용한다는 의미로, 크롬과 ie 모두 설치된 pc에서는 크롬의 렌더링 엔진을 사용해 화면에 출력되지만 아닌 경우는 ie로 출력한다.

```
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

- `width=device-width`
  : 기기에 따라 달라지는 디바이스의 화면 너비에 맞게 웹 페이지의 너비를 설정한다.

* `initial-scale=1.0`
  브라우저에 의헤 웹페이지가 처음으로 로드될 때 초기 확대/축소 레벨을 설정한다.

## (2) 확대를 2배까지만 제한하고 싶을 때

```
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=2.0">
```

- `content="maximum-scale"`
  : **최대 화면 배율 설정**
  사용자가 극단적으로 화면 확대하는 것을 방지한다.

* `content="minimum-scale"`
  : **최소 화면 배율 설정**
  사용자가 극단적으로 화면 축소하는 것을 방지한다.

## (3) 모바일에서 확대 축소를 막으려면?

`content` 속성값에 `user-scalable="no"` 추가
