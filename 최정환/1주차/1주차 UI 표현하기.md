# 1주차 : UI 표현하기

# 첫 번째 컴포넌트

## 컴포넌트 : UI 구성요소

- React를 사용하면 마크업, CSS, JS를 앱의 재사용 가능한 UI요소인 사용자 정의 “컴포넌트”로 결합할 수 있다.
- 컴포넌트를 작성, 순서 지정 및 중첩하여 전체 페이지를 디자인할 수 있다.

```jsx
<PageLayout>
  <NavigationHeader>
    <SearchBar />
    <Link to="/docs">Docs</Link>
  </NavigationHeader>
  <Sidebar />
  <PageContent>
    <TableOfContents />
    <DocumentationText />
  </PageContent>
</PageLayout>
```

- 장점
    - 이미 완성한 컴포넌트의 재사용으로 개발 속도가 빨라진다.
    - 커뮤니티에서 공유되는 컴포넌트를 사용할 수도 있다.

## 컴포넌트 정의하기

<aside>
💡 React 컴포넌트 : 마크업으로 뿌릴 수 있는 JS 함수.

</aside>

- 이전에는 웹 페이지 제작시 웹 개발자가 컨텐츠를 마크업 한 후 JS를 뿌려 상호작용을 추가했다.
- React는 동일 기술을 사용하면서도 상호작용을 우선시 한다.

```jsx
export default function Profile() {
  return (
    <img
      src="https://i.imgur.com/MK3eW3Am.jpg"
      alt="Katherine Johnson"
    />
  )
}
```

## 컴포넌트를 빌드하는 방법

### 1단계 : 컴포넌트 내보내기

- export default 접두사는 표준 JS 구문이다.
    - 이 접두사를 사용하면 다른 파일에서 가져올 수 있도록 파일에 주요 기능을 포시할 수 있다.

### 2단계 : 함수 정의하기

```jsx
function Component () {

}
```

- 위 코드를 사용하면 Component라는 이름의 JS 함수를 정의할 수 있다.

<aside>
💡 React 컴포넌트는 일반 JS함수 이지만, 이름은 대문자로 시작해야 함.

</aside>

### 3단계 : 마크업 추가하기

```jsx
function Component () {
	return (
	  <div>
	    <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />
	  </div>
	);
}
```

- HTML처럼 작성되어 있지만 실제로는 JS이며, 위 구문을 JSX라 함.
    - JS 안에 마크업 삽입 가능.
- return과 같은 라인에 있다면 괄호 생략 가능하지만 아닌 경우 괄호로 묶어야 함.
    - 괄호가 없으면 return 뒷 라인에 있는 모든 코드가 무시됨.

## 컴포넌트 사용하기

- 컴포넌트 속에 컴포넌트 중첩이 가능하다.

```jsx
function Profile() {
  return (
    <img
      src="https://i.imgur.com/MK3eW3As.jpg"
      alt="Katherine Johnson"
    />
  );
}

export default function Gallery() {
  return (
    <section>
      <h1>Amazing scientists</h1>
      <Profile />
      <Profile />
      <Profile />
    </section>
  );
}
```

- 위 코드는 아래 코드와 같다.

```jsx
<section>
  <h1>Amazing scientists</h1>
  <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />
  <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />
  <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />
</section>
```

### 브라우저에 표시되는 내용

- 주의점
    - 소문자로 시작 → React가 HTML태그로 인식
    - 대문자 시작 → React가 컴포넌트를 사용한다고 이해

### 컴포넌트 중첩 및 구성

- 컴포넌트는 일반 JS함수이므로 같은 파일에 여러 컴포넌트를 포함할 수 있다.
    - 컴포넌트가 상대적으로 작거나 밀접하게 관련되어 있을 때 편리하다.
- 파일이 복잡해지면 언제든지 컴포넌트를 별도의 파일로 옮길 수 있다.
- 위 코드에서 Gallery 컴포넌트는 Profile을 자식으로 하는 부모 컴포넌트 이다.
- 주의점
    - 컴포넌트는 다른 컴포넌트를 렌더링 할 수 있지만, 정의를 중첩해서는 안 된다.
    - 자식 컴포넌트에 부모 컴포넌트의 일부 데이터가 필요한 경우, props를 사용해 전달해야 한다.

# 컴포넌트 import 및 export하기

<aside>
💡 컴포넌트의 가장 큰 장점은 재사용성으로 컴포넌트를 조합할 수 있다는 것!

</aside>

- 컴포넌트를 분리하여 다른 파일로 만들면 찾기도 쉽고, 재사용하기 편하다!

## Root 컴포넌트란

- 컴포넌트들은 App.js라는 root 컴포넌트 파일에 존재한다.
    - 설정에 따라 root컴포넌트가 다른 파일에 위치할 수도 있다.
    - Next.js 처럼 파일 기반으로 라우팅하는 프레임워크일 경우 페이지별로 root 컴포넌트가 다를 수 있다.

## 컴포넌트를 import 하거나 export 하는 방법

