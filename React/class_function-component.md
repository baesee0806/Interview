# class component / function component

React 에서 component 는 class component 와 function component 로 나뉜다.

## class component

class component의 예시는 다음과 같다.

```jsx
import React, {Component} from 'react';

class App extends Component {
  render() {
    const name = 'react';
    return <div className="react">{name}</div>
  }
}
```
- state, lifeCycle 관련 기능사용 가능하다.
- 메모리 자원을 함수형 컴포넌트보다 조금 더 사용한다.
- 임의 메서드를 정의할 수 있다.
---

## function component

function component의 예시는 다음과 같다.

```jsx
import React from 'react';
import './App.css';

function App() {
  const name = 'react';
  return <div className = "react">{name}</div>
}

export default App;
```
- state, lifeCycle 관련 기능사용 불가능 [Hook을 통해 해결 됨]
- 메모리 자원을 함수형 컴포넌트보다 덜 사용한다.
- 컴포넌트 선언이 편하다.
<!-- 참고 
https://velog.io/@sdc337dc/0.%ED%81%B4%EB%9E%98%EC%8A%A4%ED%98%95-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8
 -->