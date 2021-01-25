```
리액트를 다루는 기술 정리
```
# 2. JSX

## 2.1 코드 이해하기
```jsx
import React from 'react';
```

* node_modules 디렉토리에 있는 react 모듈을 import 구문을 통해 불러옴
* Javascript를 실행할 수 있게 해주는 환경인 Node.js에서 지원하는 기능
* Node.js에서는 import가 아닌 require 구문으로 패키지를 불러옴
> #### 번들러 - webpack
> * 리액트는 주로 웹팩을 사용함(편의성과 확장성이 다른 도구보다 뛰어남)
> * import 또는 require로 모듈을 불러왔을 때 불러온 모듈을 합쳐서 하나의 파일을 생성 
> * css-loader - CSS파일을 불러올 수 있음
> * file-loader - 웹 폰트, 미디어 파일등을 불러올 수 있음
> * babel-loader - 자바스크립트 파일을 불러오고 최신 자바스크립트 문법으로 작성된 코드를 ES5 문법으로 변환
> * create-react-app - 직접 웹팩의 로더를 설치하고 설정해야 할 수고를 덜어줌

## 2.2 JSX란?
* JSX는 자바스크립트의 확장 문법이며 XML과 매우 비슷하게 생김
* 브라우저에서 실행되기 전 코드가 번들링되는 과정에서 바벨을 사용하여 일반 자바스크립트 형태 코드로 변환
```jsx
function App() {
  return (
    <div>
      Hello <b>react</b>
    </div>
  );
}
```
아래의 코드처럼 변환
```jsx
function App() {
  return React.createElement("div", null, "Hello ", React.createElement("b", null, "react"));
}
```

## 2.3 JSX의 장점

### 2.3.1 보기 쉽고 익숙하다
* HTML 코드를 작성하는 것과 비슷하기 떄문에 가독성이 높고 작성하기 쉬움

### 2.3.2 더욱 높은 활용도
> #### ReactDOM.render
> * 컴포넌트를 페이지에 렌더링하는 역할
> * 첫번째 파라미터 - 페이지에 렌더링할 내용을 JSX형태로 작성
> * 두번째 파라미터 - 해당 JSX를 렌더링 할 document 내부 요소를 설정

## 2.4 JSX문법

### 2.4.1 감싸인 요소
* 컴포넌트에 여러 요소가 있다면 반드시 부모 요소 하나로 감싸야 함
* Virtual DOM에서 컴포넌트 변화를 감지해 낼 때 효율적으로 비교할 수 있도록 컴포넌트 내부는 하나의 DOM트리 구조로 이루어져야 함

### 2.4.2 자바스크립트 표현
* 자바스크립트 표현식은 { } 로 함

### 2.4.3 if문 대신 조건부 연산자
* JSX 내부 { } 안에서 if문 사용이 불가능
* JSX 밖에서 if문을 사용하여 사전에 값을 설정하거나 조건부 연산자를 사용한다.

### 2.4.4 AND 연산자(&&)를 사용한 조건부 렌더링
* 특정 조건을 만족하거나 만족하지 않을때 사용
* 리액트에서 false를 렌더링할 때 null과 마찬가지로 아무것도 나타나지 않음
```jsx
  function App() {
    return <div>{name === '리액트' && <h1>리액트입니다.</h1>}</div>
  } 
```

### 2.4.5 undeined를 렌더링하지 않기
* 리액트 컴포넌트에서는 함수에서 undefined를 반환하면 안됨
* OR연산자(||)를 사용하면 오류를 방지할 수 있음
```JSX
  function App() {
      const name = undefined;
      return name || '값이 undefined입니다.'
    } 
```

### 2.4.6 인라인 스타일링
* 리액트 DOM 요소에 스타일 적용시 객체로 넣음
* 카멜 표기법으로 작성 (background-color -> backgroundColor)