- 한 컴포넌트를 다른 곳에서도 사용하게 된다면 파일을 나옮기는게 좋다.
    - 재사용성이 높아져 모듈로서 사용할 수 있다.
    - 단계
        1. 컴포넌트를 추가할 JS파일 생성
        2. 새로 만든 파일에서 함수 컴포넌트 export(default or named export)
        3. 컴포넌트를 사용할 파일에서 import

```jsx
import Gallery from './Gallery.js';

export default function App() {
  return (
    <Gallery />
  );
}
```

- Default 방식으로 Gallery import
- Root App 컴포넌트를 default 방법으로 export

```jsx
function Profile() {
  return (
    <img
      src="https://i.imgur.com/QIrZWGIs.jpg"
      alt="Alan L. Hart"
    />
  );
}

export default function Gallery() {
  return (
    <section>
      <h1>Amazing scientists</h1>
      <Profile />
      <Profile />
      <Profile />
    </section>
  );
}
```

- Profile 컴포넌트를 정의하지만, 해당 파일에서만 사용되기에 export되지 않음.
- Default 방식으로 Gallery 컴포넌트 export

<aside>
💡 .js와 같은 파일 확장자가 없을 때도 있다.

</aside>

## 한 파일에서 여러 컴포넌트를 import 하거나 export 하는 방법

<aside>
💡 한 파일에서는 단 하나의 default export만 사용할 수 있다.
named export는 여러 번 사용할 수 있다.

</aside>

- named export 방식

```jsx
export function Profile() {
  // ...
}
```

```jsx
import { Profile } from './Gallery.js';
```

- 이렇게 되면 Gallery.js 에는 default Gallery export, named Profile export 두 가지 export가 존재하게 된다.

# JSX로 마크업 작성하기

<aside>
💡 JSX는 JS를 확장한 문법으로, JS파일을 HTML과 비슷하게 마크업을 작성할 수 있다.

</aside>

- 컴포넌트를 작성하는 다른 방법도 있지만, 대부분의 React 개발자는 JSX의 간결함을 선호하며 대부분의 코드 베이스에서 JSX를 사용한다.

## JSX: JS에 마크업 넣기

- Web 초반엔 HTML, CSS, JS를 분리된 파일로 관리하고 따로 관리했다.
- 요즘엔 Web의 상호작용이 많아지면서 로직이 내용을 결정하는 경우가 많아졌다.
    - 그래서 JS가 HTML을 담당하게 되었다.
        - React에서 렌더링 로직과 마크업이 같은 위치에 함께 있게 된 이유(컴포넌트)

![Untitled](1%E1%84%8C%E1%85%AE%E1%84%8E%E1%85%A1%20UI%20%E1%84%91%E1%85%AD%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20e9a9af679d334aa5a15f063bd3ea0e36/Untitled.png)

- 버튼의 렌더링 로직과 버튼의 마크업이 함께 있으면 변화가 생길 때마다 서로 동기화 상태를 유지할 수 있다.
    - 반면 버튼의 마크업과 사이드바의 마크업처럼 서로 관련이 없는 항목들은 분리되어 있기에 각 개별적으로 변경 하는 것이 더 안전하다.

**정리**

1. 각 React 컴포넌트는 React가 브라우저에 마크업을 렌더링할 수 있는 JS 함수이다.
2. React 컴포넌트는 JSX라는 확장된 문법을 사용하여 마크업을 나타낸다.
3. JSX는 HTML과 비슷해 보이지만, 조금 더 엄격하며 동적으로 정보를 표시할 수 있다.

