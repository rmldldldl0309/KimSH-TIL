# 이벤트

이벤트는 프로그래밍하고 있는 시스템에서 일어나는 사건이나 발생을 의미한다, 발생하는 시점이나 순서를 사전에 인지할 수 없으므로 일반적인 제어 흐름과는 다른 접근 방식이 필요하다

## ▶ 이벤트 바인딩

### 1. 인라인 이벤트 핸들러

HTML 어트리뷰트 안에 직접접으로 Javascript를 삽입한 경우이다. 하나의 파일로 이루어지지만 두가지의 요소가 섞이는 것이기에
분석하기에 용이하지 않고 이는 유지보수에 어려움을 더한다. 현재 이방식은 권장되지 않는 방식으로 사용하지 않는것이 바람직하다.

### 2. 이벤트 핸들러 프로퍼티

Javascript와 HTML이 뒤섞이는 문제를 해결할 수 있지만, 이벤트 별로 하나의 함수만을 바인딩할 수 있다는 단점이 있다

### 3. 이벤트 리스너 방식

`addEventListener()` 메서드를 이용하여 바인딩하는 방식이다. 하나의 이벤트에 대해 하나 이상의 이벤트 핸들러를 추가할 수 있고, HTML요소 뿐만 아니라 DOM요소에대해서도 동작한다

* `removeEventListner()`를 통해 이벤트 리스너를 제거할 수 있다. 단, 같은 요소를 가진 것에 한하여 삭제가 가능하다

## ▶ 이벤트의 종류

* Mouse Event

|Event    |Description|Event|Description|
|:---     |:---                     |:---     |:---|
|mousedown|마우스 버튼 누르고 있을 때 |mousemove|마우스를 움직일 때|
|mouseup  |마우스 버튼 뗄 때         |mouseover|마우스를 요소 안으로 움직였을 때|
|click    |마우스 버튼 클릭          |mouseout |마우스를 요소 밖으로 움직였을 때|
|dbclick  |마우스 버튼 더블 클릭      |         |      |

* Keyboard Event

|Event  |Description|
|:---   |:---|
|keydown|키를 누르고 있을 때 |
|keyup  |누르고 있던 키를 뗄 때|
|keypress|마우스 버튼 클릭|

* UI Event

|Event   |Description|Event   |Description|
|:---    |:---|:---    |:---|
|load    |페이지의 로드가 완료 |error |브라우저가 자바스크랩트 오류를 만났거나 요청한 자원 존재 X|
|unload  |페이지가 언로드 될 때|resize|브라우저 크기 조절했을 때|
|select  |텍스트를 선택했을 때 |scroll|페이지 스크롤 할때|

* Focus Event

|Event  |Description|
|:---   |:---|
|submit |사용자가 버튼이나 키를 이용하여 폼을 제출할 때|
|input  |input 또는 textarea 요소 값이나 contentediate특성을 가진 요소 값이 변경되었을 때|
|change |select box, checkbox, radio button 의 상태가 변경되었을 때|
|reset  |reset버튼을 클릭할 때|

* Clipboard Event

|Event |Description|
|:---  |:---|
|cut   |콘텐츠를 잘라내기 할 때 |
|copy  |콘텐츠를 복사할 때|
|paste |콘텐츠를 붙여넣기 할 때|

* Focus Event

|Event|Description|
|:--- |:---|
|focus|요소가 포커스를 얻었을 때|
|focus in |요소가 포커스를 얻었을 때|
|focus out|요소가 포커스를 잃었을 때|
|blur |요소가 포커스를 잃었을 때|

## ▶ 이벤트 객체

### - 프로퍼티

* `.target` : 이벤트가 처음 발생한 대상을 가리킨다
* `.currentTarget` : 현재 이벤트가 발생하고 있는 대상
* `.type` : 발생한 이벤트의 이름, 대소문자를 구분하지 않는다

### - 메서드

* `.preventDafault()` : 이벤트를 취소
* `.stopPropagation()` : 이벤트의 DOM 전파를 멈춘다

## ▶ 이벤트 버블링과 캡쳐링

버블링 : 한 요소에 이벤트가 발생할 때 요소에 할당된 핸들러가 동작하고, 가장 최상단의 조상 요소를 만날 때까지 부모 요소의 핸들러가 동작하는 현상<br/>기본적으로 브라우저의 이벤트들은 버블링 방식으로 전파된다. 단, 버블링이 진행되는 중에도 `target`은 부모 요소의 핸들러가 동작함에도 맨 처음으로 이벤트가 일어났던 요소에 머무른다

캡쳐링 : 한 요소에 이벤트가 발생되면, 그 요소 자손 요소의 이벤트도 같이 발생하는 현상, 기본적으로 브라우저의 이벤트 전파 방식은 버블링이 기본값이기에 따로 설정해주어야 한다<br/>
`addEventListener()`함수의 3번째 매개변수로 `true`값을 주는 것으로 캡쳐링을 발동시킬 수 있다

* `stopPropagation()`메서드를 통하여 버블링이 실행되는 것을 막을 수 있다

## ▶ 이벤트 위임

이벤트 위임을 이용하면 각 요소마다 각각 핸들러를 할당하지 않고도 여러 요소를 한번에 다룰 수 있게된다. 버블링 요소를 이용하여 자식요소들에 각각 이벤트 핸들러를 할당하지 않고, 부모 요소에 이벤트 핸들러를 등록하는 것으로 자식 요소들에게 발생한 이벤트를 관리할 수 있다. 

# 참조

* https://developer.mozilla.org/ko/docs/Learn/JavaScript/Building_blocks/Events#event_bubbling_and_capture

* 이벤트
    * https://ko.javascript.info/mouse-events-basics
    * https://milooy.github.io/TIL/JavaScript/event.html#%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3-%E1%84%8C%E1%85%A9%E1%86%BC%E1%84%85%E1%85%B2
    * https://developer.mozilla.org/ko/docs/Web/API/ClipboardEvent
    * https://developer.mozilla.org/ko/docs/Web/API/Event
    * https://cheonmro.github.io/2018/09/04/event-object/

* 버블링과 캡쳐링
    * https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-%EB%B2%84%EB%B8%94%EB%A7%81-%EC%BA%A1%EC%B3%90%EB%A7%81#%EC%9D%B4%EB%B2%A4%ED%8A%B8_%EB%B2%84%EB%B8%94%EB%A7%81