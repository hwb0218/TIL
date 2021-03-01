# 1. TypeScript란 무엇일까?
TypeScript는 JavaScript의 슈퍼셋이다. JavaScript를 기반으로 한 언어라는 뜻이다.       
JavaScript코드를 보다 쉽게 그리고 강력하게 작성 할 수 있는 좀 더 나은 JavaScript라고 생각하면 된다.
 
## 2. TypeScript 장점
- 버그를 줄일수 있다.
- 유지 보수가 쉽다.
- 질 좋은 코드를 작성할 수 있다.

### 2.1 정적 타입 지원

```javascript
//Javascript
function add (a, b) {
    return a + b;
}
console.log(add ('3', '5')); // 문제없이 정상적으로 실행된다. 
```

```typescript
//Typescript
function add (a: number, b: number) {
    return a + b;
}
console.log(add ('3', '5')); // 에러가 발생한다.
```
정적 타입을 지원하기 때문에 컴파일 단계에서 오류를 포착 할 수 있다.     
명시적인 정적 타입지정은 개발자의 의도를 명확하게 표현할 수 있고, 코드의 가독성을 높이며 유지 보수가 쉬워진다.
