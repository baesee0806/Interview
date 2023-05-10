# async/await란?

asyn/await은 자바스크립트의 비동기 처리 패턴 중 하나로, Promise와(또는 콜백 함수와) 함께 사용되어 비동기 코드를 동기식으로 작성할 수 있도록 해줍니다.


```javascript
async function asyncExample() {
  try {
    const result = await someAsyncFunc(); // 비동기 처리 코드
    console.log(result);
  } catch (err) {
    console.error(err);
  }
}
```

async 함수를 정의하면 항상 Promise를 반환하며, await 키워드를 사용해 비동기 처리 코드를 작성합니다.


## 예외 처리 방법

async/await은 try-catch 블록 내에서 에러 처리가 가능합니다.


```javascript
try {
  const result = await someAsyncFunc();
} catch {
  console.log('error occurred')
}
```

## async/await의 장점

코드의 가독성이 좋습니다.

비동기 코드를 동기식으로 작성할 수 있어 코드의 흐름을 파악하기 쉽습니다.

Promise에서 발생하는 콜백 지옥 현상을 해결할 수 있습니다.

## async/await의 단점

코드의 대규모 반복 처리 시 블로킹이 발생할 수 있습니다.

try-catch 블록을 비동기 함수마다 생성해야하므로 코드가 많아질 수 있습니다.

async/await은 아직 모든 환경에서 지원되지 않습니다.

## async/await 이전의 사용 방법

기존의 비동기 처리 방법 중 하나로 콜백 함수를 사용하여 처리하는 방법이 있습니다. 일반적으로 콜백 함수는 함수 안에서 비동기적인 작업이 끝난 후 호출되며, 해당 작업에서 반환받은 결과를 인수로 받아 처리합니다.


```javascript
function someAsyncTask(param, callback) {
    // 비동기적인 작업 호출
    setTimeout(() => {
        const result = param + 1;
        callback(result);
    }, 1000);
}

// 콜백 함수를 사용한 비동기 처리 예시
someAsyncTask(1, (result) => {
    console.log(result);
});
```

위 코드에서, someAsyncTask 함수는 1초 후에 param에 1을 더한 값으로 callback 함수를 호출합니다. 이후 result 값이 출력됩니다.


Promise를 사용한 비동기 처리 방법은 콜백 함수를 사용하는 방법에서, 비동기 작업이 수행될 객체인 Promise 객체를 반환하는 방법으로 대체되었습니다.


```javascript
function someAsyncTask(param) {
    return new Promise((resolve, reject) => {
        // 비동기적인 작업 호출
        setTimeout(() => {
            const result = param + 1;
            resolve(result);
        }, 1000);
    });
}

// Promise를 사용한 비동기 처리 예시
someAsyncTask(1).then((result) => {
    console.log(result);
});
```
위 코드에서, someAsyncTask 함수는 Promise 객체를 반환하며, 1초 후에 param에 1을 더한 값을 resolve 메서드의 인수로 전달합니다. 이후 then 메서드를 사용하여 resolve 값을 출력합니다.

## 동기/비동기 

동기와 비동기는 코드의 실행 방식과 관련이 있습니다. 동기식 코드는 코드의 흐름이 일련의 명령문처럼 위에서 아래로 실행되며 결과를 반환하기 전까지는 다른 작업을 처리할 수 없지만, 비동기식 코드는 작업을 요청하면 결과를 기다리지 않고 다른 코드를 실행하다가 작업이 완료되면 이벤트를 받아 처리합니다.


```javascript
// 동기식 예제
const syncValue = doSomethingSync();

// 비동기식 예제
doSomethingAsync((err, value) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(value);
});
```