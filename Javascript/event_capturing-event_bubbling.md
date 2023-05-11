## 이벤트 캡처링(Event Capturing)



이벤트가 하위에서 상위의 엘리먼트로 전파되는 방식입니다.

즉, 최상위 엘리먼트에서 이벤트가 발생하고 하위 엘리먼트로 전달되는 것입니다.

이 방식은 실제로는 거의 사용되지 않습니다.


```html
<div id="outer">
  <div id="inner"></div>
</div>
```
```javascript
const outer = document.querySelector('#outer');
const inner = document.querySelector('#inner');

outer.addEventListener('click', () => {
  console.log('outer clicked');
}, true);
inner.addEventListener('click', (e) => {
  e.stopPropagation();
  console.log('inner clicked');
}, true);
```
위 코드에서 addEventListener 메서드의 3번째 인자로 useCapture를 true로 설정하면, 이벤트는 이벤트 캡처링으로 전파됩니다. 위의 코드에서 outer 엘리먼트를 클릭하면 outer clicked가 출력되고, inner 엘리먼트를 클릭하면 브라우저의 기본 동작이 일어나지 않게 하기 위해 event.stopPropagation()을 호출해서 이벤트 전파를 막아놓았기 때문에 inner clicked만 출력됩니다.


## 이벤트 버블링(Event Bubbling)



이벤트가 상위에서 하위의 엘리먼트로 전파되는 방식입니다.

즉, 이벤트가 발생한 하위 엘리먼트에서 상위 엘리먼트로 전달되는 것입니다.

이 방식이 실제로 사용되는 경우가 많습니다.


```javascript
const outer = document.querySelector('#outer');
const inner = document.querySelector('#inner');

outer.addEventListener('click', () => {
  console.log('outer clicked');
});
inner.addEventListener('click', () => {
  console.log('inner clicked');
});
```

위 코드에서 addEventListener 메서드의 3번째 인자로 useCapture를 생략하거나 false로 설정하면, 이벤트는 이벤트 버블링으로 전파됩니다. 위의 코드에서 inner 엘리먼트를 클릭하면 inner clicked가 출력되고, outer 엘리먼트를 클릭하면 inner clicked, outer clicked가 출력됩니다.


이벤트 캡처링과 이벤트 버블링의 사용은 주로 이벤트 핸들러를 등록할 때, addEventListener 메서드의 3번째 인자로 useCapture를 설정하여 변경할 수 있습니다. 그러나 이벤트 전파를 중단하려면 이벤트 객체의 stopPropagation() 메서드를 호출하여 이벤트 전파를 막을 수 있습니다.