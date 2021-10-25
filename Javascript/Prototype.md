# Prototype
자바스크립트의 모든 객체는 자신의 부모 역할을 담당하는 객체와 연결되어 있다.      
이러한 부모 객체를 Prototype 객체 또는 Prototype이라 한다.      

Prototype 객체는 생성자 함수에 의해 생성된 각각의 객체에 공유 프로퍼티를 제공하기 위해 사용한다.

```javascript
const person = {};

const Person = function(name) {
  this.name = name
}

console.dir(person); // Object.prototype
console.dir(Person); // Person.prototype
```
__proto__ 프로퍼티로 자신의 부모 객체에 접근할 수 있다. 

## [[Prototype]] (===&#95;&#95;proto__)
* 함수를 포함한 모든 객체가 가지고 있는 인터널 슬롯이다.
* 객체의 입장에서 자신의 부모 역할을 하는 prototype 객체를 가리킨다(프로토타입 링크)
* 함수 객체의 경우 Function.prototype을 가리킨다.

## prototype 프로퍼티
* 함수 객체만 가지고 있는 프로퍼티
* 생성자 함수로 생성된 객체의 부모 역할을 하는 prototype 객체를 가리킨다.

## constructor 프로퍼티
* prototype 객체는 constructor 프로퍼티를 갖는다. 
* constructor 프로퍼티는 prototype 객체의 입장에서 자신을 생성한 객체를 가리킨다.

<img src="https://user-images.githubusercontent.com/52212226/107618575-1f8a0d00-6c95-11eb-88a3-0209e70d2481.png" width="400" height="300">      

> 출처 생활코딩 Javascript 객체 지향 프로그래밍

## Prototype chain
자바스크립트는 특정 객체의 프로퍼티나 메소드에 접근하려고 했을 때 없으면       
[[Prototype]] (&#95;&#95;proto__) 가 가리키는 링크를 따라 자신의 부모 역할을 하는 prototype 객체의 프로퍼티나 메소드를 차례대로 검사한다.
```javascript
const Person = function(name) {
  this.name = name;
}
Person.prototype.getName = function() {
  console.log(this.name) // foo
}

const foo = new Person('foo');
```
foo 객체는 getName()이라는 함수를 가지고 있지 않지만       
prototype 객체와 연결된 프로토타입 링크를 통해 프로퍼티나 메소드를 차례대로 검사한다.




