## React.Suspense란?

React.Suspense는 트리 하단에 있는 일부 컴포넌트가 아직 렌더링할 준비가 되지 않은 경우 로딩 지시기 (Loading indicator)를 나타낼 수 있도록 해줍니다.

현재 <React.Suspense>가 지원하는 유일한 사용 사례는 lazy loading 컴포넌트입니다.

```
// 이 컴포넌트는 동적으로 불러옵니다
const OtherComponent = React.lazy(() => import('./OtherComponent'));

function MyComponent() {
  return (
    // Displays <Spinner> until OtherComponent loads
    <React.Suspense fallback={<Spinner />}>
      <div>
        <OtherComponent />
      </div>
    </React.Suspense>
  );
}
```

lazy한 컴포넌트는 Suspense 트리 내의 깊숙한 곳에 위치할 수 있다는 점에 유의하세요. 즉, Suspense가 모든 컴포넌트를 감쌀 필요는 없다는 것입니다. 가장 좋은 사용법은 로딩 지시기를 보여주고 싶은 지점에 <Suspense>를 작성하는 것이지만, Code Splitting을 하고자 하는 지점 어디서든지 lazy()를 써야 할 것입니다.

이는 react 공식 자료에 적힌 말이다.

Suspense는 아직 렌더링이 준비되지 않은 컴포넌트가 있을때 로딩 화면을 보여주고 로딩이 완료되면 해당 컴포넌트를 보여주는 React에 내장되어 있는 기능이다.

## 왜 사용할까?

SPA(Single-Page-Application)의 단점은 한번에 사용하지 않는 모든 컴포넌트까지 불러오기 때문에 첫 화면이 렌더링 될때까지의 시간이 오래걸리는 것이다. React는 lazy를 통해 컴포넌트를 동적으로 import를 할 수 있기 때문에 이를 사용하면 초기 렌더링 지연시간을 어느정도 줄일 수 있다

```
const SomeComponent = React.lazy(() => import('./SomeComponent'));
```

Router로 분기가 나누어진 컴포넌트들을 위 코드처럼 lazy를 통해 import하면 해당 path로 이동할때 컴포넌트를 불러오게 되는데 이 과정에서 로딩하는 시간이 생기게 된다. 이 로딩되는 시간동안 로딩 화면을 보여지도록 해주는 역할을 하는 것이 바로 Suspense 이다.
