# UI 표현하기

- 첫 React 컴포넌트를 작성하는 방법
- 다중 컴포넌트 파일을 만드는 경우와 방법
- JSX로 JavaScript에 마크업을 추가하는 방법
- 컴포넌트에서 JavaScript 기능을 이용하기 위해 JSX에 중괄호를 사용하는 방법
- Props를 사용하여 컴포넌트를 구성하는 방법
- 조건부 렌더링을 하는 방법
- 여러 개의 컴포넌트를 한 번에 렌더링하는 방법
- 컴포넌트를 순수하게 유지하여 혼란스러운 버그를 피하는 방법

## 첫 번째 컴포넌트

리액트 컴포넌트란 UI를 구성하는 독립적인 단위이다.

재사용 가능한 UI 요소이며, 다른 컴포넌트와 결합하여 사용할 수 있다.

## 컴포넌트 import 및 export 하기

export할 때 `default` 또는 `named`로 export할 수 있다.

```jsx
// default
export default function App() {
  return <div className='App'>Hello World</div>;
}

// named
export function App() {
  return <div className='App'>Hello World</div>;
}
```

import할 때는 `default`는 중괄호 없이, `named`는 중괄호를 사용한다.

```jsx
// default
import App from './App';

// named
import { App } from './App';
```

## JSX로 HTML 마크업 작성하기

### JSX란?

> JavaScript + XML

JSX는 React 엘리먼트를 생성한다. 반환값에 마크업을 작성할 수 있다.

### JSX 태그를 하나로 감싸는 이유

반환된 값은 리액트에서 내부적으로 js 객체로 변환된다.

하나의 함수에서는 두 개의 객체를 반환할 수 없기 때문에 하나의 객체로 감싸야 한다. (Fragment 또는 다른 태그로 감싸기)

## 중괄호가 있는 JSX 안에서 자바스크립트 사용하기

`{{` 및 `}}` 는 특별한 문법이 아니다. JSX에서 중괄호를 사용하여 JavaScript 표현식을 넣을 수 있다.

```jsx
<ul style={
  {
    backgroundColor: 'black',
    color: 'pink'
  }
}>
```

함수도 넣어줄 수 있다.

```jsx
function getStyle() {
  return {
    backgroundColor: 'black',
    color: 'pink'
  }
}

<ul style={getStyle()}>
```

## 리스트 렌더링

map() 호출 내부의 JSX 엘리먼트에는 항상 key 필요.

`key`는 각 컴포넌트가 어떤 배열 항목에 해당하는지 React에게 알려주어 나중에 일치하는 항목을 찾을 수 있도록 해준다.
key를 잘 선택하면 정확히 무슨 일이 일어났는지 추론하고 DOM 트리에 올바르게 업데이트 하는데 도움이 된다.

### 인덱스를 key로?

item 추가, 삭제되거나 배열 순서가 바뀌면 시간이 지남에 따라 렌더링하는 순서가 변경되어 미묘한 버그가 발생할 수 있다.

즉석에서 key를 생성하지 말고, 항상 고유한 값을 key로 사용해야 한다.

## 컴포넌트 순수하게 유지하기

*`순수`*하다는건 무엇일까?

> 순수 함수란
>
> 1. 동일한 인자에 대해 항상 동일한 값을 반환하는 함수
> 2. 함수 외부의 어떤 상태도 바꾸지 않는 함수

React에서는 모든 컴포넌트가 순수 함수일 거라고 가정한다.

### 순수함수로 구성하려는 이유

- 예측 가능성
  - 같은 입력 -> 같은 JSX 반환
- 테스트 용이성
  - 예측 가능 -> 테스트 용이
- 성능 최적화
  - props가 변경되지 않으면 렌더링을 건너뛸 수 있음 -> 성능 향상
- 유지보수성
  - 코드의 의도를 파악하기 쉬움 -> 유지보수성 향상

즉, 순수 함수로 구성하면 상태 변화를 추적하기 쉽고 코드의 복잡성을 줄일 수 있다.

### 하지만 이벤트들은 순수하지 않다.

하지만 언젠가는 무언가를 바꿔야하는 경우가 필요하다. 부작용(사이드 이펙트)이 나쁜게 아닌 꼭 필요하다.

함수형 프로그래밍에서는 부작용을 최소화하고 순수 함수를 사용하여 부작용을 발생시키는 코드를 분리한다.

![](https://velog.velcdn.com/images/teo/post/93d8b50f-2c13-4d7f-9123-1bddd07e8658/image.png)

### StrictMode

렌더링 중에 React에 의도하지 않은 부작용이 발생하는 것을 방지하기 위해 사용한다.
각 컴포넌트의 함수를 두 번 호출하여 순수하지 않은 연산을 찾아낸다. (개발 모드에서만 동작)
