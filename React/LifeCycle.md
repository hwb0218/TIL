# LifeCycle method
모든 리액트 컴포넌트에는 라이프사이클이 존재한다.     
컴포넌트의 수명은 페이지에 렌더링되기 전인 준비 과정에서 시작하여 페이지에서 사라질 때 끝난다.     
클래스형 컴포넌트에서만 사용 가능하며 함수형 컴포넌트에서는 Hooks 기능을 사용하여 작업한다.

<img src="https://user-images.githubusercontent.com/52212226/108171753-56519e80-713f-11eb-946e-9177b3f9a9d9.jpeg" width="600" height="400">

## 라이프사이클 메서드의 이해
라이프사이클 메서드의 종류는 총 9가지     
Will 접두사가 붙은 메서드 - 어떤 작업을 작동하기 __전__ 실행되는 메서드      
Did 접두사가 붙은 메서드 - 어떤 작업을 작동한 __후__ 실행되는 메서드

라이프사이클은 세가지 카테고리로 나뉜다.

### 마운트
DOM이 생성되고 웹 브라우저 상에 나타나는 것

__마운트 할 때 호출하는 메서드__

* constructor : 컴포넌트를 생성할 때 호출되는 클래스 생성자 메서드      
* getDerivedStateFromProps : props에 있는 값을 state에 동기화 할 때 호출하는 메서드     
* render : UI를 렌더링하는 메서드      
* componentDidMount : 컴포넌트가 웹 브라우저상에 나타난 후 호출하는 메서드

### 업데이트
컴포넌트는 다음의 경우에 업데이트한다.
1. props가 바뀔 때
2. state가 바뀔 때
3. 부모컴포넌트가 리렌더링될 때
4. this.forceUpdate로 강제로 렌더링을 트리거할 때

__업데이트 할 때 호출하는 메서드__

* getDerivedStateFromProps : 업데이트 과정에서도 호출된다. props의 값의 변화에 따라 state에 동기화한다.      
* shouldComponentUpdate : 메서드에서 true, false를 반환해야 한다.       
true의 경우 다음 라이프사이클 메서드를 실행, false의 경우 업데이트 중지
* render : 컴포넌트를 리렌더링한다.
* getSnapshotBeforeUpdate : 컴포넌트 변화를 DOM에 반영하기 바로 직전에 호출하는 메서드
* componentDidUpdate : 컴포넌트 업데에트 작업이 끝난 후 호출하는 메서드 

### 언마운트
컴포넌트를 DOM에서 제거하는 것

__언마운트 할 때 호출하는 메서드__

* componentWillUnmount : 컴포넌트가 웹 브라우저상에서 사라지기 전에 호출하는 메서드
