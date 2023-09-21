# 1. BEM이란?

BEM은 CSS 제작 방법론으로 일종의 네이밍 컨벤션이다.
Block(블록), Element(요소), Modifier(수정자)의 약자로, 목적에 따라 네이밍 하는 것이 특징이다.

UI를 독립된 블록으로 분리함으로써 복잡한 페이지에서도 간단하고 신속하게 개발을 수행하는 것이 목적이다.

> ## 코딩 컨벤션이란?
>
> 코딩 습관을 통일해서 작업상의 가독성을 높여 일의 효율을 높이기 위한 내부적인 공동의 약속.

## 1-2. BEM의 특징

- 명시도를 균일하게 유지하기 위해 class 선택자만 사용한다.
- 목적에 따라 네이밍한다.
- HTML 요소들을 각각 `Block__Element--Modifer`세가지로 분류한다.

## 1-3. BEM의 장점

- 목적과 기능을 명확히 전달할 수 있다.
- 요소의 구조를 효율적으로 전달한다.
- CSS 명시도를 항상 낮은 수준으로 유지하기 때문에 구체성으로 인한 코드의 길어짐을 방지할 수 있다.

# 2. Block, Element, Modifier

## 2-1. Block

블럭은 기능적으로 독립적인 페이지 구성요소로, 재사용이 가능한 부분이다.

![](https://velog.velcdn.com/images/kjwboa/post/525d2a21-65cd-4f8c-b22e-e71a52e1a5ff/image.png)

예를 들어 이미지처럼 logo 블록, search 블록, menu 블록 등의 블록들은 여기저기 재사용될 수 있는 요소들이다.

- Block은 서로 중첩될 수 있으며, 몇 겹으로 중첩되는 것도 허용된다.

- Block의 이름은 상태가 아닌 용도를 나타낸다.

```html
<!-- O 올바른 사용 : 용도(error)를 나타냄 -->
<div class="error">
  <div>
    <!-- X 잘못된 사용 : 상태(red)를 나타냄 -->
    <div class="red-box"><div></div></div>
  </div>
</div>
```

- Block은 외부의 환경에 의존적이지 않기 위해서 Block 자체에 외부 여백이나(`margin`) 위치(`position`)를 설정하지 않아야한다.

- 모든 Block이 Element를 가지는 것은 아니다.

## 2-2. Element

블록을 구성하는 단위. 블록은 독립적이지만 엘리먼트는 블록에 의존적이다.
자식이 속한 블럭 내에서만 사용될 수 있고 다른 곳에서는 사용이 불가능하다.

![](https://velog.velcdn.com/images/kjwboa/post/8aded662-58f5-4eb8-85fc-c6c8f0aa88ad/image.png)

이미지 처럼 탭메뉴 전체를 감싸는 부분이 블록이고, 탭메뉴 하나하나가 엘리먼트이다.

```html
<ul class="tab">
  <li class="tab__item">탭 01</li>
  <li class="tab__item">탭 02</li>
  <li class="tab__item">탭 03</li>
</ul>
```

`tab`은 block이고, `tab__item`은 element다.

- Element는 Block의 부품으로 Block과 별도로 사용할 수 없다.

- Element는 상태가 아닌 용도를 나타낸다.
  이것이 무엇인가? (O) : item, text, button...
  이것이 어떻게 생겼는가? (X) : red, big...

- Element는 서로 중첩될 수 있다. 다만, Element는 Block의 부분이지 다른 Element의 부분이 아니다.
  즉 Element는 항상 Block의 하위 요소이다.

```html
<form class="search-form">
	<div class="search-form__inner>
    	<!-- X 권장: search-from__input | search-from__content-input -->
    	<input class="serach-form__inner__input /">
        <!-- X 권장: search-form__button | search-from__content-button -->
        <button class="search-form__content__button"></button>
    </div>
</form>
```

## 2-3. Modifier

블럭이나 엘리먼트의 속성이다. Block이나 Element의 상태 또는 동작을 정의한다.

![](https://velog.velcdn.com/images/kjwboa/post/e860b481-37a8-4662-a861-555cf5927ba2/image.png)

```
<ul class="tab">
  <li class="tab__item tab__item--active">탭 01</li>
  <li class="tab__item">탭 02</li>
  <li class="tab__item">탭 03</li>
</ul>
```

`tab__item--active`의 `--active`가 modifier이다.

- Modifier는 모양(appearance), 상태(state), 동작(behavior)을 나타낸다.
  (1) 어떤 사이즈, 어떤 테마 : size_s / theme_blak
  (2) 어떤 상태 : disabled / focused / active
  (3) 어떤 동작 : dirctions_left-top

- Modifier는 Block, Element의 모양/상태/동작을 변경하는 것이기 때문에 Block, Element에 추가하여 사용한다. (block\_\_element—modifier)

### Modifier의 유형

Modifier는 Boolean과 Key-Value 2가지 유형이 있다.

#### (1) Boolean유형

Modifier의 유무가 중요하고 값이 무관할 때 사용. (disabled, focused)
Boolean Modifier가 있으면 해당 값이 참으로 간주된다.

- 명명법 : `block-name_modifier-name` | `block-name__element-name_modifier-name`

```
<!-- search-form Block은 Boolean Modifier를 갖고 있음. -->
<form class="search-form search-form_focused">
	<div class="search-form__inner>
        <button class="search-form__button"></button>
    </div>
</form>
```

#### (2) Key-Value

Modifier의 값이 중요한 경우 사용. (size_s, theme_black)

- 명명법 : `block-name--modifier-name_modifier-value` | `block-name__element-name_modifier-name_modifier-vlaue`

```html
<!-- search-form Block은 black 값을 가진 theme Modifier를 갖고 있음. -->
<form class="search-form search-form_theme_black">
	<div class="search-form__inner>
        <button class="search-form__button"></button>
    </div>
</form>
```

- 동일한 유형의 Modifier를 동시에 사용할 수 없다.

```html
<!-- X 동일한 유형, theme Modifier를 갖고 있음.-->
<form class="search-form search-form_theme_black search-form_theme_blue">
	<div class="search-form__inner>
        <button class="search-form__button"></button>
    </div>
</form>
```

> ## MindBEMding
>
> Modifier 전후 구분 문자를 언더바 한 개에서 하이픈 두개로 변경한 스타일으로, 이 방식도 많이 사용된다.

- `block-name--modifier-name`
- `block-name__element-name--modifier-name`
- `block-name--modifier-name--modifier-value`
- `block-name__element-name--modifier-name--modifier-value`

- 구현된 컴포넌트에 의존하지 않고 코드가 재사용된다. -> Block
- 부모 요소 (Block) 없이 개별적으로 사용할 수 없다. -> Element
- 더 작은 부분으로 나뉘어야하는 Element -> Block / Mix

## 2-4. Mix

Mix는 Block과 Element가 하나의 HTML 요소에 존재하는 것을 의미한다.
코드 중복을 피하면서 여러 BEM 엔티티의 동작과 스타일을 결합.

- 장점 : 가급적 명시도를 높이지 않고 Block의 독립성을 유지할 수 있다.

```
<header class="header">
	<div clas="search-form header__search-form">
</header>
```

위의 예시는 `header` 블록과 `search-from` 블록 사이의 스타일링은 `header`와 `header__search-form`에 정의하여
`search-form` 블록과 `header`블록 간의 결합도를 높이지 않는다.
