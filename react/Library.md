# React의 라이브러리

## ▶ zustand

* 설치방법
```bash
    npm i zustand
```

`zustand` 라이브러리는 react에서 사용할 수 있는 상태 관리 라이브러리 중 하나이다. 한 개의 중앙에 집중된 형식의 스토어 구조를 활용하며, 상태를 정의하고 사용하는 방법이 단순하다.

typeScript에서 `zustand`라이브러리의 `create`함수를 사용하려면 제너릭으로 `store`의 타입을 지정해주어야 한다.

```tsx
    import {create} from 'zustand';

    interface Count {
        num: number;
        increaseNum: () => void;
        decreaseNum: () => void;
    }
```

`create`함수를 사용하여 `creatStore`함수를 호출하여 상태를 생성하고 변경한다. `create`함수의 반환 데이터는 훅 함수를 반환하기에 `use`라는 이름의 함수명을 이용해야 한다. `create`함수의 콟백함수가 받는 `set`인자는 상태를 업데이트하는 기능을 한다.

```tsx
    const useCount = create<Count>((set) => {
        num: 0,
        increaseNum: () => set(state => ({...state, num: state.num + 1})),
        decreaseNum: () => set(state => ({...state, num: state.num - 1})),
    })

    function CountComponent () {
        const {num, increaseNum, decreaseNum} = useCount();

        return (
            <>
                <h1>{num}</h1>
                <button onClick={decreaseNum}>감소</button>
                <button onClick={increaseNum}>증가< button>
            </>
        )
    }
```

## ▶ react-router

```bash
    npm i react-router-dom
```

`react-router`은 react에서 라우팅을 구현하기 위한 라이브러리이다. 여러 환경에서 동작할 수 있는 여러 종류의 라우터 컴포넌트를 제공한다.

> 라우팅 : 사용자가 요청한 URL에 따라 해당 URL에 맞는 페이지를 보여주는 것

사용하기에 앞서 `src/index.tsx`파일에서 `<App />`를`<BrowserRouter>`으로 감싸주어야 한다. `<BrowserRouter>`란 페이지를 새로고침하지 않아도 주소를 변경하는것이 가능하도록 해주는 역할을 하는 컴포넌트이다. 

```tsx
    import { BrowserRouter } from 'react-router-dom';

    const root = ReactDOM.createRoot(
    document.getElementById('root') as HTMLElement
    );
    root.render(
    <React.StrictMode>
        <BrowserRouter>
            <App />
        </BrowserRouter>
    </React.StrictMode>
    );
```

### - \<Routes\>, \<Route\> 컴포넌트

* `<Routes>` : 여러 `<Route>`컴포넌트를 감싸고 규칙에 맞는 URL을 가진 `<Route>`하나를 렌더링 시켜준다
* `<Route>` : URL패턴에 따라 랜더링 하고자 하는 컴포넌트를 지정할 수 있다
    * `path` : 경로 지정 / `element` : 랜더링할 컴포넌트 지정 / `index` : 현재 경로의 기본 라우터 지정

```tsx
    import { BrowserRouter } from 'react-router-dom';

    function App() {
  return (
    <Routes>
        <Route path='/first:id' element={<FirstPage/>}>  
        <Route path='/second' element={<SecondPage/>}>
        <Route path='/third' element={<ThirdPage/>}>

        {/* 지원하지 않는 페이지로 이동하는 경우 */}
        <Route path='*' element={<h2>404 Error<h2>}>
    </Routes>
  );
}
```

### - \<Link\> 컴포넌트

* `<Link>` : 기존에 웹 페이지에서 링크를 보여줄 때 사용하던 `a`태그는 새로운 페이지로 전환되는데, 이와 달리 `<Link>`컴포넌트는 새로고침을 하지 않고 URL만을 변경한다

### - useNavigate 

`useNavigate`훅을 실행하면 페이지 이동을 할 수 있게 하는 `Navigator`함수를 반환한다. 특정 조건에 따라 URL을 변경하고자 할때 사용한다.

```tsx
    const navigator = useNavigate();
    const [count, setCount] = useState<number>(0);
    const onButtonClick = () => {
        if (count === 10) navigator("/바뀔 경로");
        setCount + 1)
    }
```
> `<Link>` versus `useNavigator` : `<Link>`는 클릭 시 바로 이동하는 로직 구현시 사용하고, `useNavigator`는 페이지 전환 시 추가적으로 처리해야하는 로직이 존재하는 경우에 사용한다.

### - \<Outlet\> 컴포넌트

부모 `<Route>`에 해당 컴포넌트가 요소로 등록되었을 때 자식`<Route>`의 요소가 해당 위치에 표시되도록 하는 컴포넌트

### - useLocation 훅 함수

현재 URL 및 위치의 `location`객체를 반환하며 `pathname`, `search`, `state`등에 접근이 가능하다. 주로 `pathname`에 따라 상태값을 변경하고 싶을 때 많이 사용한다

```tsx
    export default ThirdPage () {
        const {pathname} = useLocation();

        return (
            <>
                <h4 style={{color: 'blue'}}>Location : {pathname}</h4>
                <Outlet/>
            </>
        )
    }
```

### - useParams 훅 함수

`<Route>` URL 파라미터값을 리턴하는 훅, 파라미터 값을 URL을 통해 넘겨서 넘겨받은 페이지에서 사용할 수 있도록 해준다. 

`<Route>` 컴포넌트의 `path`속성에 매칭되는 동적 URL패턴에 따른 데이터를 받아온다. `path`속성 값에 `:id`를 넣어 데이터를 받아올 수 있다, `id`는 객체의 `key`값으로 다른 명칭으로도 만들 수 있다

```tsx
    export function FirstPage () {
        const {id} = useParams();

        return <h4>Params : {id}</h4>
    }
```

### - useSearchParams 훅 함수

현재 URL에 있는 쿼리 문자열을 읽을 때 사용하는 훅으로 쿼리 문자열에 대한 배열을 반환한다

```tsx
    export function SecondPage () {
        const [queryString] = useSearchParams();
        const time = queryString.get('time');

        return <h4>SearchParams : {time}</h4>
    }
```

# 참조 

* zustand
    * https://docs.pmnd.rs/zustand/getting-started/introduction
    * https://www.nextree.io/zustand/

* react-router
    * https://goddaehee.tistory.com/305
    * https://velog.io/@pkbird/React-Router-1
    * https://babycoder05.tistory.com/entry/React-Router-v6-%EC%9E%90%EC%A3%BC-%EC%93%B0%EB%8A%94-%ED%9B%85hook-%EC%A0%95%EB%A6%AC