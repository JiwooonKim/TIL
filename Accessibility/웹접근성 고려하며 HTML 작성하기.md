## 1. 문서의 기본 언어 설정

브라우저에게 문서가 어떤언어를 사용할 것인지 알려준다.
SEO에도 좋고 보조기술이 알맞은 음성 프로파일이나 문자 집합을 선택하는데 도움을 준다.

```html
<html lang="ko">
  ...
</html>
```

## 2. 올바른 대체텍스트 제공

### 2-1. 이미지 올바른 설명

이미지가 콘텐츠로 사용된다면 이미지 콘텐츠에 대한 정보를 제공하기 위해 alt 속성을 사용한다. 이 경우 스크린 리더가 "~의 사진, 그래프"라고 읽어주기 때문에 이러한 내용을 넣지 않는다.

```html
<!-- Bad -->
<img src="" alt="딸기 이미지" />

<!-- Good👍 -->
<img src="" alt="딸기" />
```

### 2-1. 의미가 없는 이미지

의미 없는 이미지는 빈 alt 속성을 사용해 대체텍스트를 제공하지 않는다.

```html
<!-- Bad -->
<img src="" alt="장식 이미지" />

<!-- Good👍 -->
<img src="" alt />
```

### 2-2. 주변 문맥에 설명이 있는 이미지

주변 문맥에 이미지에 대한 설명이 있는 경우 중복으로 제공하지 않는다.

## 3. 레이블 제공

사용자 입력에 대응하는 레이블을 제공해야한다.

```html
<!-- 시각적인 label이 있는 경우 -->
<input id="이름" />
<label for="이름">...</label>

<!-- 시각적인 label이 없는 경우 -->
<input aria-label="이름" />
```

## 4. 헤딩태그로 마크업 구조화

`<h1>`-`<h6>` 헤딩태그를 사용하여 아웃라인을 잡아줌으로써 사용자에게 페이지 구조에 대한 이해와 각 섹션 사이의 관계를 알려준다.
NVDA 스크린 리더를 사용하는 사용자는 단축키 H와 Shif+H 를 통해 헤딩태그에서 다른 헤딩태그로 바로 이동할 수 있다.

헤딩태그를 쌓을 때 단계를 뚸어넘거나 `<h1>` 태그를 여러번 사용하는 것은 피해야한다.

html outliner를 통해 확인할 수 있다.
[HTML 5 Outliner 바로가기 >](https://gsnedders.html5.org/outliner/)

## 5. 랜드마크 사용

랜드마크 : 스크린리더 사용자가 페이지 탐색을 용이하게 하기 위해 웹페이지를 큰 영역으로 나눈 것.
주요 이점 중 하나는 스크린리더 사용자가 섹션과 섹션 사이를 바로 이동하며 페이지를 탐색할 수 있다.

각 랜드마크에는 헤딩이나 레이블을 두는 것이 좋으며, 특히 같은 랜드마크가 페이지에 둘 이상 존재할 경우 서로를 구별할 수 있는 레이블이 반드시 필요하다.

- 헤딩이 있는 경우 : `aria-labelledby` 속성 활용
- 헤딩이 없는 경우 : `aria-label` 속성 활용

search와 같이 적절한 태그가 없는 섹션은 `role` 속성을 활용해 `role="search"`라고 작성한다.
기타 랜드마크

- role="contentinfo" : 사이트 하단 (footer)에 제공되는 저작권보호, 개인정보 등을 포함할 수 있음.
- role="search" : 검색과 관련된 서식, 링크 등을 포함.

## 6. WAI-ARIA 사용

생각보다 많은 곳에 WAI-ARIA가 활용된다.

### 6-1. 레이어 팝업을 가진 버튼에 상태정보 표시

레이어 팝업을 띄우는 버튼을 스크린리더 사용자가 알 수 있도록 `aria-haspopup` 속성으로 레이어 팝업이 뜰 것이라는 안내를 해준다.
메뉴를 열기 위한 버튼 혹은 메뉴 항목이 서브메뉴를 가진 경우 사용한다.

- `aria-haspopup="true"` : 팝업이 있는 버튼.
- dialog : 버튼, 컨트롤 등 상호작용 요소가 포함된 현재 문서의 하위창
- menu : 메뉴 팝업
- listbox : 클릭스 콤보박스에 option이 나타는 버튼
- tree : 하위 list를 포함하여 접고 펼칠 수 있음
- grid : 행과 열로 구성된 선택 가능 위젯

### 6-2. 확장상태 추가

확장, 축소되는 버튼에 포커스 했을 때 현재 확장 상태인지 아닌지 알 수 있도록 `aria-expaneded` 속성을 활용한다.

- `aria-expaneded="true"` : 확장상태
- `aria-expaneded="false"` : 축소상태

### 6-3. 탭메뉴

탭이란 한 주제에 대해 여러 개의 세부 섹션을 표현하는 방법 중 하나로
tab list, tab, tab 패널로 나뉜다.
(1) 각 tab role 부여

- Tab list : Tab, Tab panel을 하나의 그룹으로 묶어 tab list라고 표현한다. `role="tablist"`
- Tab : Tab list의 하위 영역으로 각각의 tab 요소를 칭한다. `role="tab"`
- Tab panel : 각각의 tab 하위 콘텐으를 칭한다. `role="tabpanel"`

(2) 탭에 연관된 탭패널을 참조하는 속성 부여.
탭의 `id` 와 탭패널의 `aria-labelledby` 속성 연결, 탭의 `aria-controls` 와 탭패널의 `id` 속성 연결

```html
<ul role="tablist">
  <li id="tab1" role="tab" aria-controls="tab-panel1">메뉴1</li>
  <li id="tab2" role="tab" aria-controls="tab-panel2">메뉴2</li>
  <li id="tab3" role="tab" aria-controls="tab-panel3">메뉴3</li>
</ul>
<div id="tab-panel1" role="tabpanel" aria-labelledby="tab1"></div>
<div id="tab-panel2" role="tabpanel" aria-labelledby="tab2"></div>
<div id="tab-panel3" role="tabpanel" aria-labelledby="tab3"></div>
```
