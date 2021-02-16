# This
* 함수를 호출할 때 함수가 어떻게 호출되었는지에 따라 this에 바인딩할 객체가 동적으로 결정된다.

함수를 호출하는 방식은 크게 3가지가 있다.
1. 함수 호출
2. 메소드 호출
3. 생성자 함수 호출

## 1. 함수 호출
* 일반적인 함수호출에서는 this는 전역객체에 바인딩된다.
* 브라우저에서는 window객체, node.js에서는 글로벌 객체를 가리킨다.
```javascript
const outer = function () {
    console.log('outer', this); // window
    const inner = function () {
        console.log('inner', this); // window
    }
    inner();
}
outer();
```

## 2. 메소드 호출
* 함수가 객체의 프로퍼티 값이면 메소드로서 호출된다.
* 메소드 내부의 this는 메소드를 소유한 객체, 즉 해당 메소드를 호출한 객체에 바인딩된다.
* 메소드 내부에서 호출된 함수는 일반 함수 호출에서 처럼 this는 전역 객체에 바인딩된다.
```javascript
const person = {
    name: 'olaf',
    printName: function () {
        console.log(this.name); // olaf
        
        function inner() {
            console.log(this); // window
        }
        inner();
    }
}
person.printName();
```

## 3. 생성자 함수 호출
* 생성자 함수 코드가 실행되기전에 빈 객체가 생성된다.
* 이후 생성자 함수 내에서 사용되는 this는 이 빈 객체를 가리킨다.
```javascript
const Person = function (name) {
    this.name = name; // Person
}
Person.prototype.getName = function () {
    console.log(this.name); // Person.prototype 이기때문에 프로토타입 내에서도 this는 Person을 가리킨다.

    function inner() {
        console.log(this); // window
    }
    inner();
}
```

## call, apply
call과 apply는 기본적으로 함수를 호출하는 메소드다.          
this에 바인딩 할 객체를 동적으로 지정할 수 있다.          
두 메소드의 차이는 apply메소드는 두 번째 인자를 배열로 받는다.
```javascript
const obj = { name: 'wb' }

const say = function(city) {
    console.log(`Hello, my name is ${this.name}, I live In ${city}`);
}
say('seoul'); // Hello, my name is , I live In seoul
say.call(obj, 'seoul'); // Hello, my name is wb, I live In seoul
say.apply(obj, ['seoul']); // Hello, my name is wb, I live In seoul
```

## bind
bind는 call, apply와 다르게 함수를 호출하지 않으며 bound함수를 반환한다.                      
비동기 함수를 실행시킬 때 this 바인딩이 풀리는 경우 this를 고정시키기 위해 자주 사용한다.
```javascript
const obj = { name: 'wb' }

const say = function(city) {
    console.log(`Hello, my name is ${this.name}, I live In ${city}`);
}
const boundSay = say.bind(obj);
boundSay('seoul'); // Hello, my name is wb, I live In seoul
```
