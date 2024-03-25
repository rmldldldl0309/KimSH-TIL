# fetch

* `fetch` 함수는 매개변수로 request를 보낼 URL을 받고 그에 대한 결과값으로 response를 `promise`객체로 리턴받는다
* 옵션 객체로 header, body, method등을 설정할 수 있다

```JS
    let promise = fetch(url, [options])
```

## Request 의 종류에 따른 메서드

* 조회, 추가, 수정, 삭제 작업을 할 수 있으며, 메서드를 통해 구분 한다

    * `GET` : 특정한 리소스를 가져오기 위한 메서드, `method`로 아무것도 지정해주지 않으면 `GET`메서드로 지정된다

    * `DELETE` : 지정한 리소스를 삭제

    ```JS
        fetch ('url', {
            // 옵션 객체
            method: 'DELETE',
        })
            .then((response) => response.text())          
            .then((result) => { console.log(result); 
        });
    ```

    * `POST` : 지정한 서버로 데이터를 전송

    ```JS
        fetch ('url/refridgerator/food', {
            method: 'POST',
            body: 
                name : 'milk',
                variable : 'diary product'
        })
            .then((response) => response.text())          
            .then((result) => { console.log(result); 
        });

    ```

    * `PUT` : 새로운 리소스를 생성하거나 수정

* Request는 head와 body영역으로 나눌 수 있는데 head에는 Request에 대한 부가정보, body에는 실제데이터가 존재한다
    * GET, DELETE 는 데이터를 바꾸는 작업이 아니기 때문에 body영역과는 무관하다

## Response 객체

* 서버로부터 받은 응답에 대한 본문을 얻으려면 응답을 다른 형태로 변환해야 한다
    * `response.text()` : 응답을 텍스트 형태로 반환
    * `response.json()` : 응답을 파싱하여 JSON 형태로 반환

## 직렬화와 역직렬화

* 직렬화 (Serialization)
    * Request를 보낼 때 자바스크립트의 객체를 JSON의 데이터로 바꾸는 작업
    * `stringify`메서드를 사용하여 직렬화

```JS
    const jsonData = JSON.stringify(javascriptObject);
```

* 역직렬화 (Deserialization)
    * Response를 받을 때 JSON의 데이터를 자바스크립트의 객체로 바꾸는 작업
    * `parse`메서드를 사용하여 역직렬화

```JS
    const javascriptObject = JSON.parse(jsonData);
```

## 비동기 함수

* `fetch` 메서드는 `promise` 객체가 반환되는 비동기 함수로, 요청에 대한 결과가 저장되는 것을 기다리지 않고 다른 작업을  이어 실행한다

```JS
    function getLocalHost () {
    console.log('함수 시작')                                            // 1
    const response =  fetch('url')                                  
        .then(function (response) {                                // 2 request에 대한 콜백함수 저장
        response.text()
            .then(function (result) {
            console.log(result);                                        // 4
        });
    }); 
    console.log('함수 종료');                                           // 3
    }

    getLocalHost(); // 함수시작 > 함수종료 > result
```
# Promise

* `fetch`함수의 결과로서 반환되는 객체
* `promise`객체는 리퀘스트 요청에 대한 3가지의 상태중 하나를 가진다 - pending(초기상태), fulfilled(작업 성공), rejected(작업 실패)
* `promise`가 fulfilled 상태일 시 작업성공의 결과를 함께가지며, rejected 시에는 작업실패결과를 함께 가진다

## then

* `Promise`의 메서드 `then`은 `Promise`객체를 반환한다
* 최대 두 개의 인수를 받을 수 있으며 첫번째 인수는 이행된 경우에 대한 콜백함수, 두번째 인수는 거부된 경우의 콜백함수이다
* 실행된 콜백의 리턴값에 따라 `then`의 반환값이 달라진다
    * `promise`객체를 리턴 : 콜백함수가 리턴한 값과 then메서드가 리턴한 값 동일
    * 값을 반환하는 경우 : 값 그대로 결과값
    * 값을 반환하지 않는 경우 : `undefined`
    * 오류가 발생하는 경우 : 오류값 그대로 결과값

## Promise chaining

* `then`메서드는 새로운 `promise`객체를 반환하고 선택적으로 연쇄에 사용할 수 있다

```JS
    const request = new Promise((yes, no)) = > {

    }
```

# 참조

* https://developer.mozilla.org/ko/
* https://ko.javascript.info/fetch