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
### 번들러 - webpack
* 리액트에서는 주로 웹팩을 사용함(편의성과 확장성이 다른 도구보다 뛰어남)
* import 또는 require로 모듈을 불러왔을 때 불러온 모듈을 합쳐서 하나의 파일을 생성 
* css-loader를 이용해 CSS파일을 불러올 수 있음
* file-loader를 이용해 웹 폰트, 미디어 파일등을 불러올 수 있음
* babel-loader를 이용해 자바스크립트 파일을 불러오고 최신 자바스크립트 문법으로 작성된 코드를 ES5 문법으로 변환
* create-react-app이 직접 웹팩의 로더를 설치하고 설정해야 할 수고를 덜어줌
