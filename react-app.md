# 생활코딩 react
## Create-react-app 구조
<div>
  <img src="https://user-images.githubusercontent.com/52212226/101463592-f8574c80-3980-11eb-9ab1-5451eacfe2d8.png" width="200">
</div>

> Public 폴더 안에 쓰인 파일들은 오직 index.html에서만 쓰일 수 있다.         
> Src 폴더안에 js파일과 css파일들을 넣으면 된다.     
> Webpack은 이 곳에 있는 파일만 본다.    
> 이외의 다른 폴더는 webpack에 의해서 처리되지 않음    

## JS 코딩하는 법
<div>
  <img src="https://user-images.githubusercontent.com/52212226/101465864-d0b5b380-3983-11eb-9b8a-093da45b9ad9.png" width="350">
</div>

> index.js 안에서 document.getElementById 통해서 Index.html의 id = ‘root’ 를 선택       
> App은 리액트를 통해서 만든 사용자 정의 태그 즉, 컴포넌트    

## 컴포넌트 만들기
<div>
  <img src="https://user-images.githubusercontent.com/52212226/101466541-9ac4ff00-3984-11eb-9fee-8e3ee8074e47.png" width="350">
</div>

> Class를 생성하고 생성한 class를 App class안에서 html 태그처럼 사용하면 된다.

## props
> this.props.name을 사용하여 컴포넌트의 속성을 표현할 수 있다.   
> props는 부모 컴포넌트가 자식 컴포넌트에게 값을 전달한다.   

## state
> state는 컴포넌트 내부에서 선언하며 내부에서 값을 변경할 수 있다.    
> 컴포넌트가 실행될 때 render 함수보다 생성자 함수가 먼저 실행되어 초기화를 담당한다.    

## 이벤트 bind 함수
```jsx
<a href="/" onClick={
    (function (e) {
        e.preventDefault();
        this.setState({
            mode: 'read'
        });
    }).bind(this)
}>
```
>이벤트 핸들러 어트리뷰트의 값으로 지정한 함수는 이벤트 핸들러에 의해 일반함수로 호출되고    
>this는 전역 객체인 window를 가리키게 된다.    
>strict mode가 적용된 일반 함수의 내부의 this에는 window객체가 아닌 undefined가 바인딩   
>bind메서드를 사용해서 명시적으로 this를 바인딩 해줌으로써 this가 Class를 가리키도록 해주는 것   


