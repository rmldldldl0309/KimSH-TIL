# 컴포넌트

컴포넌트는 리액트로 만들어진 앱을 이루는 최소한의 단위로, MVC의 뷰를 독립적으로 구성하여 재사용이 가능하며, 이를 통해 새로운 컴포넌트를 쉽게 만들 수 있다. 컴포넌트의 이름은 항상 대문자로 시작해야하며, JavaScript의 함수와 개념적으로 유사하다.

## 함수형 컴포넌트

컴포넌트를 가장 간단하게 정의하는 방법은 자바스크립트 함수를 작성하는 것이다.  

```jsx
    import React from 'react';
    
    export default function Celebrate() {
        return (
            <div>Congratulation!</div>
        )
    }
```
반드시 return 뒤에 반환 요소가 존재해야 한다. 하나의 요소만을 반환할 수 있으며, 만약 다수의 요소를 반환하고자 하면 해당 요소들을 묶어주는 부모요소가 존재해야 한다.

## 클래스형 컴포넌트

컴포넌트 구성 요소, 리액트 생명주기를 모두 포함하고 있다. 프로퍼티, state, 생명주기 함수가 필요한 컴포넌트를 만들 때 사용된다.

```jsx
    import React from 'react';
    
    export default class Celebrate extends React.Component {
        render() {
            return (
                <div>Congratulation!</div>
            )
        }
    }
```

## 프로퍼티 (props)
하위 컴포넌트에 상위 컴포넌트의 값을 전달(단방향)할 때 사용한다. 문자열을 전달하는 경우 `""`를 문자열 외의 값을 전달할 때에는 `{}`를 사용한다. 컴포넌트는 자체 props를 수정해서는 안된다. 컴포넌트가 리렌더링 되는 기준이다. 

```jsx
    // 부모 컴포넌트
    export default function Parents () {
        return (
            <div>
                <div>
                    <Child color="red" num={15}/>
                <div>
            </div>
        )
    }
```
```jsx
    // 자식 컴포넌트
    export default function Child (props) {
        return (
            <div>
                <h1 style={{color: props.color}}>{props.num}</h1>
            </div>
        )

    }
```
* 디스럭처링 유무
```jsx
    // 디스트럭처링 X
    export default function DistructuringO (props) {
        const color = props.color;
        const num = props.num;

        return //
    }

    // 디스트럭처링 O
    export default function DistructuringO ({color, num}) {

        return //
    }
```

## 상태 (state)

컴포넌트에서 동적인 값을 상태라고하며, 동적이 데이터를 다룰 때 사용된다. `props`와 `state`는 모두 렌더링 결과물에 영향을 주는 정보를 지니고 있으나, `props`는 매개변수처럼 컴포넌트에 전달되고 `state`는 컴포넌트안에서 관리된다. `useState`라는 함수로 상태를 선언할 수 있다.

```jsx
    export default function Person () {
        const [name, setName] = useState<string>('홍길동');
        const [age, setAge] = useState<number>(25);

        return (
            <>
                <h1>{name}</h1>
                <h1>{age}</h1>
            </>
        )
    }
```

* **상태변수는 반드시 상태변경함수를 통해 변경해야 리렌더링 된다**
```jsx
    export default function Example() {

        let [count, setCount] = useState<number>(0);
        let [temp, setTemp] = useState<number>();
        const [total, setTotal] = useState<number>(0);

        // 상태 변수는 상태변수 함수로 변경해야 리렌더링된다
        const onCountHandler1 = () => {
            setCount(count + 1)  
        };
        //  1씩 증가

        // 상태 변경 함수를 통해 함수 변경해도 바로 적용되는 것이 아니다. 
        const onCountHandler2 = () => {
            setCount(count+1);
            setCount(count+1);
        }
        // 1만 증가

        // 상태 변경 함수에 콜백함수 전달 시 상태 변경 작업 누적 적용
        const onCountHandler3 = () => {
            setCount((count) => count+1);
            setCount((count) => count+1);
        }
        // 2씩 증가

        // 변경된 상태를 사용하려면 임시 변수를 사용한다
        const onCountHandler4 = () => {
            temp = count + 1
            setCount(temp);                 // +1
            setTotal(count + 1 + temp);     // +2
        }

        return (
            <>
                <button onClick={onCountHandler3}>+</button>
                <h1>{count}</h1>
                <h1>{total}</h1>
                <hr />
            </>
        )
    }
```

> 상태가 객체 또는 배열일 때 요소에 대해 추가 또는 변경이 일어나도 실제 주소값이 변경되는 것이 아니기 떄문에 상태가 변경된것으로 인식하지 않는다. 이는 새로운 배열 혹은 객체를 생성하여 상태를 변경하는 것으로 해결이 가능하다

## 렌더링

렌더링이란 컴포넌트가 현재 `props`, `state`의 상태에 기초하여 UI를 어떻게 구성할지 요청하는 것을 의미한다. 프로퍼티나 상태가 변경되는 경우에 리렌더링이 일어난다.

###  조건부 렌더링

* `if`문을 이용한 조건부 렌더링

```jsx
    function UseIf ({age}: {age: number}) {

        if (age > 19) {
            return <h1>{age} = 성인</h1>
        }
        return <h2>{age} = 청소년</h2>
    }
```
* `&&`연산자를 이용한 조건부 렌더링

```jsx
    function UseAnd ({age}: {age: number}) {
        
        return (
            <h1>
                {age > 19 && "성인"}
                {age <= 19 && "청소년"}
            </h1>
        )
    }
```
* 삼항연산자를 이용한 조건부 렌더링

```jsx
    function UseAnd ({age}: {age: number}) {
        
        return (
            <h1>
                {age > 19 ? "성인" : "청소년"}
            </h1>
        )
    }
```

### 리스트 렌더링

`map()`을 사용하여 배열을 컴포넌트로 렌더링할 수 있다

```jsx
    interface Student {
        name: string;
        age: number;
    }

    function StudentListItem ({name, age}: Student) {
        return (
            <div>
                <h4>{name}</h4>
                <h1>{age}</h1>
            </div>
        )
    }

    function StudentList () {
        const student: Student[] = [   
            {
                name: '홍길동',
                age: 15,
            },
            {
                name: '이영희',
                age: 14,
            }
        ]

        const ex = student.filter(student => student.name === "홍길동");

        return (
            <>
                {/* 전체 추출 */}
                {student.map((item, index) => {
                    return <StudentListItem key={index} {...item}/>
                })}

                {/* 특정 데이터 추출 */}
                {asd.map (item => <StudentListItem key={item.name} {...item} />)}
            </>
        )

    }
```

# 참조

* https://ko.legacy.reactjs.org/docs/components-and-props.html, https://ko.legacy.reactjs.org/docs/conditional-rendering.html
* https://goddaehee.tistory.com/299, https://goddaehee.tistory.com/300
* https://www.freecodecamp.org/korean/news/how-to-use-props-in-react/
* https://ko.react.dev/learn/rendering-lists
