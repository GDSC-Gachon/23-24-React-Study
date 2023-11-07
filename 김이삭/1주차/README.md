# 리액트 공식문서 스터디 1주차 - UI 구성하기

- React 컴포넌트 만들기
- 사용자 정의하기
- 조건부 표시 방법 알아보기

## 첫번째 컴포넌트
- React를 사용하면 markup, CSS, JavaScipt를 앱의 **재사용 가능한 UI요소인 사용자 정의** `컴포넌트`로 결합할 수 있다.
- **React 컴포넌트: 마크업으로 뿌릴 수 있는 JavaScript**
- HTML태그와 같이 컴포넌트를 작성, 순서 지정 및 중첩해 전체 페이지를 디자인할 수 있다.
  
  ```jsx
  export default function Profile() {
  return (
    <img
      src="https://i.imgur.com/MK3eW3Am.jpg"
      alt="Katherine Johnson"
    />
   );
  }
### 컴포넌트를 빌드하는 방법
1. 컴포넌트 내보내기: `export default`를 사용하면 나중에 다른 파일에서 가져올 수 있도록 파일에 주요기능을 표시할 수 있다.
2. 함수 정의하기: `function Profile(){}`을 사용하면 `Profile`이라는 이름의 함수를 정의할 수 있다.
   - 컴포넌트의 이름은 대문자로 시작하는 것이 좋다!
3. 마크업 추가하기
   - 반환문은 한줄에 작성할 수 있다. 여러줄에 있을 경우 괄호`()`로 묶어야 한다.
   - 괄호가 없을 경우 `return` 뒤 라인에 있는 모든 코드가 무시된다!
### 컴포넌트 사용하기
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
- `Profile` 컴포넌트를 정의했으므로 여러 `Profile`을 사용하는 `Gallery` 컴포넌트를 내보낼 수 있다.
### React에서의 대소문자 차이
- 소문자로 시작할 경우: HIML 태그를 가르킨다고 이해
- 대문자로 시작할 경우: 컴포넌트를 사용하고자 한다고 이해 
### 컴포넌트 중첩 및 구성
- 같은 파일에 여러 컴포넌트 포함 가능 -> 복잡해지면 별도의 파일로 옮길 수 있음
- 위 코드의 경우 `Profile` 컴포넌트는 `Gallery`에 렌더링
  - *`Gallery`는 `Profile`을 자식으로 렌더링하는 부모 컴포넌트!*
- 하지만 컴포넌트 정의가 중첩될 경우 버그가 유발된다.
- 자식 컴포넌트에서 부모 컴포넌트의 데이터 일부가 필요한 경우 **props**로 전달하기

## 컴포넌트 import 및 export
- 컴포넌트의 가장 큰 장점: `재사용성`, 컴포넌트를 조합해 또 다른 컴포넌트를 만들 수 있다!
- 컴포넌트를 파일로 분리하면 더 쉽게 찾을 수 있고 재사용하기 편리해짐
### 루트 컴포넌트
- 컴포넌트는 `App.js`라는 **root 컴포넌트 파일**에 존재
### 컴포넌트 import 및 export
- 기능별 컴포넌트를 root컴포넌트 밖으로 옮기면 모듈성이 강화되고 다른 파일에서 재사용할 수 있게 된다.
- 컴포넌트를 이동하는 방법
  1. 컴포넌트를 넣을 JS파일 생성하기
  2. 새로 만든 파일에 컴포넌트 `export`하기
    - default or named export 방식 사용
  3. 컴포넌트를 사용할 파일에서 `import`하기
   - default or named export에 대응하는 방식으로 import
### 동일한 파일에서 여러 컴포넌트 import & export하기
- 하나의 파일에서 default export를 하나만 가질 수 있지만 named export는 여러 개 가질 수 있다.
```jsx
//Gallery.js
export function Profile() { 
  // named export 방식으로 Gallery.js에서 Profile를 export
  return (
    <img
      src="https://i.imgur.com/QIrZWGIs.jpg"
      alt="Alan L. Hart"
    />
  );
}
```

```jsx
// App.js
import Gallery form './Gallery.js';
import { Profile } from './Gallery.js';
// named import방식으로 Gallery.js에서 Profile를 App.js 파일로 import
export default function App() {
  return (
    <Profile />
  );
}
```
## JSX로 마크업 작성하기
- JSX는 JavaScript를 확장한 문법! JavaScript 파일 안에 HTML과 유사한 마크업 작성을 할 수 있게 한다.
### JSX: JavaScript에 마크업 넣기
- 웹은 보통 각각 분리된 파일로 관리, 페이지 로직이 JS에서 분리되어 작동하는 동안 HTML안에서는 콘텐츠가 마크업 된다.
- 웹이 인터랙티브해짐 -> 로직의 컨텐츠 결정 경우 증가 
- 리액트에서 **렌더링 로직과 마크업이 같은 위치의 컴포넌트에 함께 있는 이유**
  - 모든 편집에서 서로 동기화 상태를 유지할 수 있다.
- JSX는 HTML과 비슷해보이지만 더 엄격하며, 동적으로 정보를 표시한다.
  - HTML 마크업을 JSX 마크업으로 변환해보자!
- NOTE: 
  - JSX: 구문확장
  - React: JS 라이브러리
### HTML을 JSX로 변환하기
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
- 유효한 HTML 코드
- 하지만 .js파일로 저장하면 오류남
  - JSX는 HTML보다 엄격하고 규칙이 더 있기 때문!
- 대부분의 경우 React 화면 오류 메세지는 문제해결에 도움이 된다!
### JSX 규칙
1. 단일 루트 엘리먼트 반환하기
   - 하나의 `부모태그`로 감싸주기
   - ex) div 태그 사용하기
   - 또는 빈 태그도 가능(= Fragment: HTML트리구조에 흔적 남기지 않고 그룹화 해준다.)
2. 모든 태그 닫기
3. 대부분이 카멜 케이스!
   - 예약어는 사용할 수 없다.
   - 소문자로 시작해 합성어 시작은 대문자로 적기
- Tip: JSX 변환기를 사용하는 것도 추천!
## JSX에서 JavaScript 사용하기
- 마크업 내에 동적 프로퍼티 참조하고 싶을 때: JSX에서 중괄호 사용해 JS창으로 열 수 있다!
### 따옴표로 문자열 전달하기
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
- "https://i.imgur.com/7vQD0fPs.jpg" 및 "Gregorio Y. Zara"는 문자열로 전달됨
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
- src와 alt가 동적으로 지정됨
- `""`을 `{}`로 대체
### 중괄호 사용하기
- `{}`안에서 js사용할 수 있다.
```jsx
export default function TodoList() {
  const name = 'Gregorio Y. Zara';
  return (
    <h1>{name}'s To Do List</h1>
  );
}
```
### 중괄호 사용위치
1. JSX 태그안에 직접 텍스트로 사용
2. `=`기호 바로 뒤에 오는 속성
### "이중 중괄호 사용: JSX 내에서의 CSS 및 다른 객체
- JSX내에서 JS객체를 전달하려면 `다른 중괄호쌍`으로 객체를 감싸야 한다.
- JSX에서 `{{`와 `}}` 볼 때 JSX 중괄호 내부의 객체일 뿐이라는 점 기억하기!, 특별한 구문 아님
## 컴포넌트에 props 전달하기
- React 컴포넌트는 props를 이용해 서로 통신
- **props: JSX 태그에 전달하는 정보**, properties의 줄임말
- 부모 컴포넌트는 props를 줌으로써 자식 컴포넌트에게 일부 정보를 전달할 수 있음
- 객체, 배열, 함수 포함한 모든 JS값 전달 가능
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
- className, src, alt, width, height 는 <img> 태그에 전달할 수 있다.
### 컴포넌트에 props 전달하기 
1. 자식 컴포넌트에 props 전달하기
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
- 이제 `Avatar` 컴포넌트 내 props를 읽을 수 있게 됨.
2. 자식 컴포넌트 내부에서 props 읽기
```jsx
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
```
- `props`를 사용하면 부모와 자식 컴포넌트를 독립적으로 생각할 수 있다.
- props는 `함수의 인수와 동일한 역할`을 한다.
  - 컴포넌트에 대한 유일한 인자!, React 컴포넌트 함수는 하나의 인자 -props 객체를 받는다.
- 보통은 전체 props를 필요로 하진 않아 개별 props로 구조분해한다.
### 구조 분해 할당
: props를 선언할 때 `()`안에 `{}`쌍을 넣는 것
```jsx
function Avatar(props) {
  let person = props.person;
  let size = props.size;
  // ...
}
``` 
### props의 기본값 지정하기
- 값이 지정되지 않았을 때 기본값을 주길 원한다면 변수 바로 뒤에 `=`와 `기본값`을 넣어 `구조 분해 할당`을 해줄 수 있다.
```jsx
function Avatar({ person, size = 100 }) {
  // ...
}
```
- size가 prop없이 렌더링되면 기본값 100으로 설정된다.
  - 기본값은 `size prop이 없거나 size={undefined} 로 전달될 때` 사용!
### JSX 전개구문으로 props 전달하기
- 반복적인 props의 간결함을 높이기 위해 전개구문을 사용한다.
- 전개 구문은 `제한적으로 사용할 것!`
  - 모든 컴포넌트에 전개구문이 사용되는 것은 문제가 있다.. 컴포넌트를 분할해 `자식을 JSX로 전달할 것.`

### 자식을 JSX로 전달하기
### 시간에 따라 props가 변하는 방식 
## 조건부 렌더링
## 목록 렌더링
## 컴포넌트 순수성 유지
