# zustand

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

# 참조

* https://docs.pmnd.rs/zustand/getting-started/introduction
* https://www.nextree.io/zustand/