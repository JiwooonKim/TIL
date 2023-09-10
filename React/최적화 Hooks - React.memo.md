리액트에서는 쓸데없는 렌더링을 방지하기 위해서 성능 최적화 hook을 제공한다.
hook을 사용하여 의도하지 않은 렌더링을 최소화 시킬 수 있다.

# 리액트에서의 렌더링

React에서는 렌더링이 다양한 상황에서 발생한다.

- Props가 변경될 때
- State가 변경될 때
- forceUpdate() 를 실행했을 때
- 부모 컴포넌트가 렌더링 되었을 때

불필요하게 리렌더링이 될 경우 hook을 이용해 최적화 할 수 있다.
최적화에 사용되는 hook은 `React.memo`, `useCallback`, `useMemo`가 있는데 이 3가지 모두 Memoization 개념을 활용한다.

> ## Memoization
>
> 한 번 계산했던 것을 메모리에 저장했다가 결과가 같으면 연산하지 않고 결과를 가져다 쓰겠다는 것.

# `React.Memo`는...

컴포넌트의 결과 값을 기억한다.

공식문서에 따르면

- `React.Memo`는 고차 컴포넌트 (Higher Order Component) 이다.
- `React.Memo`는 props의 변화에만 영향을 준다.

> ## 고차 컴포넌트란?
>
> 컴포넌트를 인자로 받아 최적화된 새로운 컴포넌트를 반환하는 함수.
>
> 이렇게 최적화된 컴포넌트는 렌더링이 되어야할 상황에 Prop Check를 통해 자신이 받는 Props의 변화를 확인한다.
> 변화가 있다면 렌더링을 하고, 없다면 기존의 렌더링 결과를 재사용한다.

즉, `React.Memo`는 컴포넌트를 받아 자신의 props가 변경될 때만 리렌더링 되고 동일한 props로 동일한 결과를 렌더링하면 마지막으로 렌더링된 결과를 재사용한다.

## 예제

예시로 부모 컴포넌트와 자녀 컴포넌트가 있다.

부모 나이 증가 버튼을 누르면 부모 컴포넌트의 age가 증가하고
자녀 나이 증가 버튼을 누르면 자녀 컴포넌트의 age가 증가한다.

![](https://velog.velcdn.com/images/kjwboa/post/4123f134-1cd9-489b-9dcb-4aafb8785b5d/image.png)

여기서 부모 나이 증가 버튼을 누르면 부모 컴포넌트가 렌더링되며 불필요하게 자녀 컴포넌트도 렌더링된다.
![](https://velog.velcdn.com/images/kjwboa/post/7475803d-922b-499a-b08e-c9917b1cbf2e/image.gif)

이를 방지하기 위해서 `React.memo`로 자녀 컴포넌트를 인자로 받아주면 부모 컴포넌트가 렌더링 되어도 자녀 컴포넌트는 렌더링 되지 않는다.

```jsx
export default React.memo(Child);
```

![](https://velog.velcdn.com/images/kjwboa/post/07f3f225-c9cd-48cf-ae15-8e2b0f93a154/image.png)

물론 `React.memo`는 props의 변화에만 영향을 주기

# 얕은 비교

age를 지우고 자녀 컴포넌트가 name이라는 객체를 전달받는다고 가정해보자.
이렇게 되면 부모 나이 증가 버튼을 누르면 `React.memo`로 자녀 컴포넌트를 감싸줬음에도 자녀 컴포넌트가 리렌더링 된다.

![](https://velog.velcdn.com/images/kjwboa/post/889c3f7a-08b5-4e8c-bb9d-7151ce56024d/image.gif)

그 이유는, `React.memo`가 Props를 비교하는 방식 때문이다.
**`React.memo`는 얕은 비교 즉, 주소를 통해서 같은 값인지 판단한다.**

자녀 컴포넌트가 전달받은 name Props는 객체다.
변수에 값을 할당하면 값이 그대로 저장되는 원시타입과는 다르게 비원시타입인 객체는 메모리 주소가 저장된다.

App 컴포넌트가 다시 렌더링되는 것은 함수가 다시 호출되는 것이므로 함수 안의 모든 변수가 초기화 되기 때문에 렌더링 될 때마다 객체는 다른 메모리 주소가 저장 된다.
이렇게 메모리 주소가 바뀌는 것을 Props에 변화가 있다고 인식하여 자녀 컴포넌트도 리렌더링 되는 것이다.

```jsx
import React, { useState } from "react";
import "./App.css";
import Child from "./components/Child";
import OptimizeTest from "./components/OptimizeTest";
import Lifecycle from "./components/Lifecycle";

function App() {
  console.log("🧑‍🍼부모 컴포넌트가 렌더링 되었습니다.");

  const [parentAge, setParentAge] = useState(0);
  const [childAge, setChildAge] = useState(0);

  const addParentAge = () => {
    setParentAge(parentAge + 1);
  };
  return (
    <div className="App" style={{ border: "4px solid blue", margin: "20px" }}>
      <h1>🧑‍🍼부모</h1>
      <p>age: {parentAge}</p>
      <button onClick={addParentAge}>부모 나이 증가</button>
      <Child
        name={{
          lastName: "김",
          firstName: "선아",
        }}
      />
    </div>
  );
}
export default App;
```
