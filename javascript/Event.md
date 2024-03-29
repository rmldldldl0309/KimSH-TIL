# 이벤트

* 이벤트 : 프로그래밍하고 있는 시스템에서 일어나는 사건이나 발생, 발생하는 시점이나 순서를 사전에 인지할 수 없으므로 일반적인 제어 흐름과는 다른 접근 방식이 필요

## ▶ 이벤트 바인딩

### 1. 인라인 이벤트 핸들러

HTML 어트리뷰트 안에 직접접으로 Javascript를 삽입한 경우이다. 하나의 파일로 이루어지지만 두가지의 요소가 섞이는 것이기에
분석하기에 용이하지 않고 이는 유지보수에 어려움을 더한다. 현재 이방식은 권장되지 않는 방식으로 사용하지 않는것이 바람직하다.

### 2. 이벤트 핸들러 프로퍼티

Javascript와 HTML이 뒤섞이는 문제를 해결할 수 있지만, 이벤트 별로 하나의 함수만을 바인딩할 수 있다는 단점이 있다

### 3. 이벤트 리스너 방식

`addEventListener()` 메서드를 이용하여 바인딩하는 방식이다. 하나의 이벤트에 대해 하나 이상의 이벤트 핸들러를 추가할 수 있고, HTML요소 뿐만 아니라 DOM요소에대해서도 동작한다

* `removeEventListner()`를 통해 이벤트 리수너를 제거할 수 있다. 단,

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


# 참조

* https://ko.javascript.info/mouse-events-basics
* https://milooy.github.io/TIL/JavaScript/event.html#%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3-%E1%84%8C%E1%85%A9%E1%86%BC%E1%84%85%E1%85%B2
* https://developer.mozilla.org/ko/docs/Web/API/ClipboardEvent