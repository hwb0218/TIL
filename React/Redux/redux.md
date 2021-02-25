## Redux
* 자바스크립트로 만든 app을 위한 예측 가능한 상태의 저장소    
* 상태값을 컴포넌트에 종속시키지 않고, 상태 관리를 컴포넌트의 바깥에서 관리 할 수 있다.
* 컴포넌트끼리 같은 상태를 공유해야 할 때 여러 컴포넌트를 거치지 않고 상태 값을 전달하거나 업데이트 할 수 있다.   

## Reducer
* state와 action을 통해 nextState return, store의 state값을 변경한다.
* nextState는 원본이 아닌 사본값을 return 받아야한다.

## Redux를 사용하지 않으면?
* Redux를 사용하지 않은 코드는 component끼리의 의존성이 높다.   
  * 어떠한 component에서 다른 component가 연결 된 코드를 수정, 삭제하면 이에 맞춰서 각 component들의 코드를 수정, 삭제해야한다.          
    하지만, Redux를 통해 상태 관리를 컴포넌트의 바깥에서 처리한다면 각 component는 action을 통해 store에 dispatch 후   
    Reducer에서 state와 action을 가지고 새로운 state를 return store에 subscribe했던 component는 새로운 state를 통해 render를 한다. 
