# TDZ란? 
"Temporal Dead Zone"을 의미하며 JavaScript에서 변수가 존재하지만 액세스할 수 없는 기간을 나타냅니다. 변수가 `let` 또는 `const`로 선언되었지만 아직 초기화되지 않은 경우에 발생합니다.

TDZ 동안 변수에 액세스하려는 모든 시도는 `ReferenceError`를 발생시킵니다. 이는 변수가 범위에 존재하지만 아직 사용할 준비가 되지 않았음을 의미합니다. 변수에 값이 할당되면 TDZ가 종료됩니다.

```javascript
console.log(myVar); // ReferenceError
let myVar = 1;
```

`myVar`가 일반적으로 호이스팅을 허용하는 `let`으로 선언되더라도 초기화되기 전에 액세스하려고 하면 TDZ로 인해 `ReferenceError`가 발생합니다.