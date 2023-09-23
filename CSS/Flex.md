# 0. `flex`란?

flex는 행과 열 형태로 배치하는 일차원 레이아웃 배치 속성이다.

기존에 사용하던 float이나 inline-block을 활용해서 레이아웃을 만드는 것보다 편리한 기능들을 제공한다.

flex 레이아웃은 **flex container**라고 불리는 부모요소와 **flex item**이라 불리는 복수의 자식요소로 구성된다.

```
<div class="container">
    <div class="item">item1</div>
    <div class="item">item2</div>
</div>
```

![](https://velog.velcdn.com/images/kjwboa/post/815415e9-e4e2-41d4-ac45-16781a1d95c3/image.png)

flex의 속성들은 아래의 2가지로 나뉜다.

- **flex 컨테이너(부모요소)에 적용하는 속성**
- **flex 아이템(자식요소)에 적용하는 속성**

# 1. 컨테이너에 적용하는 속성들

## 1.1 `display: flex;`

> display:  flex  |  inline-flex

flex를 사용하기 위해서 flex container에 항상 써줘야 하는 속성이다.

- flex : 컨테이너에 display: flex를 써주기만 해도 세로로 배치되던 컨테이너 안의 아이템들이 가로로 배치된다.
- inline-flex : 아이템의 배치보다는 컨테이너가 주변 요소들과 어떻게 배치될지를 결정한다. inline-block 처럼 동작함.

아래 이미지는 container1에 `display: flex`를 적용했다.

![](https://velog.velcdn.com/images/kjwboa/post/a9d222c2-7133-4fad-9fb4-a31c0b073311/image.png)

![](https://velog.velcdn.com/images/kjwboa/post/0817982b-f6a2-47de-bb02-405a9244f6dc/image.png)

flex 아이템들은 가로 방향으로 배치된다. 자신의 콘텐츠 만큼만 width를 갖게 되고 height는 컨테이너의 높이 만큼 알아서 늘어난다. (align-items: strech가 기본 값이기 때문)

아래는 container1에 `display: inline-flex`를 적용했다.

![](https://velog.velcdn.com/images/kjwboa/post/d5be30bb-3010-4b75-b867-ac2f45999e98/image.png)

`display: flex`; 처럼 컨테이너 안의 아이템들이 정렬되긴 하나, 컨테이너와 다른 요소의 배치도 정렬된다.

## 1.2 `flex-direction` 배치 방향 설정

> flex-direction:  row (default)  |  column  |  row-reverse  |  column-reverse

아이템이 배치되는 방향을 설정하는 속성이다.

- row _(default)_ : 아이템이 가로(행) 배치된다.
- column : 아이템이 세로(열) 배치된다.
- row-reverse : 아이템이 역순으로 가로 배치된다.
- column-reverse : 아이템이 역순으로 세로 배치된다.

![](https://velog.velcdn.com/images/kjwboa/post/00b40170-96c9-4f69-9995-c1ad23e32b91/image.png)

## 1.3 `flex-wrap` 줄넘김 처리 설정

> flex-wrap:  nowrap (default)  |  wrap  |  wrap-reverse

컨테이너가 아이템을 더 이상 한 줄에 담을 공간이 없을 때 아이템 줄바꿈을 어떻게 할지 결정한다.

- nowrap _(default)_ : 줄바꿈을 하지 않는다.
- wrap : 줄바꿈을 한다.
- wrap-reverse : 줄바꿈을 하되 역순으로 한다.

![](https://velog.velcdn.com/images/kjwboa/post/1b743431-3d1a-4967-a0db-42fc463b64d5/image.png)

## 1.4 `flex-flow` (flex-direction flex-wrap 단축속성)

> flex-flow:  row wrap  |  column wrap-reverse ~

`flex-direction`과 `flex-wrap`을 한 번에 지정할 수 있는 단축 속성이다.

`flex-direction`, `flex-wrap` 순서대로 써주면 된다.

## 1.5 `justify-content` 메인축 방향 정렬

> justify-content:  flex-start (default)  |  flex-end  |  center  |  space-between  |  space-around  |  space-evenly

메인축 방향으로 아이템들을 정렬하는 속성이다.

- flex-start _(default)_ : 아이템들을 메인축 시작점으로 정렬한다.
- flex-end : 아이템들을 메인축 끝점으로 정렬한다.
- center : 아이템들을 메인축 가운데로 정렬한다.
- space-between : 각 아이템들의 **사이**에 균일한 간격을 만들어준다.
- space-around : 각 아이템들의 **둘레**에 균일한 간격을 만들어준다.
- space-evenly : 각 아이템들의 **사이와 양 끝**에 균일한 간격을 만들어준다.

![](https://velog.velcdn.com/images/kjwboa/post/beef3e8e-dded-400c-ac85-3b664b0bae3e/image.png)

![](https://velog.velcdn.com/images/kjwboa/post/3ef63fb9-0ea9-48da-8e86-8d025e1cdba6/image.png)

## 1.6 `align-items` 수직축 방향 정렬

> align-items:  strech (default)  |  flex-start  |  flex-end  |  center  |  baseline

수직축 방향으로 아이템들을 정렬하는 속성이다.

- strech _(default)_ : 아이템들이 수직축 방향으로 컨테이너의 높이만큼 쭈욱 늘어난다.
- flex-start : 아이템들을 수직축 시작점으로 정렬한다.
- flex-end : 아이템들을 수직축 끝점으로 정렬한다.
- center : 아이템들을 수직축 가운데로 정렬한다.
- baseline : 아이템들을 텍스트 베이스라인 기준으로 정렬한다.

![](https://velog.velcdn.com/images/kjwboa/post/0e726a05-d547-49a9-bd9a-bac001ea748d/image.png)

## 1.7 `align-content` 여러 행 아이템 묶음 정렬

> align-content: strech (default) | flex-start | flex-end | center | space-between | space-around | space-evenly

`flex-wrap: wrap`을 설정한 경우 아이템들의 행이 2줄 이상이 되었을 때의 수직축 방향 정렬을 결정하는 속성이다.

`justify-content`와 비슷하게 작동하나 수직축 방향의 정렬이라고 보면 된다.

![](https://velog.velcdn.com/images/kjwboa/post/0d1cbbcb-3ccd-4d70-9462-8dfb799952e4/image.png)

## 1.8 `gap` 아이템 간격

> gap: 10px (숫자값)

`gap`은 아이템 간의 간격을 설정 할 수 있다.

`column-gap` 열간 간격을, `row-gap`은 행간 간격을 따로 설정 할 수 있고 `gap`으로 한 번에 행열 간격을 써줄 수 도 있다.

```css
.container {
  /* gap: 40px 10px; */
  column-gap: 10px;
  row-gap: 40px;
}
```

![](https://velog.velcdn.com/images/kjwboa/post/a65ca045-3c24-4678-8266-8a23bc883c7b/image.png)

# 2. 아이템에 적용하는 속성들

## 2.1 `flex-basis` 아이템의 기본 크기

> flex-basis: auto (default) | 1 (숫자 값)

`flex-basis`는 중심축을 기준으로 flex 아이템의 기본 크기를 설정한다.

( `flex-direction: row;` 일 때는 너비, `flex-direction: column` 일 때는 높이 )

예를 들어 `flex-direction: row` 일 때 `flex-basis: 100px`은 아이템의 width가 100px이 되고

`flex-direction: column` 일 때 `flex-basis: 100px`은 아아템의 height가 100px이 된다.

grow나 shrink를 사용해서 아이템이 늘어나거나 줄어들 때의 기준이 된다.

> 💡 **주의할 점**  
> 어디까지나 '기본 크기'를 설정하는 값이다.  
> 아래 이미지는 각 item에 flex-basis: 100px;을 주었는데 원래 너비가 100px이 넘지 않았던 item1, item2는 100px이 되었지만 원래 너비가 100px이 넘던 item3은 그대로 유지된다.

![](https://velog.velcdn.com/images/kjwboa/post/58c9ca1a-3321-4f3a-b597-53ff1a5264c1/image.png)

## 2.2 `flex-grow` 늘어나는 비율

> flex-grow: 1 (숫자 값)

`flex-grow`는 아이템이 `flex-basis`의 값보다 커질 수 있는지를 결정한다.

속성 값으로 숫자가 들어가는데, 몇이든 0보다 큰 값이 세팅되면 해당 아이템은 유연하게 늘어나는 박스로 변하고 원래의 크기보다 커지며 빈 공간을 채우게 된다.

기본값이 0이기 때문에 따로 적용하기 전까지는 아이템이 늘어나지 않는다.

![](https://velog.velcdn.com/images/kjwboa/post/a6d36d26-b353-4516-b0fd-35c285e627fa/image.png)

> 💡 **주의할점**  
> flex-grow에 들어가는 숫자는 아이템 자체 너비의 비율이 아니라,  
> flex-basis(아이템 너비)를 제외한 **여백 부분의 비율**이다.

![](https://velog.velcdn.com/images/kjwboa/post/67f4cee6-0da4-42b3-bf4f-aa5d5503f31b/image.png)

아이템 자체 너비의 비율을 설정하고 싶다면 단축 속성인 `flex`를 사용하는 것이 좋다.

## 2.3 `flex-shrink` 줄어드는 비율

`flex-grow`와 쌍을 이루는 속성으로 아이템이 `flex-basis` 값보다 작아질 수 있는지를 결정한다.

grow와 마찬가지로 속성 값으로 숫자가 들어가는데, 몇이든 0보다 큰 값이 세팅되면 해당 아이템은 유연한 박스로 변하고 `flex-basis` 보다 작아진다.

기본값이 1이기 때문에 따로 세팅하지 않아도 아이템이 `flex-basis`보다 작아질 수 있었다.

`flex-shrink`를 0으로 세팅하면 아이템의 크기가 `flex-basis`보다 작아지지 않기 때문에 고정된 너비의 아이템을 만들 수 있다.

## 2.4 `flex` (flex-grow flex-shrink flex-basis 단축속성)

`flex-grow`, `flex-shrink`, `flex-basis`를 한 번에 쓸 수 있는 단축 속성이다.

이 세가지 속성들은 관련이 깊기 때문에 단축 속성인 `flex`를 쓰는 편이 편하다.

## 2.5 `align-self` 수직축으로 아이템 단독 정렬

> align-self: auto | strecth | flex-start | flex-end | center | baseline

align-items가 전체 아이템들을 정렬했다면, align-self는 여러 아이템 중 하나의 아이템만 골라서 수직축으로 정렬할 수 있다.

컨테이너에 `align-items: flex-start`; 가 적용되있고 세 번째 위치한 아이템만 따로 `align-self: flex-end;`로 세팅하면 아래와 같은 이미지처럼 배치된 모습을 볼 수 있다.

![](https://velog.velcdn.com/images/kjwboa/post/1931a66c-3f5e-49a7-b917-8a459e1f4508/image.png)

## 2.6 `order` 아이템 배치 순서

> order: 0 (default) | 1 (숫자값)

각 아이템들의 시각적 나열 순서를 결정하는 속성이다.

속성값으로 숫자가 들어가며 작은 숫자일 수록 먼저 배치된다. 기본값으로 0을 가지고 있기 때문에 -1을 써주면 다른 아이템들보다 먼저 배치 될 수 있고, 1을 써주면 다른 아이템들보다 뒤에 배치될 수 있다.

> 💡**주의할 점**  
> 어디까지나 "시각적"으로 보여지는 순서가 변경 될 뿐이므로 HTML 자체의 구조가 바뀌는게 아니라서 접근성 측면에서 사용에 주의해야한다. 스크린 리더로 화면을 읽을 때, order로 바꾼 순서는 소용이 없다.
