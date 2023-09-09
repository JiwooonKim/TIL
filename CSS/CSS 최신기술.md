# CSS 최신 기능

## 1. Cascade Layers `@layer`

> 지원 브라우저 (2023. 09. 09 기준)
>
> ![](https://velog.velcdn.com/images/kjwboa/post/1f129ef2-0a7e-413f-a12c-b7714f60350d/image.png)

사용자가 지정한 레이어의 순서에 따라 CSS의 우선순위가 정해진다.
(뒤에 배치할수록 우선순위 높음)

기존에 프레임워크 CSS와 커스텀 CSS를 함께 사용할 때
우선순위 때문에 내가 적용하고 싶은 스타일링이 적용되지 않는 문제가 발생할 수 있었다.
Cascade Layers를 사용하면 구체적인 셀렉터나 선언된 순서를 고려하지 않아도 손쉽게 우선순위를 설정할 수 있다.

```css
/* 레이어 순서 정하기 */
@layer reset, defaults, patterns, components, utilities, overrides;

/* 프레임워크 스타일을 한 레이이에 모아두기 */
@import url("framework.css") layer(components.framework);

/* 레이어별 스타일링 */
@layer utilities {
  [data-color="brand"] {
    color: var(--brand, rebeccapurple);
  }
}
@layer defaults {
  a:any-link {
    color: maroon;
  }
}
```

## 2. `@container`

> 지원 브라우저
>
> ![](https://velog.velcdn.com/images/kjwboa/post/37e94083-3c77-4be8-a476-acf52f22fb82/image.png)

`@container` 는 부모 요소의 너비에 반응하는 CSS를 작성할 수 있다.

`@media` 와 유사한 기능이지만 `@media`는 윈도우 사이즈가 변경되어야만 아이템을 재배치할 수 있는 문제를 갖고있기 때문에 `@container`를 사용하면 컴포넌트 단위의 재사용성을 높일 수 있다.

```css
/* 컨테이너 정의 */
.card_holder {
  container-type: inline-size;
  container-name: card-holder;
}
.card {
  display: flex;
  flex-direction: row;
}

/* 컨테이너 사용 */
@container card-holder (max-width: 200px) {
  .card {
    flex-direction: column;
  }
}
```

## 3. `@nest`

> 지원 브라우저 (2023. 09. 09 기준)
>
> ![](https://velog.velcdn.com/images/kjwboa/post/66e925ce-be87-4232-9c67-828a66cab8f7/image.png)

부모와 자식간의 관계를 더욱 명확하게 표현이 가능하다.
`@nest`의 사용이 가능하다면 nesting 기능을 위해 scss를 사용하는 일은 불필요해진다.

```css
article {
  color: darkgray;

  & > a {
    color: hotpink;
  }
}
```

## 4. `@scope`

> 지원 브라우저 (2023. 09. 09 기준)
>
> ![](https://velog.velcdn.com/images/kjwboa/post/41a2ea16-8850-4b8a-9319-63c671558f60/image.png)

서로 스타일이 다른 컴포넌트 / 모듈을 `@scope`로 감싸 충돌을 피할 수 있도록 한다.
`@scope` 사용이 가능하다면 특정 컴포넌트별로 CSS를 적용할 수 있으므로 별도로 CSS Module 전처리기의 사용이 불필요해진다.

```css
@scope (.media) {
  img {
    border: red;
  }

  p {
    font-size: 0.75rem;
  }

  .title {
    font-size: 2rem;
  }
}

@scope (.card) {
  img {
    border: none;
  }

  p {
    font-size: 0.8rem;
  }

  .title {
    font-size: 1.5rem;
  }
}
```

## 5. `accent-color`

> 지원 브라우저 (2023. 09. 09 기준)
>
> ![](https://velog.velcdn.com/images/kjwboa/post/571a58a0-3ea6-4a6e-a4ac-a061e8bec0f2/image.png)

동일한 웹사이트여도 브라우저별로 기본 스타일에 차이가 있는데,
`accent-color` 를 지정하면 페이지에서 사용하는 기본적인 요소들의 색상을 변경할 수 있다.

컴포넌트가 위치한 배경 색상에 따라서 그와 대비되는 색상을 자동으로 지정해주기 때문에 웹접근성에 위배되지 않는다.

```css
:root {
  accent-color: red;
}
```
