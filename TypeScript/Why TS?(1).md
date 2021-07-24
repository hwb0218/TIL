## 타입스크립트란?
타입스크립트는 자바스크립트에 타입을 부여한 언어입니다. 자바스크립트의 확장된 언어라고 볼 수 있습니다.       
타입스크립트는 자바스크립트와 달리 브라우저에서 실행하려면 파일을 한번 변환해주어야 합니다.      
이 변환 과정을 우리는 컴파일(complile) 이라고 부릅니다.      

</br>

## 타입스크립트를 왜 사용하나?
* 에러의 사전 방지
* 코드 가이드 및 자동완성(개발 생산성 향상)

</br>

### 1. 에러의 사전 방지
```javascript
function sum(a, b) {
  return a + b;
}
sum('10', '20'); // 1020
```
```typescript
function sum(a: number, b: number) {
  return a + b;
}
sum('10', '20'); // Error: '10'은 number에 할당될 수 없습니다.
```
✔ 이처럼 의도하지 않은 코드의 동작을 예방할 수 있습니다. 

</br>

### 2. 코드 가이드 및 자동완성(개발 생산성 향상)
Visual Studio Code는 툴의 내부가 타입스크립트로 작성되어 있어 타입스크립트 개발에 최적화 되어 있습니다.
```javascript
function sum(a, b) {
    return a + b;
}
var result = sum(10, 20);
result.toLocaleString();
```
result라는 변수가 코드를 작성하는 시점에 타입이 __`number`__ 라는 것을 자바스크립트에서 인지하지 못합니다.      
달리 말하면, 개발자 스스로 __`sum()`__ 함수의 결과를 예상하고 타입이 __`number`__ 라고 가정한 상태에서      
__`number`__ 의 API인 __`toLocaleString()`__ 을 코딩하게 되는 것입니다.

</br>

```typescript
function sum(a: number, b: number): number {
  return a + b;
}
var total = sum(10, 20);
total.toLocaleString();
```
✔ 타입스크립트로 작성하면 변수 __`total`__ 에 대한 타입이 지정되어 있기 때문에 VSC에서 해당 타입에 대한 API를 미리 보기로 띄워주고     
따라서, API를 직접 작성할 필요 없이 tab으로 빠르고 정확하게 작성할 수 있습니다.
