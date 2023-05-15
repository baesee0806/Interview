# closure란?

함수와 그 함수가 선언된 어휘적 환경의 조합이다.

```javascript
function counter() {
  let count = 0;
  return function () {
    count++;
    console.log(count);
  };
}
```
이코드에서의 counter는 함수이고, counter()를 호출하면 내부에 있는 익명함수가 반환된다. 이 익명함수는 count라는 변수를 참조하고 있다. 이 익명함수가 바로 클로저이다.

단순하게 설명하자면, 함수 내에서 선언된 변수를 반환된 함수에서도 접근하여 사용할 수 있다는 것입니다. 이를 통해 생성된 함수에서 외부 함수의 변수 값에 계속 접근하여 사용할 수 있고, 이를 통해 프로그래밍에서 유용하게 사용됩니다.