# 훅 함수

Hook은 함수형 컴포넌트에서 React state와 생명주기 기능을 연동할 수 있게 해주는 함수이다. 클래스안에서 동작하지 않으며, 클래스 없이도 React를 사용할 수 있도록 해준다.

> 생명주기 : 컴포넌트의 랜더링이 시작되는 지점부터 끝나는 지점까지의 범위

## ▶ 규칙 

* 반드시 함수 컴포넌트내에서 호출되어야 하며, 만약 다른곳에서 호출하려면 그 함수는 반드시 훅 함수여야 한다
* 최상위에서만 Hook을 호출해야 한다. 반복문, 조건문, 중첩된 함수 내에서 Hook함수를 실행하지 않도록 해야한다

## ▶ 종류

### useState

`useState` 함수는 함수 컴포넌트 내에서 `state`를 사용할 수 있게끔 해주는 함수이다. `useState`함수는 `state`깂과 `state`값을 변경하는 함수를 배열로 반환해주기 때문에 주로 배열 구조 분해 할당을 활용하여 사용한다.

```tsx
    const [countdown, setCountdown] = useState<number>(10);

    const counting = () => {
        setCountdown(countdown ++;);
    }
```

### useEffect

`useEffect`함수는 컴포넌트가 렌더링 될 때마다 특정 작업을 수행할 수 있도록 해주는 함수이다. `mount`, `update`, `unmount` 단계에서 수행된다.

```tsx
    const [countdown, setCountdown] = useState<number>(10);

    useEffect(() => {
        // mount 단계에서 수행
        alert('mount');
        return () => {
            // unmount 단계에서 수행
            alert('unmount');
        }
    }, [{/* 스코프할 상태 배열 */}])
```

> 리액트가 처음으로 구성요소를 렌더링하고 초기 DOM을 빌드하는 되는 것을 mount라 하고, 끝나는 것을 unmount라 한다. 컴포넌트가 render될때는 mount과정을 거치고, props나 state의 변경으로 인한 render에서는 mount과정을 거치지 않는다.

### useRef

DOM객체를 직접 다루거나 렌더링 없이 값을 변경 혹은 저장하고자 할때 사용한다. useState와 달리 값이 변경될 때마다 렌더링이 일어나지않는다. ref의 참조객체는 `current`속성에 들어있다.

```tsx
        const inputBox = useRef<HTMLInputElement>(null);
    const onButtonClickHandler = () => {
        // null 또는 undefined가 아닌 상태에서만 작업을 수행해야 한다
        if(inputBox.current) inputBox.current.focus();
    };

    return (
        <>
            <input ref={inputBox} type="text" />
            <button onClick={onButtonClick}>Focus the input</button>
        </>
    )
```

### Custom Hook

함수명을 `use`로 시작하게 작성하여 커스텀 훅 함수를 만들 수 있다. 다른 훅 함수를 포함하여 작성할 수 있다.

* ex) `useState`를 포함하는 `Custom Hook`
```tsx
    export function useCounter(num = 0) {
        const [count, setCount] = useState<number>(num);

        function increment() {
            setCount(count + 1);
        }

        function decrement() {
            setCount(count - 1);
        }

        return {count, increment, decrease}
    }

    export default function Counting() {
        const counter = useCounter(0);

        return (
            <div>
                <h4>{counter.count}</h4>
                <button onClick={counter.decrement}>-</button>
                <button onClick={counter.increment}>+</button>
            </div>
        )
    }
```

# 참조

* https://ko.legacy.reactjs.org/docs/hooks-overview.html
* https://funveloper.tistory.com/34
* https://velog.io/@velopert/react-hooks
* https://ko.legacy.reactjs.org/docs/hooks-reference.html
*( https://ccomccomhan.tistory.com/273)