# 01. UI 표현하기


### **React**

- 사용자 인터페이스 (UI)를 렌더링하기 위한 JavaScript 라이브러리
- UI - 버튼, 텍스트, 이미지와 같은 작은 요소로 구성됨
- React를 통해 작은 요소들을 재사용 가능하고 중첩할 수 있는 컴포넌트로 조합할 수 있음


## 첫 컴포넌트

- React 애플리케이션은 컴포넌트라고 불리는 독립된 UI 조각들로 이루어짐
- React 컴포넌트는 마크업을 얹을 수 있는 JavaScript 함수


### **컴포넌트: UI 구성 요소**

- 마크업 - 스타일을 위한 CSS, 상호작용을 위한 JavaScript와 결합하여 웹에서 볼 수 있는 모든 UI의 기반이 됨
- React 사용 → 마크업, CSS, JavaScript를 **앱의 재사용 가능한 UI 요소인** 사용자 정의 “컴포넌트”로 결합할 수 있음
- HTML 태그와 마찬가지로 컴포넌트를 작성, 순서 지정 및 중첩하여 전체 페이지를 디자인할 수 있음
- 이미 작성한 컴포넌트를 재사용하여 많은 디자인을 구성할 수 있으므로 개발 속도가 빨라짐
    - ex) [Chakra UI](https://chakra-ui.com/), [Material UI.](https://material-ui.com/)와 같은 React 오픈 소스 커뮤니티에서 공유되는 수천 개의 컴포넌트로 프로젝트를 빠르게 시작할 수도 있음


### **컴포넌트 정의하기**

**React 컴포넌트는 *마크업으로 뿌릴 수 있는 JavaScript* 함수**

**1단계: 컴포넌트 내보내기**

`export default` 접두사는 [표준 JavaScript 구문](https://developer.mozilla.org/docs/web/javascript/reference/statements/export)

→ 이 접두사를 사용하면 나중에 다른 파일에서 가져올 수 있도록 파일에 주요 기능을 표시할 수 있음

**2단계: 함수 정의하기**

<aside>
💡 React 컴포넌트는 일반 JavaScript 함수이지만, 이름은 대문자로 시작해야 하며 그렇지 않으면 작동하지 않습니다!
</aside>

`function Profile() { }`을 사용하면 `Profile`이라는 이름의 JavaScript함수를 정의할 수 있음

**3단계: 마크업 추가하기**

<aside>
💡 괄호가 없으면 `return` 뒷 라인에 있는 모든 코드가 무시됩니다
</aside>

**JSX**

- HTML처럼 태그<>로 작성되었지만 실제로는 JavaScript인 구문
- JavaScript 안에 마크업을 삽입할 수 있음


**컴포넌트 사용하기**

`Profile` 컴포넌트를 정의했으므로 다른 컴포넌트 안에 중첩할 수 있음


**브라우저에 표시되는 내용**

<aside>
💡 대소문자의 차이에 주목
</aside>

- <section>은 소문자 → React는 HTML 태그를 가리킨다고 이해함
- <Profile />은 대문자로 시작 → React는 Profile이라는 컴포넌트를 사용하고자 한다고 이해함


**컴포넌트 중첩 및 구성**

<aside>
💡 컴포넌트를 한 번 정의한 다음 원하는 곳에서 원하는 만큼 여러 번 사용할 수 있다는 점이 바로 React의 마법
</aside>

- 컴포넌트 - 일반 JavaScript함수이므로 같은 파일에 여러 컴포넌트를 포함할 수 있음
- 컴포넌트가 상대적으로 작거나 서로 밀접하게 관련되어 있을 때 편리
- `Profile` 컴포넌트는 `Gallery`안에서 렌더링되기 때문 → `Gallery`는 각 `Profile`을 “자식”으로 렌더링하는 **부모 컴포넌트**

<aside>
💡 컴포넌트는 다른 컴포넌트를 렌더링할 수 있지만, 그 정의를 중첩해서는 안 됩니다.
</aside>

```jsx
export default function Gallery() {
  // 🔴 Never define a component inside another component!
  function Profile() {
    // ...
  }
  // ...
}
```

<aside>
💡 자식 컴포넌트에 부모 컴포넌트의 일부 데이터가 필요한 경우, 정의를 중첩하는 대신 props로 전달하세요.
</aside>

```jsx
export default function Gallery() {
  // ...
}

// ✅ Declare components at the top level
function Profile() {
  // ...
}
```

### **요약**

- React를 사용하면 앱의 재사용 가능한 UI 요소인 컴포넌트를 만들 수 있다!
- React 앱에서 모든 UI는 컴포넌트이다!
- React 컴포넌트는 다음 몇 가지를 제외하고는 일반적인 JavaScript 함수이다!
    - 컴포넌트의 이름은 항상 대문자로 시작한다!
    - JSX 마크업을 반환한다!

### **챌린지 도전하기**

**챌린지 1 of 4: 컴포넌트 내보내기**

root 컴포넌트를 내보내지 않았기 때문에 이 샌드박스는 작동하지 않습니다.

**Before**

```jsx
function Profile() {
  return (
    <img
      src="https://i.imgur.com/lICfvbD.jpg"
      alt="Aklilu Lemma"
    />
  );
}
```

**After**

```jsx
export default function Profile() {
  return (
    <img
      src="https://i.imgur.com/lICfvbD.jpg"
      alt="Aklilu Lemma"
    />
  );
}
```

**챌린지 2 of 4: return 문을 고치세요**

이 return 문에는 문제가 있습니다. 고칠 수 있나요?

**Before**

```jsx
export default function Profile() {
  return
    <img src="https://i.imgur.com/jA8hHMpm.jpg" alt="Katsuko Saruhashi" />;
}
```

**After**

```jsx
export default function Profile() {
  return <img src="https://i.imgur.com/jA8hHMpm.jpg" alt="Katsuko Saruhashi" />;
}
```

**챌린지 3 of 4: 실수를 찾아내세요.**

`Profile` 컴포넌트가 선언되고 사용되는 방식에 문제가 있습니다. 실수를 발견할 수 있을까요? (React가 컴포넌트를 일반 HTML 태그와 어떻게 구분하는지 기억해 보세요!)

**Before**

```jsx
function profile() {
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
      <profile />
      <profile />
      <profile />
    </section>
  );
}
```

**After**

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

**챌린지 4 of 4: 컴포넌트를 새로 작성해 보세요.**

컴포넌트를 처음부터 작성해 보세요. 유효한 이름을 지정하고 마크업을 반환할 수 있습니다. 아이디어가 떠오르지 않는다면 `<h1>Good job!</h1>` 라고 표시하는 `Congratulations` 컴포넌트를 작성할 수 있습니다. export를 잊지 마세요!

```jsx
// Write your component below!
function Hello() {
  return <h1>Good Job!</h1>;
}

export default function Main() {
  return <Hello/>;
}
```


## 컴포넌트 Import 및 Export 하기

**컴포넌트의 가장 큰 장점?** 

**재사용성으로 컴포넌트를 조합해 또 다른 컴포넌트를 만들 수 있다는 것**

컴포넌트를 여러 번 중첩하게 되면 다른 파일로 분리해야 하는 시점이 생김 → 분리하면 나중에 파일을 찾기 더 쉽고 재사용하기 편리해짐


### **Root 컴포넌트란**

예제의 컴포넌트들은 모두 `App.js`라는 **root 컴포넌트 파일**에 존재

설정에 따라 root 컴포넌트가 다른 파일에 위치할 수도 있음

Next.js처럼 파일 기반으로 라우팅하는 프레임워크일 경우 페이지별로 root 컴포넌트가 다를 수 있음


### **컴포넌트를 import 하거나 export 하는 방법**

<aside>
💡 가끔 `.js`와 같은 파일 확장자가 없을 때도 있음

</aside>

`Gallery` 컴포넌트와 `Profile` 컴포넌트를 root 컴포넌트가 아닌 다른 파일로 옮기는 게 좋음 → **재사용성이 높아져 컴포넌트를 모듈로 사용할 수 있음**


**컴포넌트를 다른 파일로 이동하는 단계**

1. 컴포넌트를 추가할 JS 파일을 생성
2. 새로 만든 파일에서 함수 컴포넌트를 export 함 ([default](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/export#using_the_default_export) 또는 [named](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/export#using_named_exports) export 방식을 사용합니다)
3. 컴포넌트를 사용할 파일에서 import 함 (적절한 방식을 선택해서 [default](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/import#importing_defaults) 또는 [named](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/import#import_a_single_export_from_a_module)로 import 합니다)


**예제**

App.js 파일에서 Profile과 Gallery 컴포넌트를 빼서 새로운 Gallery.js 파일로 옮김

이제 Gallery는 Gallery.js에서 import 해서 사용할 수 있음

**App.js**

```jsx
import Gallery from './Gallery.js';

export default function App() {
  return (
    <Gallery />
  );
}
```

- Default 방식으로 Gallery를 Gallery.js로부터 import 함
- Root App 컴포넌트를 default 방식으로 export 함

**Gallery.js**

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

- Profile 컴포넌트를 정의하고 해당 파일에서만 사용되기 때문에 export 되지 않음
- Default 방식으로 Gallery 컴포넌트를 export 함


### **한 파일에서 여러 컴포넌트를 import 하거나 export 하는 방법**

**한 파일에서는 단 하나의 default export만 사용할 수 있지만 named export는 여러 번 사용할 수 있음**

1. named export 방식을 사용해서 export 해보자 (`default` 키워드를 사용하지 않습니다)

```jsx
export function Profile() {
  // ...
}
```

2. named import 방식으로 Gallery.js 파일에서 Profile 컴포넌트를 App.js 파일로 import 하자. (중괄호를 사용합니다)

```jsx
import { Profile } from './Gallery.js';
```

3. 마지막으로 <Profile />을 App 컴포넌트에서 렌더링

```jsx
export default function App() {
  return <Profile />;
}
```

4. `App.js`에서는 두 컴포넌트를 import 해서 사용할 수 있다. 

```jsx
import Gallery from './Gallery.js';
import { Profile } from './Gallery.js';

export default function App() {
  return (
    <Profile />
  );
}
```

default와 named export 방식 둘 다 사용할 수 있게 됨

- **Gallery.js**
    - Named export 방식으로 Profile이라는 이름의 컴포넌트를 export 함
    - Default export 방식으로 Gallery 컴포넌트를 export 함
- **App.js**
    - Gallery.js에서 named import 방식으로 Profile 컴포넌트를 import 함
    - Gallery.js에서 default import 방식으로 Gallery 컴포넌트를 import 함
    - Default export 방식으로 App 컴포넌트를 export 함


### **요약**

- Root 컴포넌트란 무엇인지
- 컴포넌트를 import 하거나 export 하는 방법
- 언제 default 또는 named imports와 exports를 사용할지
- 한 파일에서 여러 컴포넌트를 export 하는 방법
    - 한 파일에서는 단 하나의 default export만 사용할 수 있지만 named export는 여러 번 사용할 수 있음


### **챌린지 도전하기**

**챌린지 1 of 1: 컴포넌트를 한 단계 더 분리하기**

현재 `Gallery.js` 파일이 `Profile`과 `Gallery`를 둘 다 export 해서 헷갈리게 할 수 있습니다.

`Profile.js` 파일을 생성해서 `Profile` 컴포넌트를 해당 파일로 옮기고 `App` 컴포넌트에서는 `<Profile />`과 `<Gallery />`를 각각 렌더링하도록 변경합니다.

Default 또는 named export를 사용해서 `Profile`을 export 할 수 있습니다. 다만 주의할 점은 사용한 export 방식에 맞는 import 문법을 사용해야 한다는 점입니다. 

**App.js**

```jsx
import Gallery from './Gallery.js';
import Profile from './Profile.js';

export default function App() {
  return (
    <div>
      <Profile />
    </div>
  );
}
```

**Gallery.js**

```jsx
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

**Profile.js**

```jsx
export default function Profile() {
  return (
    <img
      src="https://i.imgur.com/QIrZWGIs.jpg"
      alt="Alan L. Hart"
    />
  );
}
```


## JSX로 마크업 작성하기

<aside>
💡 JSX와 React는 서로 다른 별개의 개념입니다. 종종 함께 사용되기도 하지만 독립적으로 사용할 수도 있습니다. JSX는 확장된 문법이고, React는 JavaScript 라이브러리입니다.

</aside>

*JSX* JavaScript를 확장한 문법

JavaScript 파일을 HTML과 비슷하게 마크업을 작성할 수 있도록 해줌

대부분의 React 개발자는 JSX의 간결함을 선호 → 대부분의 코드 베이스에서 JSX를 사용

### JSX: JavaScript에 마크업 넣기

- Web은 HTML, CSS, JavaScript를 기반으로 만들어져 옴
- HTML로 내용을, CSS로 디자인을, JavaScript로 로직을 작성
- 보통은 HTML, CSS, JavaScript를 분리된 파일로 관리
- 그러나 Web이 더욱 인터랙티브 해지면서 로직이 내용을 결정하는 경우가 많아짐
- → JavaScript가 HTML을 담당하게 됨
- ⇒ **React에서 렌더링 로직과 마크업이 같은 위치에 함께 있게 된 이유**

- 각 React 컴포넌트는 React가 브라우저에 마크업을 렌더링할 수 있는 JavaScript 함수
- React 컴포넌트는 JSX라는 확장된 문법을 사용하여 마크업을 나타냅니다.
- JSX는 HTML과 비슷해 보이지만, 조금 더 엄격하며 동적으로 정보를 표시할 수 있습니다.


### **HTML을 JSX로 변환하기**

<aside>
💡 대부분의 경우 React의 화면 오류 메시지는 문제가 있는 곳을 찾는 데 도움이 됩니다.
</aside>

HTML

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

컴포넌트로 만들어보자

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

**동작하지 X** → JSX는 HTML보다 더 엄격하고 몇 가지 규칙이 더 있기 때문

### **JSX의 규칙**

1. **하나의 루트 엘리먼트로 반환하기**

- 한 컴포넌트에서 여러 엘리먼트를 반환하려면, **하나의 부모 태그로 감싸주세요.**
- 마크업에 `<div>`를 추가하고 싶지 않다면, `<>`와 `</>`로 대체할 수 있습니다.
- 빈 태그를 [Fragment](https://ko.react.dev/reference/react/Fragment)라고 함 - Fragments는 브라우저상의 HTML 트리 구조에서 흔적을 남기지 않고 그룹화해 줌

ex) 

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

> **왜 여러 JSX 태그를 하나로 감싸줘야 할까요?**
JSX는 HTML처럼 보이지만 **내부적으로는 일반 JavaScript 객체로 변**환됩니다. 하나의 배열로 감싸지 않은 하나의 함수에서는 두 개의 객체를 반환할 수 없습니다. 따라서 또 다른 태그나 Fragment로 감싸지 않으면 두 개의 JSX 태그를 반환할 수 없습니다.
> 

1. **모든 태그는 닫아주기**

JSX에서는 태그를 명시적으로 닫아야 함

1. **거의 대부분은 캐멀 케이스로!**

<aside>
💡 역사적인 이유로, `aria-*`와 `data-*`의 어트리뷰트는 HTML에서와 동일하게 대시를 사용하여 작성합니다.

</aside>

JSX는 JavaScript로 바뀌고 JSX에서 작성된 어트리뷰트는 JavaScript 객체의 키가 됨

컴포넌트에서는 종종 어트리뷰트를 변수로 읽고 싶은 경우가 있음

But! 그러나 JavaScript는 변수명에 제한이 있음

⇒ React에서 HTML과 SVG의 어트리뷰트 대부분이 캐멀 케이스로 작성

> `class`는 예약어이기 때문에, React에서는 [DOM의 프로퍼티](https://developer.mozilla.org/en-US/docs/Web/API/Element/className)의 이름을 따서 `className`으로 대신 작성
> 

### **추천-팁: JSX 변환기 사용하기**

[변환기](https://transform.tools/html-to-jsx)를 사용하여 기존 HTML과 SVG를 JSX로 변환하는 것을 추천합니다

### **요약**

- React 컴포넌트는 서로 관련이 있는 마크업과 렌더링 로직을 함께 그룹화함
- JSX는 HTML과 비슷하지만 몇가지 차이점이 있음 (필요 시, 변환기를 사용할 수 있음)
- 오류 메시지는 종종 마크업을 수정할 수 있도록 올바른 방향을 알려줌

### **챌린지 도전하기**

**챌린지 1 of 1:HTML을 JSX로 변환해보기**

다음은 컴포넌트에 HTML을 붙여 넣었지만, 올바른 JSX가 아닙니다. 수정해 보세요.

before

```jsx
export default function Bio() {
  return (
    <div class="intro">
      <h1>Welcome to my website!</h1>
    </div>
    <p class="summary">
      You can find my thoughts here.
      <br><br>
      <b>And <i>pictures</b></i> of scientists!
    </p>
  );
}
```

After

```jsx
export default function Bio() {
  return (
    <div>
      <div className="intro">
        <h1>Welcome to my website!</h1>
      </div>
      <p className="summary">
        You can find my thoughts here.
        <br /><br />
        <b>And <i>pictures</i></b> of scientists!
      </p>
    </div>
  );
}
```

## JSX에서 중괄호를 이용하여 JavaScript 사용하기


JSX를 사용하면 JavaScript 파일에 HTML과 비슷한 마크업을 작성하여 렌더링 로직과 콘텐츠를 같은 곳에 놓을 수 있음

JavaScript 로직을 추가하거나 해당 마크업 내부의 동적인 프로퍼티를 참조하고 싶음 → **JSX에서 중괄호를 사용하여 JavaScript를 사용할 수 있음**

### **따음표로 문자열 전달하기**

문자열 어트리뷰트를 JSX에 전달하려면 작은따옴표나 큰따옴표로 묶어야 합니다.

그러나 `src` 또는 `alt`를 동적으로 지정하려면 어떻게 해야 할까요? 

⇒ **`"`와`"`를 `{`와`}`로 바꿔 JavaScript의 값을 사용할 수 있습니다**.

**중괄호를 사용하면 마크업에서 바로 JavaScript를 사용할 수 있음**

### ****중괄호 사용하기: JavaScript 세계로 연결하는 창****

JSX는 JavaScript를 작성하기 위하여 중괄호 `{ }` 사이에서 JavaScript를 사용할 수 있음

중괄호를 사용하는 곳

JSX 안에서 중괄호는 두 가지 방법으로 사용할 수 있음

1. JSX 태그 안의 **문자:** <h1>{name}'s To Do List</h1>
2. = 바로 뒤에 오는 **어트리뷰트:** src={avatar}

### ****“이중 중괄호” 사용하기: JSX의 CSS와 다른 객체****

<aside>
💡 인라인 `style` 프로퍼티는 캐멀 케이스로 작성됩니다. 예를 들어 HTML에서의 `<ul style="background-color: black">`은 컴포넌트에서 `<ul style={{ backgroundColor: 'black' }}>`로 작성됩니다.

</aside>

<aside>
💡 JSX에서 `{{` 와 `}}` 를 본다면 JSX 중괄호 안의 객체에 불과하다는 것을 알아야 함!

</aside>

JSX에는 문자열, 숫자 및 기타 JavaScript 표현식뿐만 아니라 객체를 전달할 수도 있음

객체는 `{ name: "Hedy Lamarr", inventions: 5 }`처럼 중괄호로 표시됨

⇒ 따라서 JSX에서 객체를 전달하려면 `person={{ name: "Hedy Lamarr", inventions: 5 }}`와 같이 다른 중괄호 쌍으로 객체를 감싸야 함.

### ****JavaScript 객체와 중괄호에 대해서 더 알아보기****

여러 표현식을 하나의 객체로 옮기고 중괄호 안의 JSX에서 참조할 수 있음

JSX는 JavaScript를 사용하여 데이터와 논리를 구성할 수 있는 매우 작은 템플릿 언어

### **요약**

- 따음표 안의 JSX 어트리뷰트는 문자열로 전달됨
- 중괄호를 사용하면 JavaScript 논리와 변수를 마크업으로 가져올 수 있음
- JSX 태그 재부 또는 어트리뷰트의 = 뒤에서 작동함
- {{ 및 }} 는 특별한 문법이 아니다 → JSX 중괄호 안에 들어 있는 JavaScript 객체임

## 컴포넌트에 Props 전달하기

React 컴포넌트는 props를 이용해 서로 통신

모든 부모 컴포넌트는 props를 줌으로써 몇몇의 정보를 자식 컴포넌트에게 전달할 수 있음

props는 객체, 배열, 함수를 포함한 모든 JavaScript 값을 전달할 수 있음


### **친숙한 props**

props는 JSX 태그에 전달하는 정보

`<img>` 태그에 전달할 수 있는 props는 미리 정의되어 있습니다. (ReactDOM은 [HTML 표준](https://www.w3.org/TR/html52/semantics-embedded-content.html#the-img-element)을 준수합니다.)


### **컴포넌트에 props 전달하기**

두 단계에 걸쳐 `Avatar`에 props를 전달할 수 있음

**1단계: 자식 컴포넌트에 props 전달하기**

<aside>
💡 `person=` 뒤에 있는 이중 괄호가 혼란스럽다면, JSX 중괄호 안의 객체라고 기억!

</aside>

`Avatar`에 몇몇 props를 전달합니다. 예를 들어 `person` (객체)와 `size` (숫자)를 전달해 보겠습니다.

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

이제 `Avatar` 컴포넌트 내 props를 읽을 수 있음

**2단계: 자식 컴포넌트 내부에서 props 읽기**

이러한 props는 `function Avatar` 바로 뒤에 있는 `({`와 `})` 안에 그들의 이름인 `person, size` 등을 쉼표로 구분함으로써 읽을 수 있음

⇒ `Avatar` 코드 내에서 변수를 사용하는 것처럼 사용할 수 있음

```jsx
function Avatar({ person, size }) {
  // person과 size는 이곳에서 사용가능합니다.
}
```

`Avatar`에 렌더링을 위해 `person` 과 `size` props를 사용하는 로직을 추가하면 완료

⇒ `Avatar`를 다른 props를 이용해 다양한 방식으로 렌더링하도록 구성할 수 있음

props는 조절할 수 있는 손잡이, props는 함수의 인수와 동일한 역할

**React 컴포넌트 함수는 하나의 인자, 즉 `props` 객체를 받습니다.**

전체 props 자체를 필요로 하지는 않기에, 개별 props로 구조 분해 할당함

<aside>
💡 props를 선언할 때 `(` 및 `)` 안에  `{` 및 `}` 쌍을 놓치지 마세요

</aside>


### ****prop의 기본값 지정하기****

- 값이 지정되지 않았을 때, prop에 기본값을 주길 원한다면, 변수 바로 뒤에 `=` 과 함께 기본값을 넣어 구조 분해 할당을 해줄 수 있음
- 이 [기본값](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/Default_parameters)은 size prop이 없거나 `size={undefined}`로 전달될 때 사용됨
- but `size={null}`  또는 `size={0}`으로 전달된다면, 기본값은 사용되지 **않습니다**.


### ****JSX spread 문법으로 props 전달하기****

<aside>
💡 spread 문법은 제한적으로 사용하세요.

</aside>

- 때때로 전달되는 props는 반복적
- 일부 컴포넌트는 그들의 모든 props를 자식 컴포넌트에 전달
- → props를 직접 사용하지 않기 때문에 보다 간결한 “spread” 문법을 사용하는 것이 합리적

```jsx
function Profile(props) {
  return (
    <div className="card">
      <Avatar {...props} />
    </div>
  );
}
```

모든 props를 각각의 이름을 나열하지 않고 `Avatar`로 전달

### ****자식을 JSX로 전달****

- 내장된 브라우저 태그는 중첩하는 것이 일반적
- but 때로는 같은 방식으로 자체 컴포넌트를 중첩하고 싶을 때가 있음

```jsx
<Card>
  <Avatar />
</Card>
```

- JSX 태그 내에 콘텐츠를 중첩하면, 부모 컴포넌트는 해당 콘텐츠를 `children`이라는 prop으로 받을 것임
- `children` prop을 가지고 있는 컴포넌트는 부모 컴포넌트가 임의의 JSX로 “채울” 수 있는 “구멍”이 있는 것으로 생각할 수 있음

### 시간에 따라 props가 변하는 방식

<aside>
💡 “props 변경”을 시도하지 마세요.

</aside>

`Clock` 컴포넌트는 부모 컴포넌트로부터 `color`와 `time`이라는 두 가지 props를 받습니다. (부모 컴포넌트의 코드는 아직 자세히 다루지 않을 [state](https://ko.react.dev/learn/state-a-components-memory)를 사용하기 때문에 생략합니다.)

**컴포넌트가 시간에 따라 다른 props를 받을 수 있음을 보여줍니다.**

Props는 컴포넌트의 데이터를 처음에만 반영하는 것이 아니라 모든 시점에 반영합니다.

컴포넌트가 props를 변경해야 하는 경우, 부모 컴포넌트에 *다른 props*, 즉 새로운 객체를 전달하도록 “요청”해야 합니다! 그러면 이전의 props는 버려지고, 결국 자바스크립트 엔진은 기존 props가 차지했던 메모리를 회수하게 됩니다.

사용자 입력에 반응해야 하는 경우 - [State: 컴포넌트의 메모리](https://ko.react.dev/learn/state-a-components-memory)에서 배울 “set state”가 필요할 것


### **요약**

- **Props를 전달**하려면 HTML 어트리뷰트를 사용할 때와 마찬가지로 **JSX에 props를 추가**합니다.
- **Props를 읽으려면 `function Avatar({ person, size })` 구조 분해 할당 문법을 사용**합니다.
- `size = 100` 과 같은 **기본값을 지정할 수 있으며**, 이는 누락되거나 `undefined` 인 props에 사용됩니다.
- **모든 props를 `<Avatar {...props} />`로 전달할 수 있습니다.** JSX spread 문법을 사용할 수 있지만 과도하게 사용하지 마세요!
- `<Card><Avatar /></Card>`와 같이 **중첩된 JSX는 `Card`컴포넌트의 자식 컴포넌트로 나타납니다.**
- **Props는 읽기 전용 스냅샷**으로, **렌더링 할 때마다 새로운 버전의 props를 받습니다.**
- **Props는 변경할 수 없습니다**. **상호작용이 필요한 경우 state를 설정**해야 합니다.


## 조건부 렌더링

컴포넌트는 조건에 따라 다른 항목을 표시해야 하는 경우가 많음

리액트는 `if` 문, `&&` 및 `? :` 연산자와 같은 자바스크립트 문법을 사용하여 조건부로 JSX를 렌더링할 수 있음


### ****조건부로 JSX 반환하기****

- JavaScript의 `if`와 `return` 문으로 분기 로직을 만드는 방법을 살펴보세요.
- React에서 제어 흐름(예: 조건문)은 JavaScript로 처리합니다.


### ****조건부로 `null`을 사용하여 아무것도 반환하지 않기**

- 어떤 경우에는 아무것도 렌더링하고 싶지 않을 수 있음
- 컴포넌트는 반드시 무언가를 반환해야 하는데 이 경우에 `null`을 반환할 수 있음


### ****조건부로 JSX 포함시키기****

- 이전 예제에서는 어떤 항목(있는 경우)을 제어함
- 컴포넌트에 의해 JSX 트리가 반환되었는데 렌더링 된 출력 결과에서 이미 일부 중복이 발견됨 (두 조건부 분기가 모두 `<li className="item">...</li>`를 반환)
- → 이러한 상황에서 조건부로 약간의 JSX를 포함해 코드를 더 [DRY(덜 반복적이게)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) 하게 만들 수 있습니다.


### ****삼항 조건 연산자 (`? :`)**

JavaScript는 [조건 연산자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Conditional_Operator) 또는 “삼항 조건 연산자”라는 조건식을 작성하기 위한 간단한 문법이 있음

```jsx
return (
  <li className="item">
    {isPacked ? name + ' ✔' : name}
  </li>
);
```

중첩된 조건부 마크업이 너무 많아 컴포넌트가 지저분해질 경우 자식 컴포넌트를 추출하여 정리해라


### ****논리 AND 연산자 (`&&`)**

[JavaScript 논리 AND (’&&’) 연산자](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND#:~:text=The%20logical%20AND%20(%20%26%26%20)%20operator,it%20returns%20a%20Boolean%20value.) 사용

React 컴포넌트에서는 조건이 참일 때 일부 JSX를 렌더링하거나 **그렇지 않으면 아무것도 렌더링하지 않을 때** 를 나타내는 경우가 많음 

⇒ `&&`를 사용하면 `isPacked`가 `true`인 경우에만 조건부로 체크 표시를 렌더링할 수 있음


### ****변수에 조건부로 JSX를 할당하기****

`if` 문과 변수를 사용, `[let](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/let)`으로 정의된 변수는 재할당할 수 있으므로 표시할 기본 내용인 이름을 먼저 대입


### ****요약****

- **React에서 JavaScript로 분기 로직을 제어**합니다.
- **조건부로 `if` 문과 함께 JSX 식을 반환**할 수 있습니다.
- 조건부로 일부 JSX를 변수에 저장한 다음 중괄호를 사용하여 다른 JSX에 포함할 수 있습니다.
- JSX에서 `{cond ? <A /> : <B />}`는 *“`cond`이면 `<A />`를 렌더링하고, 그렇지 않으면 `<B />`를 렌더링합니다.”* 를 의미합니다.
- JSX에서 `{cond && <A />}`는 *“`cond`이면, `<A />`를 렌더링하되, 그렇지 않으면 아무것도 렌더링하지 않습니다.”* 를 의미합니다.
- 위 예시는 흔한 방법이지만, `if`를 선호한다면 사용하지 않아도 됩니다.


## 리스트 렌더링

데이터 모음에서 유사한 컴포넌트를 여러 개 표시하고 싶을 때 [JavaScript 배열 메서드](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array#)를 사용하여 데이터 배열을 조작할 수 있음

React에서 `filter()`와 `map()`을 사용해 데이터 배열을 필터링하고 컴포넌트 배열로 변환해보자


### ****배열을 데이터로 렌더링하기****

리스트 항목의 유일한 차이점이 콘텐츠(데이터) 일 때, 해당 데이터를 JavaScript 객체와 배열에 저장하고 `map()`과 `filter()` 같은 메서드를 사용하여 해당 객체에서 컴포넌트 리스트를 렌더링할 수 있음.

배열에서 항목 리스트를 생성하는 방법 예시

1. 데이터를 배열로 이동함

```jsx
const people = [
  'Creola Katherine Johnson: mathematician',
  'Mario José Molina-Pasquel Henríquez: chemist',
  'Mohammad Abdus Salam: physicist',
  'Percy Lavon Julian: chemist',
  'Subrahmanyan Chandrasekhar: astrophysicist'
];
```

2. `people`의 요소를 새로운 JSX 노드 배열인 `listItems`에 **매핑**합니다.

```jsx
const listItems = people.map(person => <li>{person}</li>);
```

3. `<ul>`로 래핑된 컴포넌트의 `listItems`를 **반환**합니다.

```jsx
return <ul>{listItems}</ul>;
```


### ****배열의 항목들을 필터링하기****

<aside>
💡 화살표 함수는 암시적으로 `=>` 바로 뒤에 식을 반환하기 때문에 `return` 문이 필요하지 않습니다. 하지만 `=>` 뒤에 `{` 중괄호가 오는 경우 `return`을 명시적으로 작성해야 합니다!

</aside>

JavaScript의 `filter()` 메서드를 사용하여 해당하는 사람만 반환할 수 있음

`filter()` 메서드는 항목 배열을 받아 “test”(`true` 혹은 `false`를 반환하는 함수)를 통과한 후 테스트에 통과된 항목(`true`가 반환된 항목)만 있는 새로운 배열을 반환함

ex) 

`people`에서 `filter()`를 호출해 `person.profession === 'chemist'`로 필터링해서 “chemist”로만 구성된 새로운 배열 `chemists`를 **생성**

```jsx
const chemists = people.filter(person =>
  person.profession === 'chemist'
);
```


### ****`key`를 사용해서 리스트 항목을 순서대로 유지하기**

<aside>
💡 `map()` 호출 내부의 JSX 엘리먼트에는 항상 key가 필요함!

</aside>

각 배열 항목에 다른 항목 중에서 **고유하게 식별할 수 있는 문자열 또는 숫자를 `key`로 지정**해야 함


### ****`key`를 가져오는 곳**

데이터 소스마다 다른 key 소스를 제공함

- **데이터베이스의 데이터:** 데이터베이스에서 데이터를 가져오는 경우 본질적으로 고유한 데이터베이스 key/ID를 사용할 수 있음
- **로컬에서 생성된 데이터:** 데이터가 로컬에서 생성되고 유지되는 경우, 항목을 만들 때 증분 일련번호나 `crypto.randomUUID()` 또는 `uuid` 같은 패키지를 사용함


### ****key 규칙****

- **key는 형제 간에 고유해야 함 -** 하지만 같은 key를 *다른* 배열의 JSX 노드에 동일한 key를 사용해도 됨
- **key는 변경되어서는 안 됨 -** 그렇게 되면 key는 목적에 어긋납니다! 렌더링 중에는 key를 생성하지 마세요.


### ****React에 key가 왜 필요한 이유는 무엇인가요?****

<aside>
💡 배열에서 항목의 인덱스를 key로 사용하고 싶을 수도 있습니다. 실제로 `key`를 전혀 지정하지 않으면 React는 인덱스를 사용합니다. 하지만 항목이 삽입되거나 삭제하거나 배열의 순서가 바뀌면 시간이 지남에 따라 항목을 렌더링하는 순서가 변경됩니다.
</aside>

- 형제 항목 간에 항목을 고유하게 식별할 수 있음
- 잘 선택된 key는 배열 내 위치보다 더 많은 정보를 제공함
- 재정렬로 인해 _위치_가 변경되더라도 `key`는 React가 생명주기 내내 해당 항목을 식별할 수 있게 해줌


### ****요약****

- 컴포넌트에서 배열이나 객체와 같은 데이터 구조로 데이터를 이동하는 방법
- JavaScript의 `map()`을 사용하여 유사한 컴포넌트 집합을 생성하는 방법
- JavaScript의 `filter()`를 사용하여 필터링된 항목의 배열을 생성하는 방법
- 컬렉션에서 각 컴포넌트에 `key`를 설정하여 위치나 데이터가 변경되더라도 React가 각 컴포넌트를 추적할 수 있도록 하는 이유와 방법


## 컴포넌트 순수하게 유지하기

- 자바스크립트 일부 함수는 *순수함*
- 순수 함수는 오직 연산만을 수행함
- 컴포넌트를 엄격하게 순수 함수로 작성하면 코드 베이스가 점점 커지더라도 버그를 피할 수 있음


### ****순수성: 공식으로서의 컴포넌트****

컴퓨터 과학에서(특히 함수형 프로그래밍의 세계에서는) [순수 함수](https://wikipedia.org/wiki/Pure_function)는 다음과 같은 특징을 지니고 있는 함수

- **자신의 일에 집중함.** 함수가 호출되기 전에 존재했던 어떤 객체나 변수는 변경하지 않음
- **같은 입력, 같은 출력** 같은 입력이 주어졌다면 순수함수는 같은 결과를 반환해야 함

**React는 작성되는 모든 컴포넌트가 순수 함수일 거라 가정합니다.** 이러한 가정은 작성되는 React 컴포넌트가 같은 입력이 주어진다면 반드시 같은 JSX를 반환한다는 것을 의미합니다.


### ****사이드 이펙트: 의도하지(않은) 결과****

<aside>
💡 순수 함수는 연산만 하므로 두 번 호출해도 아무 것도 변경되지 않습니다. 항상 같은 입력이면 같은 출력입니다.
</aside>

- React의 렌더링 과정은 항상 순수해야 함.
- 컴포넌트는 렌더링하기 전에 존재했던 객체나 변수들을 *변경*하지 말고 컴포넌트를 순수하지 않도록하는 JSX만 *반환*해야 함
- ⇒ `[guest` 변수를 대신 프로퍼티로 넘겨](https://ko.react.dev/learn/passing-props-to-a-component) 이 컴포넌트를 고칠 수 있음

> ****엄격 모드로 순수하지 않은 연산을 감지****
React에는 렌더링하면서 읽을 수 있는 세 가지 종류의 입력 요소(props, state, context)가 있으며 이러한 입력 요소는 항상 읽기 전용으로 취급해야 함.
사용자의 입력에 따라 무언가를 *변경* 하려는 경우, 변수를 직접 수정하는 대신 [set state](https://ko.react.dev/learn/state-a-components-memory)를 활용해야 합니다. 컴포넌트가 렌더링되는 동안엔 기존 변수나 개체를 변경하면 안됩니다.
React는 개발 중에 각 컴포넌트의 함수를 두 번 호출하는 “엄격 모드”를 제공합니다. **컴포넌트 함수를 두 번 호출함으로써, 엄격 모드는 이러한 규칙을 위반하는 컴포넌트를 찾는데 도움을 줍니다.**
> 


### 지역 변형: 컴포넌트의 작은 비밀

- 예시에서 문제는 렌더링하는 동안 컴포넌트가 기존 변수를 변경했다는 것 ⇒ **변형**
- 순수 함수는 함수 스코프 밖의 변수나 호출 전에 생성된 객체를 변경하지 않음
- But **렌더링하는 동안 *그냥* 만든 변수와 객체를 변경하는 것은 전혀 문제가 없음!**
- **“지역 변형”**


### 부작용을 일으킬 수 있는 지점

- 함수형 프로그래밍은 순수성에 크게 의존하지만, 언젠가는, 어딘가에서, *무언가가* 바뀌어야 함
- 이러한 변화들-화면을 업데이트하고, 애니메이션을 시작하고, 데이터를 변경하는 것을 **사이드 이펙트**라고 함
- 렌더링중에 발생하는 것이 아니라 *“사이드에서,”* 발생하는 현상
- 리액트에선, **사이드 이펙트는 보통 [이벤트 핸들러](https://ko.react.dev/learn/responding-to-events)에 포함됨**
- 이벤트 핸들러는 리액트가 일부 작업을 수행할 때 반응하는 기능
- **이벤트 핸들러는 순수할 필요가 없습니다.**
- 다른 옵션을 모두 사용했지만 사이드 이펙트에 적합한 이벤트 핸들러를 찾을 수 없는 경우에도, 컴포넌트에서 `useEffect` 호출을 사용하여 반환된 JSX에 해당 이벤트 핸들러를 연결할 수 있음
- But **이 접근 방식이 마지막 수단이 되어야 합니다.**
- 가능하면 렌더링만으로 로직을 표현

> ****리액트는 왜 순수함을 신경쓸까요?****
우리가 구축하고 있는 모든 새로운 리액트 기능은 순수성을 활용함
컴포넌트는 다른 환경에서도 실행될 수 있음 (동일한 입력에 대해 동일한 결과를 반환하기 때문에 하나의 컴포넌트는 많은 사용자 요청을 처리할 수 있음)
입력이 변경되지 않은 컴포넌트 [렌더링을 건너뛰어](https://ko.react.dev/reference/react/memo) 성능을 향상시킬 수 있음 (순수 함수는 항상 동일한 결과를 반환하므로 캐시하기에 안전함)
순수함은 언제든지 연산을 중단하는 것을 안전하게 함
> 


### 요약

- 컴포넌트는 순수해야 함
- 렌더링은 언제든지 발생할 수 있으므로 컴포넌트는 서로의 렝더링 순서에 의존하지 않아야 함
- 컴포넌트가 렌더링을 위해 사용되는 입력을 변형해서는 안 됨. (여기에는 프로퍼티즈, 상태, 그리고 컨텍스트가 포함) 화면을 업데이트하려면 기존 객체를 변환하는 대신 [상태를 “설정”](https://ko.react.dev/learn/state-a-components-memory)해라
- 반환하는 JSX에서 컴포넌트의 로직을 표현하기 위해 노력하십시오. “무언가를 변경”해야 할 경우 일반적으로 이벤트 핸들러에서 변경하고 싶을 것입니다. 마지막 수단으로 `useEffect`를 사용할 수 있음
- 순수 함수를 작성하는 것은 약간의 연습이 필요하지만, React 패러다임의 힘을 풀어줌


## 전체 내용 요약

**첫 번째 컴포넌트**

- React를 사용하면 앱의 **재사용 가능한 UI 요소인 컴포넌트**를 만들 수 있다!
- React 앱에서 모든 UI는 컴포넌트이다!
- React 컴포넌트는 다음 몇 가지를 제외하고는 일반적인 JavaScript 함수이다!
    - 컴포넌트의 이름은 항상 대문자로 시작한다!
    - JSX 마크업을 반환한다!

****컴포넌트 import 및 export 하기****

- Root 컴포넌트란 무엇인지
- 컴포넌트를 import 하거나 export 하는 방법
- 언제 default 또는 named imports와 exports를 사용할지
- 한 파일에서 여러 컴포넌트를 export 하는 방법
    - 한 파일에서는 단 하나의 default export만 사용할 수 있지만 named export는 여러 번 사용할 수 있음

****JSX로 마크업 작성하기****

- React 컴포넌트는 서로 관련이 있는 마크업과 렌더링 로직을 함께 그룹화함
- JSX는 HTML과 비슷하지만 몇가지 차이점이 있음 (필요 시, 변환기를 사용할 수 있음)
- 오류 메시지는 종종 마크업을 수정할 수 있도록 올바른 방향을 알려줌

****중괄호가 있는 JSX 안에서 자바스크립트 사용하기****

- 따음표 안의 JSX 어트리뷰트는 문자열로 전달됨
- 중괄호를 사용하면 JavaScript 논리와 변수를 마크업으로 가져올 수 있음
- JSX 태그 재부 또는 어트리뷰트의 = 뒤에서 작동함
- {{ 및 }} 는 특별한 문법이 아니다 → JSX 중괄호 안에 들어 있는 JavaScript 객체임

****컴포넌트에 props 전달하기****

- **Props를 전달**하려면 HTML 어트리뷰트를 사용할 때와 마찬가지로 **JSX에 props를 추가**합니다.
- **Props를 읽으려면 `function Avatar({ person, size })` 구조 분해 할당 문법을 사용**합니다.
- `size = 100` 과 같은 **기본값을 지정할 수 있으며**, 이는 누락되거나 `undefined` 인 props에 사용됩니다.
- **모든 props를 `<Avatar {...props} />`로 전달할 수 있습니다.** JSX spread 문법을 사용할 수 있지만 과도하게 사용하지 마세요!
- `<Card><Avatar /></Card>`와 같이 **중첩된 JSX는 `Card`컴포넌트의 자식 컴포넌트로 나타납니다.**
- **Props는 읽기 전용 스냅샷**으로, **렌더링 할 때마다 새로운 버전의 props를 받습니다.**
- **Props는 변경할 수 없습니다**. **상호작용이 필요한 경우 state를 설정**해야 합니다.

****조건부 렌더링****

- React에서 JavaScript로 분기 로직을 제어합니다.
- 조건부로 `if` 문과 함께 JSX 식을 반환할 수 있습니다.
- 조건부로 일부 JSX를 변수에 저장한 다음 중괄호를 사용하여 다른 JSX에 포함할 수 있습니다.
- JSX에서 `{cond ? <A /> : <B />}`는 *“`cond`이면 `<A />`를 렌더링하고, 그렇지 않으면 `<B />`를 렌더링합니다.”* 를 의미합니다.
- JSX에서 `{cond && <A />}`는 *“`cond`이면, `<A />`를 렌더링하되, 그렇지 않으면 아무것도 렌더링하지 않습니다.”* 를 의미합니다.
- 위 예시는 흔한 방법이지만, `if`를 선호한다면 사용하지 않아도 됩니다.

****리스트 렌더링****

- 컴포넌트에서 배열이나 객체와 같은 데이터 구조로 데이터를 이동하는 방법
- JavaScript의 `map()`을 사용하여 유사한 컴포넌트 집합을 생성하는 방법
- JavaScript의 `filter()`를 사용하여 필터링된 항목의 배열을 생성하는 방법
- 컬렉션에서 각 컴포넌트에 `key`를 설정하여 위치나 데이터가 변경되더라도 React가 각 컴포넌트를 추적할 수 있도록 하는 이유와 방법

****컴포넌트 순수하게 유지하기****

- 컴포넌트는 순수해야 함
- 렌더링은 언제든지 발생할 수 있으므로 컴포넌트는 서로의 렝더링 순서에 의존하지 않아야 함
- 컴포넌트가 렌더링을 위해 사용되는 입력을 변형해서는 안 됨. (여기에는 프로퍼티즈, 상태, 그리고 컨텍스트가 포함) 화면을 업데이트하려면 기존 객체를 변환하는 대신 [상태를 “설정”](https://ko.react.dev/learn/state-a-components-memory)해라
- 반환하는 JSX에서 컴포넌트의 로직을 표현하기 위해 노력하십시오. “무언가를 변경”해야 할 경우 일반적으로 이벤트 핸들러에서 변경하고 싶을 것입니다. 마지막 수단으로 `useEffect`를 사용할 수 있음
- 순수 함수를 작성하는 것은 약간의 연습이 필요하지만, React 패러다임의 힘을 풀어줌


## Q & A

> **React에서 "props", "state", 및 "context"란 무엇인가요? 각각의 역할과 차이점은 무엇인가요?**
>

- React에서 컴포넌트가 렌더링하면서 읽을 수 있는 세 가지 종류의 입력 요소는 **`props`**, **`state`**, 그리고 **`context`**입니다.
1. **Props (Properties)**:
- **역할**: **`props`**는 컴포넌트의 속성(특성)을 나타냅니다. 부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달하는 데 사용됩니다.
- **읽기 전용**: **`props`**은 읽기 전용이며 컴포넌트 내에서 변경할 수 없습니다.

```jsx
function Greeting(props) {
  return <div>Hello, {props.name}!</div>;
}
```

2. **State**:
- **역할**: **`state`**는 컴포넌트 내에서 관리되는 로컬 상태를 나타냅니다. 이 상태가 변경될 때 컴포넌트가 리렌더링됩니다.
- **읽기 전용**: **`state`** 역시 읽기 전용이며 직접 수정하는 대신 **`setState`** 함수를 통해 변경합니다.

```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  }

  render() {
    return (
      <div>
        Count: {this.state.count}
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}
```

3. **Context**:
- **역할**: **`context`**는 컴포넌트 트리에서 전역 데이터를 공유하는 데 사용됩니다. 주로 어떤 컴포넌트에서 다른 컴포넌트로 데이터를 전달할 때 유용합니다.
- **읽기 전용**: **`context`** 또한 읽기 전용이며 변경하려면 해당 컴포넌트에서 값을 업데이트하고 해당 업데이트를 구독하는 컴포넌트에서 변경사항을 감지해야 합니다.

```jsx
const MyContext = React.createContext();

function App() {
  const sharedValue = "Shared Value";
  return (
    <MyContext.Provider value={sharedValue}>
      <ChildComponent />
    </MyContext.Provider>
  );
}

function ChildComponent() {
  return (
    <MyContext.Consumer>
      {value => <div>Shared Value: {value}</div>}
    </MyContext.Consumer>
  );
}
```

**공통점:**

- 모든 세 가지 요소는 컴포넌트 간 데이터 전달에 사용됩니다.
- 모든 요소는 읽기 전용으로 취급되며 직접 수정하면 안 됩니다.

**차이점:**

- `props`는 **데이터를 부모에서 자식으로 전달할 때 사용**하며 **컴포넌트 외부에서 제어**됩니다.
- `state`는 **컴포넌트의 로컬 상태를 관리**하며 **컴포넌트 내부에서 변경**됩니다.
- `context`는 **전역 데이터 공유**를 위해 사용되며 **컴포넌트 트리의 여러 레벨에서 데이터를 공유**할 수 있습니다.

> **React에서 "지역 변형(Local Mutation)"이 어떻게 작동하며, 어떤 상황에서 이것을 사용해야 할까요?**
> 
- React의 "지역 변형(Local Mutation)"은 컴포넌트 내에서 렌더링 중에만 생성된 변수나 객체를 변경하는 것을 의미합니다.
- 이것은 컴포넌트 내부에서만 영향을 미치며 컴포넌트 외부에는 전혀 영향을 미치지 않습니다.
- ⇒ 이로써 컴포넌트 내부의 데이터를 안전하게 조작할 수 있습니다.

```jsx
function TeaGathering() {
  // 지역적으로 배열을 생성
  const cups = [];

  // 렌더링 중에만 cups 배열을 조작
  cups.push("Tea Cup 1");
  cups.push("Tea Cup 2");

  return (
    <div>
      <h2>Tea Gathering</h2>
      <ul>
        {cups.map((cup, index) => (
          <li key={index}>{cup}</li>
        ))}
      </ul>
    </div>
  );
}
```

- 이 예시에서, **`cups` 배열은 컴포넌트 함수 내에서 지역적으로 생성되었고, 렌더링 중에만 수정**됩니다.
- 이렇게 **생성된 변수나 객체는 컴포넌트 외부에서는 보이지 않으며 다른 컴포넌트나 전역 상태에 영향을 미치지 않습니다**.
- 이것은 **React 컴포넌트의 작은 "비밀"처럼 작용**합니다.
- 만약 **`cups` 배열이 컴포넌트 외부에서 생성되었다면 다른 컴포넌트에서 `cups` 배열을 변경하거나 영향을 미칠 수 있었지만,** 이 예시에서는 그렇지 않습니다.
- 이렇게 하면 **컴포넌트 간 상호작용과 데이터의 격리를 지원하며 예측 가능한 동작을 유지**할 수 있게 됩니다.
- "지역 변형"은 React의 함수형 컴포넌트에서 흔하게 사용되며 **컴포넌트가 렌더링 중에만 필요한 데이터를 관리하는 데 매우 유용**합니다.

> **JSX에서 중괄호 `{ }`를 사용하는 이유는 무엇이고, 이것을 사용할 때 주의할 점은 무엇인가요?**
> 
- JSX에서 중괄호 **`{ }`**를 사용하면 JavaScript 코드를 마크업 안에서 사용할 수 있습니다.
- ⇒ 이를 통해 동적 데이터를 렌더링하거나 JavaScript 표현식을 마크업 어트리뷰트에 사용할 수 있습니다.

```jsx
function Greeting(props) {
  const name = "John";
  const age = 30;

  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>You are {age} years old.</p>
    </div>
  );
}
```

이 예시에서 `{name}`과 `{age}`는 중괄호를 사용하여 JavaScript 변수를 마크업 안에 삽입한 것입니다. 이를 통해 동적 데이터를 표시하거나 템플릿 내에서 JavaScript 로직을 실행할 수 있습니다.

