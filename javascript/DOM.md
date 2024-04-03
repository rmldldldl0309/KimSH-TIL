# 문서 객체 모델 (DOM)

문서 객체 모델은 웹페이지(HTML, XML 등)의 콘텐츠와 구조 및 스타일 요소를 구조화 시켜 표현하여 프로그래밍 언어가 해당 문서에 접근하여 읽고 조작할 수 있도록 API를 제공하는 일종의 인터페이스를 뜻한다<br/>

## ▶ 구조

문서 객체 모델은 총 4가지의 노드로 나누어져 있다 (문서노드, 요소노드, 텍스트노드, 속성노드)

* 문서(document) 노드 : DOM Tree의 최상의 루트 노드, document 객체를 가리키며 문서 전체를 나타내는 노드이다 `document`, `window.document`를 통해 사용할 수 있ㄷ 
* 요소(element) 노드 : `HTML`, `body`, `div` 등 모든 HTML 요소들이 요소노드에 속한다. 부모-자식관계가 존재하여 계층구조를 이루며, 유일하게 속성을 가질 수 있다
* 텍스트(text) 노드 : 모든 텍스트가 속하는 노드
* 속성(attribute) 노드 : HTML요소들의 속성이 속하는 노드

## ▶ DOM 타입

* `document` : document 타입의 객체를 리턴했을때의 객체
*  `node` : .문서내의 모든개체는 일종의 노드이다
* `element` : DOM API의 멤버에 의해 반환된 요소또는 `element`타입의 노드를 의미한다
* `nodeList` : `element`의 배열이며 인덱스를 통해 접근이 가능하다. `list.item[i]`, `list[i]`의 방식으로 접근이 가능하다

## ▶ DOM 접근방법

* `document.`
| Method             | Description                                                    |
|--------------------|----------------------------------------------------------------|
| querySelector()    | 제공한 선택자를 만족하는 첫번째 객체를 반환                    |
| querySelectorAll() | 제공한 선택자와 일치하는 모든 요소를 반환                      |
| getElementById()   | 제공한 문자열과 일치한 `id`속성을 가진 요소를 찾아 요소를 반환 |

* `.node`
| Method        | Description                                                                     |
|---------------|---------------------------------------------------------------------------------|
| append()      | 지정된 요소의 자식 노드 리스트의 끝에 하나이상의 노드 혹은 DOMString객체를 추가 |
| appendChild() | 지정된 요소를 제거                                                              |
| removeChild() | 지정된 부모 요소의 자식 요소 중 하나를 제거                                     |
| textContent   | 노드와 그 자손의 텍스트 콘텐츠를 표현합니다                                     | 

`.element`
| Method             | Description                                                           |
|--------------------|-----------------------------------------------------------------------|
| setAttribute()     | 지정한 요소의 속성 값을 설정, 이미 속성이 존재하는 경우 업데이트 한다 |
| getAttribute()     | 지정한 요소의 지정된 속성 값을 반환                                   |
| addEventListener() | 지정된 이벤트가 대상에 전달될 때 마다 호출되는 함수를 설정            |
| innerHTML          | 요소 안의 HTML이나 XML을 가져온다                                     |

# 참조

* https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model/Introduction
* https://www.codestates.com/blog/content/dom-javascript
* https://newcodingman.tistory.com/entry/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-append-vs-appendChild-%EC%B0%A8%EC%9D%B4%EC%A0%90
