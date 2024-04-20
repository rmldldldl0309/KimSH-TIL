# Axios

* 설치방법
```bash
    npm i axios
```

`Promise`기반의 HTTP 비동기 통신 라이브러리로 웹브라우저, Node.j 기반의 환경에서 동작한다

> `Promise` : JS에서 제공하는 비동기를 간편하게 처리할 수 있도록 돕는 객체이다. promise는 성공할수도, 실패할수도 있는데 성공한 경우 `resolve`함수를 호출하고, 실패하는 경우 `reject`함수를 호출한다

## ▶ axios 객체

`axios`객체는 http method에 해당하는 `get`, `post`, `patch`, `put`, `delete`등의 함수들을 포함한다. `URL`, `option`을 매개변수로 받으며 각각의 http method함수는 결과를 `promise`형태로 반환 한다.

* 사용 예제
```tsx
    export default function AxiosHTTPMethod1 () {

        axios.get('/user').then(response => {
            console.log(response.data);
        })
        .catch(error => {
            console.log(error);
        })

        axios.get('/user', {
            params:{
                'ID': '1234'
            }
        })

        axios.post('/user', {
            'name': 'honggildong',
            'age': 25
        })

    return <></>
    }
```
`response`객체는 `status`, `header`, `data`값을 포함하고 있다. 위의 코드에서 `then`작업을 통해 status code가 400, 500번대가 아닌경우에 `response`값을 받아온다
만약 status code가 400번대나 500번대인 경우 `catch`를 통해 `AxiosError`객체를 받아올 수 있다. 