<aside>
💡 JSX와 React는 서로 다른 별개의 개념이다. 종종 함께 사용되기도 하지만 [독립적으로](https://ko.react.dev/blog/2020/09/22/introducing-the-new-jsx-transform.html#whats-a-jsx-transform) 사용할 수도 있다. JSX는 확장된 문법이고, React는 JavaScript 라이브러리 이다.

</aside>

## HTML을 JSX로 변환하기

```html
<h1>Hedy Lamarr's Todos</h1>
<img
  src="https://i.imgur.com/yXOvdOSs.jpg"
  alt="Hedy Lamarr"
  class="photo"
>
<ul>
    <li>Invent new traffic lights
    <li>Rehearse a movie scene
    <li>Improve the spectrum technology
</ul>
```

- 위 코드를 변환해 보자.

```jsx
export default function TodoList() {
  return (
    // 이것은 동작하지 않습니다!
    <h1>Hedy Lamarr's Todos</h1>
    <img
      src="https://i.imgur.com/yXOvdOSs.jpg"
      alt="Hedy Lamarr"
      class="photo"
    >
    <ul>
      <li>Invent new traffic lights
      <li>Rehearse a movie scene
      <li>Improve the spectrum technology
    </ul>
  );
}
```

- 그냥 함수 내부에 붙여넣기 하면 동작하지 않는다.
    - 규칙이 있기 때문이다.

<aside>
💡 대부분의 경우 React의 화면 오류 메시지는 문제가 있는 곳을 찾는 데 도움을 준다.

</aside>

## JSX의 규칙

### 1. 하나의 루트 엘리먼트로 반환하기

- 한 컴포넌트에서는 하나의 엘리먼트 만을 반환할 수 있다.
    - 따라서 여러 엘러먼트를 반환하고자 한다면 하나의 부모 테그로 감싸야 한다.

```jsx
<div>
  <h1>Hedy Lamarr's Todos</h1>
  <img
    src="https://i.imgur.com/yXOvdOSs.jpg"
    alt="Hedy Lamarr"
    class="photo"
  >
  <ul>
    ...
  </ul>
</div>
```

- <div/>를 사용하기 싫다면 <> </> 로 대체할 수 있다.
    - 빈 태그를 Fragment 라고 한다.
- ****JSX 태그를 하나로 감싸줘야 하는 이유****
    - JSX는 HTML처럼 보이지만 내부적으로는 일반 JavaScript 객체로 변환된다. 하나의 배열로 감싸지 않은 하나의 함수에서는 두 개의 객체를 반환할 수 없다. 따라서 또 다른 태그나 Fragment로 감싸지 않으면 두 개의 JSX 태그를 반환할 수 없다.
    

### 2. 모든 태그는 닫아주기

- JSX에서는 태그를 명시적으로 닫아야 한다.
    - <img> 처럼 자체적으로 닫아주는 태그는 반드시 <img/> 형태로 작성해야 한다.

### 3. 대부분 캐멀 케이스로

- JSX는 JS로 바뀌고 JSX에서 작성된 어트리뷰트는 JS 객체의 키가 된다.
    - 컴포넌트에서는 종종 어트리뷰트를 변수로 읽고 싶은 경우가 있다.
- 변수명에는 제한이 있는데, 대시를 포함하거나 class 처럼 예약어가 그 예시이다.
- 이것이 어트리뷰트 대부분이 캐멀 케이스로 작성되는 이유이다.

```jsx
<img
  src="https://i.imgur.com/yXOvdOSs.jpg"
  alt="Hedy Lamarr"
  className="photo"
/>
```

<aside>
💡 역사적인 이유로, `[aria-*](https://developer.mozilla.org/docs/Web/Accessibility/ARIA)`와 `[data-*](https://developer.mozilla.org/docs/Learn/HTML/Howto/Use_data_attributes)`의 어트리뷰트는 HTML에서와 동일하게 대시를 사용하여 작성한다.

</aside>

### 추천 팁 : JSX 변환기 이용하기

- [변환기](https://transform.tools/html-to-jsx)를 사용하여 기존 HTML과 SVG를 JSX로 변환하는 것을 추천한다.

# 중괄호가 있는 JSX 안에서 JS 사용하기

<aside>
💡 JSX에 JavaScript 로직을 추가하거나 해당 마크업 내부의 동적인 프로퍼티를 참조하고 싶을 수 있다. 이 상황에서는 JSX에서 중괄호를 사용하여 JavaScript를 사용할 수 있다.

</aside>

## 따옴표로 문자열 전달하기

- 문자열 어트리뷰트를 JSX에 전달하려면 작은따옴표나 큰따옴표로 묶어야 한다.

```jsx
export default function Avatar() {
  return (
    <img
      className="avatar"
      src="https://i.imgur.com/7vQD0fPs.jpg"
      alt="Gregorio Y. Zara"
    />
  );
}
```

- 여기에서는 `"https://i.imgur.com/7vQD0fPs.jpg"`와 `"Gregorio Y. Zara"`가 문자열로 전달되고 있다.

- 동적으로 전달하고자 한다면?

```jsx
export default function Avatar() {
  const avatar = 'https://i.imgur.com/7vQD0fPs.jpg';
  const description = 'Gregorio Y. Zara';
  return (
    <img
      className="avatar"
      src={avatar}
      alt={description}
    />
  );
}
```

- **`"`와`"`를 `{`와`}`로 바꿔 JavaScript의 값을 사용할 수 있다**.

## ****중괄호 사용하기: JavaScript 세계로 연결하는 창****

- 중괄호 `{ }` 사이에서 JavaScript를 사용할 수 있다. 아래 예시는 `name`을 선언한 다음 `<h1>` 내부에 중괄호로 포함한다.

```jsx
export default function TodoList() {
  const name = 'Gregorio Y. Zara';
  return (
    <h1>{name}'s To Do List</h1>
  );
}
```

- `formatDate()`와 같은 함수 호출을 포함해 모든 JavaScript 표현식은 중괄호 사이에서 작동한다.

```jsx
const today = new Date();

function formatDate(date) {
  return new Intl.DateTimeFormat(
    'en-US',
    { weekday: 'long' }
  ).format(date);
}

export default function TodoList() {
  return (
    <h1>To Do List for {formatDate(today)}</h1>
  );
}
```

### 중괄호를 사용하는 곳

1. JSX 태그 안의 **문자**: `<h1>{name}'s To Do List</h1>`는 작동하지만, `<{tag}>Gregorio Y. Zara's To Do List</{tag}>`는 작동하지 않는다.
2. `=` 바로 뒤에 오는 **어트리뷰트**: `src={avatar}`는 `avatar` 변수를 읽지만 `src="{avatar}"`는 `"{avatar}"` 문자열을 전달한다.

## ****“이중 중괄호” 사용하기: JSX의 CSS와 다른 객체****

- JSX에서 객체를 전달하려면 `person={{ name: "Hedy Lamarr", inventions: 5 }}`와 같이 다른 중괄호 쌍으로 객체를 감싸야 한다.
- 인라인 스타일이 필요할 때 `style` 어트리뷰트에 객체를 전달해야 합니다.

```jsx
export default function TodoList() {
  return (
    <ul style={{
      backgroundColor: 'black',
      color: 'pink'
    }}>
      <li>Improve the videophone</li>
      <li>Prepare aeronautics lectures</li>
      <li>Work on the alcohol-fuelled engine</li>
    </ul>
  );
}
```

- JSX에서 `{{` 와 `}}` 를 본다면 JSX 중괄호 안의 객체에 불과하다는 것을 알아야 한다.

<aside>
💡 인라인 `style` 프로퍼티는 캐멀 케이스로 작성됩니다. 예를 들어 HTML에서의 `<ul style="background-color: black">`은 컴포넌트에서 `<ul style={{ backgroundColor: 'black' }}>`로 작성됩니다.

</aside>

## ****JavaScript 객체와 중괄호에 대해서 더 알아보기****

- 여러 표현식을 하나의 객체로 옮기고 중괄호 안의 JSX에서 참조할 수 있다.

```jsx
const person = {
  name: 'Gregorio Y. Zara',
  theme: {
    backgroundColor: 'black',
    color: 'pink'
  }
};

export default function TodoList() {
  return (
    <div style={person.theme}>
      <h1>{person.name}'s Todos</h1>
      <img
        className="avatar"
        src="https://i.imgur.com/7vQD0fPs.jpg"
        alt="Gregorio Y. Zara"
      />
      <ul>
        <li>Improve the videophone</li>
        <li>Prepare aeronautics lectures</li>
        <li>Work on the alcohol-fuelled engine</li>
      </ul>
    </div>
  );
}
```

- 이 예시에서 `person` 객체는 `name` 문자열과 `theme` 객체를 포함한다.

# 컴포넌트에 props 전달하기

<aside>
💡 React 컴포넌트는 props를 이용해 서로 통신합니다. 모든 부모 컴포넌트는 props를 줌으로써 몇몇의 정보를 자식 컴포넌트에게 전달할 수 있다.

</aside>

- props는 HTML 어트리뷰트를 생각나게 할 수도 있지만, 객체, 배열, 함수를 포함한 모든 JavaScript 값을 전달할 수 있다.

## 친숙한 props

<aside>
💡 props는 JSX 태그에 전달하는 정보이다. 예를 들어, `className`, `src`, `alt`, `width`, `height`는 `<img>` 태그에 전달할 수 있다.

</aside>

```jsx
function Avatar() {
  return (
    <img
      className="avatar"
      src="https://i.imgur.com/1bX5QH6.jpg"
      alt="Lin Lanying"
      width={100}
      height={100}
    />
  );
}

export default function Profile() {
  return (
    <Avatar />
  );
}
```

- `<img>` 태그에 전달할 수 있는 props는 미리 정의되어 있다. (ReactDOM은 [HTML 표준](https://www.w3.org/TR/html52/semantics-embedded-content.html#the-img-element)을 준수합니다.) 자신이 생성한 `<Avatar>`와 같은 어떤 컴포넌트든 props를 전달할 수 있다.

## 컴포넌트에 props 전달하기

```jsx
export default function Profile() {
  return (
    <Avatar />
  );
}
```

- 위 코드에서 Profile 컴포넌트는 자식 컴포넌트인 Avatar에 어떤 props도 전달하지 않는다.

### 1단계 : ****자식 컴포넌트에 props 전달하기****

```jsx
export default function Profile() {
  return (
    <Avatar
      person={{ name: 'Lin Lanying', imageId: '1bX5QH6' }}
      size={100}
    />
  );
}
```

- `Avatar`에 몇몇 props를 전달한다. 예를 들어 `person` (객체)와 `size` (숫자)를 전달해 보았다.

<aside>
💡 `person=` 뒤에 있는 이중 괄호가 혼란스럽다면, [JSX 중괄호 안의 객체](https://ko.react.dev/learn/javascript-in-jsx-with-curly-braces#using-double-curlies-css-and-other-objects-in-jsx)라고 기억하시면 된다.

</aside>

### 2단계 : ****자식 컴포넌트 내부에서 props 읽기****

<aside>
💡 이러한 props는 `function Avatar` 바로 뒤에 있는 `({`와 `})` 안에 그들의 이름인 `person, size` 등을 쉼표로 구분함으로써 읽을 수 있다.

</aside>

- 이렇게 하면 `Avatar` 코드 내에서 변수를 사용하는 것처럼 사용할 수 있다.

```jsx
import { getImageUrl } from './utils.js';

function Avatar({ person, size }) {
  return (
    <img
      className="avatar"
      src={getImageUrl(person)}
      alt={person.name}
      width={size}
      height={size}
    />
  );
}

export default function Profile() {
  return (
    <div>
      <Avatar
        size={100}
        person={{ 
          name: 'Katsuko Saruhashi', 
          imageId: 'YfeOqp2'
        }}
      />
      <Avatar
        size={80}
        person={{
          name: 'Aklilu Lemma', 
          imageId: 'OKS67lh'
        }}
      />
      <Avatar
        size={50}
        person={{ 
          name: 'Lin Lanying',
          imageId: '1bX5QH6'
        }}
      />
    </div>
  );
}
```

- props를 사용하면 부모 컴포넌트와 자식 컴포넌트를 독립적으로 생각할 수 있다.
- `Avatar` 가 props를 어떻게 사용하는지 생각할 필요 없이  `Profile`의 `person` 또는 `size` props를 수정할 수 있다.
    - 마찬가지로 `Profile`을 보지 않고도 `Avatar`가 props를 사용하는 방식을 바꿀 수 있다.
- 사실 props는 컴포넌트에 대한 유일한 인자이다.

```jsx
function Avatar(props) {
  let person = props.person;
  let size = props.size;
  // ...
}
```

## props의 기본값 지정하기

- 값이 지정되지 않았을 때, prop에 기본값을 주길 원한다면, 변수 바로 뒤에 `=` 과 함께 기본값을 넣어 구조 분해 할당을 해줄 수 있다.

```jsx
function Avatar({ person, size = 100 }) {
  // ...
}
```

- `<Avatar person={...} />`가 `size` prop이 없이 렌더링 된다면, `size`는 `100`으로 설정된다.
- 이 [기본값](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/Default_parameters)은 size prop이 없거나 `size={undefined}`로 전달될 때 사용된다. 그러나 `size={null}`  또는 `size={0}`으로 전달된다면, 기본값은 사용되지 **않는다**.

## ****JSX spread 문법으로 props 전달하기****

```jsx
function Profile({ person, size, isSepia, thickBorder }) {
  return (
    <div className="card">
      <Avatar
        person={person}
        size={size}
        isSepia={isSepia}
        thickBorder={thickBorder}
      />
    </div>
  );
}
```

```jsx
function Profile(props) {
  return (
    <div className="card">
      <Avatar {...props} />
    </div>
  );
}
```

- 이렇게 하면 `Profile`의 모든 props를 각각의 이름을 나열하지 않고 `Avatar`로 전달한다.

## ****자식을 JSX로 전달하기****

```jsx
<Card>
  <Avatar />
</Card>
```

- JSX 태그 내에 콘텐츠를 중첩하면, 부모 컴포넌트는 해당 콘텐츠를 `children`이라는 prop으로 받는다.

```jsx
import Avatar from './Avatar.js';

function Card({ children }) {
  return (
    <div className="card">
      {children}
    </div>
  );
}

export default function Profile() {
  return (
    <Card>
      <Avatar
        size={100}
        person={{ 
          name: 'Katsuko Saruhashi',
          imageId: 'YfeOqp2'
        }}
      />
    </Card>
  );
}
```

- 위 `Card` 컴포넌트는 `<Avatar />`로 설정된 `children` prop을 받아 이를 래퍼 div에 렌더링 할 것입니다.

## 시간에 따라 props가 변하는 방식

- 아래의 `Clock` 컴포넌트는 부모 컴포넌트로부터 `color`와 `time`이라는 두 가지 props를 받는다.

```jsx
export default function Clock({ color, time }) {
  return (
    <h1 style={{ color: color }}>
      {time}
    </h1>
  );
}
```

- **컴포넌트가 시간에 따라 다른 props를 받을 수 있음을 보여준다.**
    - Props는 항상 고정되어 있지 않다!
- `time` prop은 매초 변경되고, `color` prop은 다른 색상을 선택하면 변경된다.
    - Props는 컴포넌트의 데이터를 처음에만 반영하는 것이 아니라 모든 시점에 반영한다.
- 그러나 props는 컴퓨터 과학에서 “변경할 수 없다”라는 의미의 [불변성](https://en.wikipedia.org/wiki/Immutable_object)을 가지고 있다.
- 컴포넌트가 props를 변경해야 하는 경우(예: 사용자의 상호작용이나 새로운 데이터에 대한 응답), 부모 컴포넌트에 *다른 props*, 즉 새로운 객체를 전달하도록 “요청”해야 한다! 그러면 이전의 props는 버려지고, 결국 자바스크립트 엔진은 기존 props가 차지했던 메모리를 회수하게 됩니다.

<aside>
💡 **“props 변경”을 시도하지 마세요.** 선택한 색을 변경하는 등 사용자 입력에 반응해야 하는 경우에는 [State: 컴포넌트의 메모리](https://ko.react.dev/learn/state-a-components-memory)에서 배울 “set state”가 필요할 것입니다.

</aside>

# 조건부 렌더링

<aside>
💡 리액트는 `if` 문, `&&` 및 `? :` 연산자와 같은 자바스크립트 문법을 사용하여 조건부로 JSX를 렌더링할 수 있다.

</aside>

## ****조건부로 JSX 반환하기****

```jsx
function Item({ name, isPacked }) {
  if (isPacked) {
    return <li className="item">{name} ✔</li>;
  }
  return <li className="item">{name}</li>;
}

export default function PackingList() {
  return (
    <section>
      <h1>Sally Ride's Packing List</h1>
      <ul>
        <Item 
          isPacked={true} 
          name="Space suit" 
        />
        <Item 
          isPacked={true} 
          name="Helmet with a golden leaf" 
        />
        <Item 
          isPacked={false} 
          name="Photo of Tam" 
        />
      </ul>
    </section>
  );
}
```

- `isPacked` prop이 `true`이면 이 코드는 **다른 JSX 트리를 반환한다.** 이로 인해 일부 항목은 끝에 체크 표시가 있다.

## ****조건부로 `null`을 사용하여 아무것도 반환하지 않기**

- 아무것도 렌더링하고 싶지 않을 때 사용.

```jsx
function Item({ name, isPacked }) {
  if (isPacked) {
    return null;
  }
  return <li className="item">{name}</li>;
}

export default function PackingList() {
  return (
    <section>
      <h1>Sally Ride's Packing List</h1>
      <ul>
        <Item 
          isPacked={true} 
          name="Space suit" 
        />
        <Item 
          isPacked={true} 
          name="Helmet with a golden leaf" 
        />
        <Item 
          isPacked={false} 
          name="Photo of Tam" 
        />
      </ul>
    </section>
  );
}
```

- `isPacked`가 `true`라면 컴포넌트는 아무것도 반환하지 않지만, `false`라면 JSX가 반환됨.
- 하지만 이는 흔하게 사용하지 않는다.

## ****조건부로 JSX 포함시키기****

```jsx
<li className="item">{name} ✔</li>
```

```jsx
<li className="item">{name}</li>
```

- 위 두 코드는 매우 비슷하다.
    - 위 코드를 리팩토링 해보자.

### ****삼항 조건 연산자 (`? :`)**

```jsx
if (isPacked) {
  return <li className="item">{name} ✔</li>;
}
return <li className="item">{name}</li>;
```

```jsx
return (
  <li className="item">
    {isPacked ? name + ' ✔' : name}
  </li>
);
```

- 위 코드 대신 아래 코드를 사용하면 된다.

```jsx
function Item({ name, isPacked }) {
  return (
    <li className="item">
      {isPacked ? (
        <del>
          {name + ' ✔'}
        </del>
      ) : (
        name
      )}
    </li>
  );
}

export default function PackingList() {
  return (
    <section>
      <h1>Sally Ride's Packing List</h1>
      <ul>
        <Item 
          isPacked={true} 
          name="Space suit" 
        />
        <Item 
          isPacked={true} 
          name="Helmet with a golden leaf" 
        />
        <Item 
          isPacked={false} 
          name="Photo of Tam" 
        />
      </ul>
    </section>
  );
}
```

- 위 스타일 코드는 간단한 조건에 잘 어울리나, 적당히 사용해야 한다.
    - 중첩된 조건부 마크업이 너무 많아 컴포넌트가 지저분해지면 추출해서 정리하는게 좋다.

## ****논리 AND 연산자 (`&&`)**

- “`isPacked`이면 (`&&`) 체크 표시를 렌더링하고, 그렇지 않으면 아무것도 렌더링하지 않는다.”

```jsx
function Item({ name, isPacked }) {
  return (
    <li className="item">
      {name} {isPacked && '✔'}
    </li>
  );
}

export default function PackingList() {
  return (
    <section>
      <h1>Sally Ride's Packing List</h1>
      <ul>
        <Item 
          isPacked={true} 
          name="Space suit" 
        />
        <Item 
          isPacked={true} 
          name="Helmet with a golden leaf" 
        />
        <Item 
          isPacked={false} 
          name="Photo of Tam" 
        />
      </ul>
    </section>
  );
}
```

<aside>
💡 조건을 테스트하기 위해 JavaScript는 자동으로 왼쪽을 부울로 변환한다. 그러나 왼쪽이 `0`이면 전체 식이 (`0`)을 얻게 되고, 리액트는 아무것도 아닌 `0`을 렌더링할 것이다.

</aside>

## ****변수에 조건부로 JSX를 할당하기****

- 위와 같은 방법이 일반 코드를 작성하는 데 방해가 되면 `if` 문과 변수를 사용. `[let](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/let)`으로 정의된 변수는 재할당할 수 있으므로 표시할 기본 내용인 이름을 먼저 대입.

```jsx
function Item({ name, isPacked }) {
  let itemContent = name;
  if (isPacked) {
    itemContent = (
      <del>
        {name + " ✔"}
      </del>
    );
  }
  return (
    <li className="item">
      {itemContent}
    </li>
  );
}

export default function PackingList() {
  return (
    <section>
      <h1>Sally Ride's Packing List</h1>
      <ul>
        <Item 
          isPacked={true} 
          name="Space suit" 
        />
        <Item 
          isPacked={true} 
          name="Helmet with a golden leaf" 
        />
        <Item 
          isPacked={false} 
          name="Photo of Tam" 
        />
      </ul>
    </section>
  );
}
```

# 리스트 렌더링

<aside>
💡 데이터 모음에서 유사한 컴포넌트를 여러 개 표시하고 싶을 때가 종종 있다. [JavaScript 배열 메서드](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array#)를 사용하여 데이터 배열을 조작할 수 있다.

</aside>

- React에서 filter()와  map()을 사용해 데이터 배열을 필터링하고 컴포넌트 배열로 변환.

## ****배열을 데이터로 렌더링하기****

```jsx
<ul>
  <li>Creola Katherine Johnson: mathematician</li>
  <li>Mario José Molina-Pasquel Henríquez: chemist</li>
  <li>Mohammad Abdus Salam: physicist</li>
  <li>Percy Lavon Julian: chemist</li>
  <li>Subrahmanyan Chandrasekhar: astrophysicist</li>
</ul>
```

- 위 코드를 리팩토링 해보자.
1. 데이터를 배열로 이동.

```jsx
const people = [
  'Creola Katherine Johnson: mathematician',
  'Mario José Molina-Pasquel Henríquez: chemist',
  'Mohammad Abdus Salam: physicist',
  'Percy Lavon Julian: chemist',
  'Subrahmanyan Chandrasekhar: astrophysicist'
];
```

1. `people`의 요소를 새로운 JSX 노드 배열인 `listItems`에 **매핑**.

```jsx
const listItems = people.map(person => <li>{person}</li>);
```

1. `<ul>`로 래핑된 컴포넌트의 `listItems`를 **반환**.

```jsx
return <ul>{listItems}</ul>;
```

- 완성된 코드

```jsx
const people = [
  'Creola Katherine Johnson: mathematician',
  'Mario José Molina-Pasquel Henríquez: chemist',
  'Mohammad Abdus Salam: physicist',
  'Percy Lavon Julian: chemist',
  'Subrahmanyan Chandrasekhar: astrophysicist'
];

export default function List() {
  const listItems = people.map(person =>
    <li>{person}</li>
  );
  return <ul>{listItems}</ul>;
}
```

## ****배열의 항목들을 필터링하기****

- filter() 메서드는 항목 배열을 받아 “test”(`true` 혹은 `false`를 반환하는 함수)를 통과한 후 테스트에 통과된 항목(`true`가 반환된 항목)만 있는 새로운 배열을 반환한다.

```jsx
const people = [{
  id: 0,
  name: 'Creola Katherine Johnson',
  profession: 'mathematician',
}, {
  id: 1,
  name: 'Mario José Molina-Pasquel Henríquez',
  profession: 'chemist',
}, {
  id: 2,
  name: 'Mohammad Abdus Salam',
  profession: 'physicist',
}, {
  name: 'Percy Lavon Julian',
  profession: 'chemist',
}, {
  name: 'Subrahmanyan Chandrasekhar',
  profession: 'astrophysicist',
}];
```

1. `people`에서 `filter()`를 호출해 `person.profession === 'chemist'`로 필터링해서 “chemist”로만 구성된 새로운 배열 `chemists`를 **생성**.
    
    ```jsx
    const chemists = people.filter(person =>
      person.profession === 'chemist'
    );
    ```
    
2. 이제 `chemists`를 **매핑**.
    
    ```jsx
    const listItems = chemists.map(person =>
      <li>
         <img
           src={getImageUrl(person)}
           alt={person.name}
         />
         <p>
           <b>{person.name}:</b>
           {' ' + person.profession + ' '}
           known for {person.accomplishment}
         </p>
      </li>
    );
    ```
    
3. 마지막으로 컴포넌트에서 `listItems`를 **반환**.
    
    ```jsx
    return <ul>{listItems}</ul>;
    ```
    
    - 완성된 코드
    
    ```jsx
    import { people } from './data.js';
    import { getImageUrl } from './utils.js';
    
    export default function List() {
      const chemists = people.filter(person =>
        person.profession === 'chemist'
      );
      const listItems = chemists.map(person =>
        <li>
          <img
            src={getImageUrl(person)}
            alt={person.name}
          />
          <p>
            <b>{person.name}:</b>
            {' ' + person.profession + ' '}
            known for {person.accomplishment}
          </p>
        </li>
      );
      return <ul>{listItems}</ul>;
    }
    ```
    

<aside>
💡 화살표 함수는 암시적으로 `=>` 바로 뒤에 식을 반환하기 때문에 `return` 문이 필요하지 않다.
하지만 **`=>` 뒤에 `{` 중괄호가 오는 경우 `return`을 명시적으로 작성해야 한다!**

</aside>

## ****`key`를 사용해서 리스트 항목을 순서대로 유지하기**

<aside>
💡 각 배열 항목에 다른 항목 중에서 고유하게 식별할 수 있는 문자열 또는 숫자를 `key`로 지정해야 한다.

</aside>

- Key는 각 컴포넌트가 어떤 배열 항목에 해당하는지 React에 알려주어 나중에 일치시킬 수 있도록 한다.
- 즉석에서 key를 생성하는 대신 데이터 안에 key를 포함해야 합니다.

### ****`key`를 가져오는 곳**

- **데이터베이스의 데이터:** 데이터베이스에서 데이터를 가져오는 경우 본질적으로 고유한 데이터베이스 key/ID를 사용할 수 있다.
- **로컬에서 생성된 데이터:** 데이터가 로컬에서 생성되고 유지되는 경우(예: 메모 작성 앱의 노트), 항목을 만들 때 증분 일련번호나 `[crypto.randomUUID()](https://developer.mozilla.org/en-US/docs/Web/API/Crypto/randomUUID)` 또는 `[uuid](https://www.npmjs.com/package/uuid)` 같은 패키지를 사용.

### ****key 규칙****

- **key는 형제 간에 고유해야 한다.** 하지만 같은 key를 *다른* 배열의 JSX 노드에 동일한 key를 사용해도 괜찮다.
- **key는 변경되어서는 안 되며** 그렇게 되면 key는 목적에 어긋난다! 렌더링 중에는 key를 생성하지 말자.

### ****React에 key가 왜 필요한 이유는 무엇인가요?****

- 식별하는게 제일 중요한 이유.
    - 삭제, 이동시 참고해야 한다.

<aside>
💡 index를 key로 사용하면 버그가 발생할 확률이 있다.

</aside>

<aside>
💡 `key={Math.random()}`처럼 즉석에서 key를 생성하면 안된다. 이렇게 하면 렌더링 간에 key가 일치하지 않아 모든 컴포넌트와 DOM이 매번 다시 생성될 수 있다.

</aside>

<aside>
💡 컴포넌트가 `key`를 prop으로 받지 않는다는 점에 유의. key는 React 자체에서 힌트로만 사용된다. 컴포넌트에 ID가 필요하다면 `<Profile key={id} userId={id} />`와 같이 별도의 prop으로 전달해야 한다.

</aside>

# ****컴포넌트 순수하게 유지하기****

<aside>
💡 컴포넌트를 엄격하게 순수함수로 작성하면 코드베이스가 점점 커지더라도 예상밖의 동작이나 당황케하는 버그를 피할 수 있다.

</aside>

## ****순수성: 공식으로서의 컴포넌트****

- 컴퓨터 과학에서 [순수 함수](https://wikipedia.org/wiki/Pure_function)는 다음과 같은 특징을 지니고 있는 함수이다.
    - **자신의 일에 집중한다.** 함수가 호출되기 전에 존재했던 어떤 객체나 변수는 변경하지 않는다.
    - **같은 입력, 같은 출력** 같은 입력이 주어졌다면 순수함수는 같은 결과를 반환해야 한다.

## ****사이드 이펙트: 의도하지(않은) 결과****

<aside>
💡 React의 렌더링 과정은 항상 순수해야 한다. 컴포넌트는 렌더링하기 전에 존재했던 객체나 변수들을 *변경*하지 말고 컴포넌트를 순수하지 않도록하는 JSX만 *반환*해야한다.

</aside>

- 아래는 규칙을 위반하는 컴포넌트

```jsx
let guest = 0;

function Cup() {
  // 나쁜 지점: 이미 존재했던 변수를 변경하고 있다!
  guest = guest + 1;
  return <h2>Tea cup for guest #{guest}</h2>;
}

export default function TeaSet() {
  return (
    <>
      <Cup />
      <Cup />
      <Cup />
    </>
  );
}
```

- 이건 **컴포넌트가 여러번 불리면 다른 JSX를 생성한다는 것을 의미한다!**

## ****지역 변형: 컴포넌트의 작은 비밀****

- **렌더링하는 동안 *그냥* 만든 변수와 객체를 변경하는 것은 전혀 문제가 없다.**

```jsx
function Cup({ guest }) {
  return <h2>Tea cup for guest #{guest}</h2>;
}

export default function TeaGathering() {
  let cups = [];
  for (let i = 1; i <= 12; i++) {
    cups.push(<Cup key={i} guest={i} />);
  }
  return cups;
}
```

- 만약 `cups` 변수나 `[]` 배열이 `TeaGathering`의 바깥에서 생성되었다면 큰 문제가 된다.
    - 기존 객체 변경 가능성이 있기 때문

## ****부작용을 *일으킬 수 있는* 지점**

- 함수형 프로그래밍은 순수성에 크게 의존하지만, 언젠가는, 어딘가에서, *무언가가* 바뀌어야 합니다. 그것이 프로그래밍의 요점.
    - 이러한 변화들-화면을 업데이트하고, 애니메이션을 시작하고, 데이터를 변경하는 것을 **사이드 이펙트라고 함.**
    - 렌더링중에 발생하는 것이 아니라 *“사이드에서,”* 발생하는 현상.
- 리액트에선, **사이드 이펙트는 보통 [이벤트 핸들러](https://ko.react.dev/learn/responding-to-events)에 포함됨.**
    - 이벤트 핸들러가 컴포넌트 *내부에* 정의되었다 하더라도 렌더링 *중에는* 실행되지 않는다!
        - **그래서 이벤트 핸들러는 순수할 필요가 없다.**
- 다른 옵션을 모두 사용했지만 사이드 이펙트에 적합한 이벤트 핸들러를 찾을 수 없는 경우에도, 컴포넌트에서 `[useEffect](https://ko.react.dev/reference/react/useEffect)` 호출을 사용하여 반환된 JSX에 해당 이벤트 핸들러를 연결할 수 있다.
    - 이것은 리액트에게 사이드 이펙트가 허용될 때 렌더링 후 나중에 실행하도록 지시한다. **그러나 이 접근 방식이 마지막 수단이 되어야 한다.**