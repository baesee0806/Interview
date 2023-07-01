### Promise란?

Promise는 비동기 처리에 사용되는 객체입니다. Promise는 비동기 작업이 끝난 후의 결과를 나타냅니다. Promise는 다음과 같은 상태를 가집니다.

- 대기(pending): 비동기 처리가 아직 수행되지 않은 상태
- 이행(fulfilled): 비동기 처리가 수행된 상태(resolve)
- 거부(rejected): 비동기 처리가 실패한 상태(reject)

Promise는 다음과 같은 메서드를 제공합니다.

- then: 이행 상태일 때 호출되는 메서드
- catch: 거부 상태일 때 호출되는 메서드
- finally: 이행 또는 거부 상태일 때 호출되는 메서드

Promise는 다음과 같은 특징을 가집니다.

- Promise는 생성자 함수로 생성합니다.
- Promise는 비동기 처리가 성공하면 resolve 메서드를 호출하고, 실패하면 reject 메서드를 호출합니다.
- Promise는 then, catch, finally 메서드를 통해 비동기 처리 결과를 사용합니다.
- Promise는 비동기 처리가 끝난 후의 결과를 가지고 있습니다.
- Promise는 비동기 처리가 끝난 후에도 then, catch, finally 메서드를 통해 비동기 처리 결과를 사용할 수 있습니다.

### Promise의 사용

Promise는 다음과 같이 생성합니다.

```javascript
const promise = new Promise((resolve, reject) => {
  // 비동기 처리를 수행합니다.
  // ...
  if (/* 비동기 처리 성공 */) {
    resolve('result');
  } else { /* 비동기 처리 실패 */
    reject('failure reason');
  }
});
```

Promise는 다음과 같이 사용합니다.

```javascript
promise
  .then((result) => {
    // 비동기 처리 성공 시
  })
  .catch((error) => {
    // 비동기 처리 실패 시
  })
  .finally(() => {
    // 끝나고 무조건 실행
  });
```

### Promise의 예외 처리

Promise는 다음과 같이 예외 처리합니다.

```javascript
const promise = new Promise((resolve, reject) => {
  // 비동기 처리를 수행합니다.
  // ...
  if (/* 비동기 처리 성공 */) {
    resolve('result');
  } else { /* 비동기 처리 실패 */
    reject(new Error('failure reason'));
  }
});

promise
  .then((result) => {
    // 비동기 처리 성공 시
  })
  .catch((error) => {
    // 비동기 처리 실패 시
  })
  .finally(() => {
    // 끝나고 무조건 실행
  });
```

### Promise의 체이닝

Promise는 다음과 같이 체이닝을 할 수 있습니다.

```javascript
const promise = new Promise((resolve, reject) => {
  // 비동기 처리를 수행합니다.
  // ...
  if (/* 비동기 처리 성공 */) {
    resolve('result');
  } else { /* 비동기 처리 실패 */
    reject(new Error('failure reason'));
  }
});

promise
  .then((result) => {
    // 비동기 처리 성공 시
    return 'result2';
  })
  .then((result2) => {
    // 비동기 처리 성공 시
  })
  .catch((error) => {
    // 비동기 처리 실패 시
  })
  .finally(() => {
    // 끝나고 무조건 실행
  });
```

### Promise.all

Promise.all은 다음과 같이 사용합니다.

```javascript
const promise1 = new Promise((resolve, reject) => {
  // 비동기 처리를 수행합니다.
  // ...
  if (/* 비동기 처리 성공 */) {
    resolve('result1');
  } else { /* 비동기 처리 실패 */
    reject(new Error('failure reason1'));
  }
});

const promise2 = new Promise((resolve, reject) => {
  // 비동기 처리를 수행합니다.
  // ...
  if (/* 비동기 처리 성공 */) {
    resolve('result2');
  } else { /* 비동기 처리 실패 */
    reject(new Error('failure reason2'));
  }
});
```
