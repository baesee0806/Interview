### ① JavaScript 에서 Function안의 this란?

- The object that is executing the current function.
- 즉 **현재 함수를 부른 객체가 누구인지를 나타냄 (고정값이 아님)**

### ② 일반 함수 호출 (Single Function Invocation) 에서의 `this`

```
const name = 'Dong Hyun';
function hello(thing){
 console.log(this + 'says hello ' + thing);
 console.log('My name is' + this.name);
}

hello('world'); // [object Window] says hello world! \n My name is Dong Hyun
```

- global 객체인 **[window 객체](https://developer.mozilla.org/ko/docs/Web/API/Window/window)**
    - property 로는 전역변수들을 가진다.
- 단, strict 모드에선 **undefined**

### ② 객체의 메소드 (Method Function) 에서의 `this`

```
let person = {
 name : 'Jake',
 hello : function(thing){
	console.log(this.name + ' says hello ' + thing);
 }
}

person.hello('world'); // Jake says hello world
```

- **호출한 객체 (인스턴스)**
- 아무리 객체 안의 메서드라도, **메서드 그 자체가 아니라면 ① 상황으로 해석 해야 한다.**

```
    const value = 100;
    const myObj = {
      value: 1,
      func1: function() {
        console.log(`func1's this.value: ${this.value}`);

        const func2 = function() {
          console.log(`func2's this.value ${this.value}`);
        };
        func2();
      }
    };

    myObj.func1();
    // console> func1's this.value: 1
    // console> func2's this.value: 100
```

- `func1` ⇒ ② 상황 , 객체의 메서스
- `func2` ⇒ ① 상황, 일반 함수 호출

### ③ 생성자 함수 (Constructor Function)

- `new` 키워드를 이용해 생성자 함수를 호출하는 경우를 의미한다.

```
const Person = function(name) {
  console.log(this);
  this.name = name;
};

const foo = new Person("foo"); // Person
console.log(foo.name); // foo
```

- `*this` 는 객체 자신이 됨**
    1. 일단 빈 객체가 생성
    2. 이 빈 객체에 this 가 바인딩
    3. return 문이 명시되어 있지 않는 경우 this 로 바인딩 된 새로 생성한 객체가 반환됨

### ④ 화살표 함수 (Arrow Function)

- arrow function이 **정의된 곳의 렉시컬 환경에 따른다. (정적으로 결정)**
    - 렉시컬 환경과 관련된 이야기는 클로저 문서에서 확인

```
function objFunction() {
	console.log('Inside `objFunction`:', this.foo); // 13
	return {
		foo: 25,
	  bar: () => console.log('Inside `bar`:', this.foo) // 13
};
}

objFunction.call({foo: 13}).bar();
```

- arrow Function 이 정의된 곳 (상위 스코프)의 this 를 따른다
    - 위의 코드에서 상위 스코프는 `objFunction()` 함수 내부이다.
- 따라서, return 문에서 새롭게 `foo` 를 할당해서 오버라이딩을 할려해도 오버라이딩이 진행되지 않는다.
- 이에 따라서, `this` 를 실행단계가 아닌 **코드를 작성하는 단계에서 확인할 수 있다는 장점**을 가지게 된다.
- 아래 코드와 비교하면 좋다

```
function objFunction() {
	console.log('Inside `objFunction`:', this.foo); // 13
	return {
		foo: 25,
	  bar: function() {
				console.log('Inside `bar`:', this.foo) // 25
		}
};
}

objFunction.call({foo: 13}).bar();
```