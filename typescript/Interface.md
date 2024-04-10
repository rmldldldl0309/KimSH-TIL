# 인터페이스

일반적으로 인터페이스는 타입체크를 위해 사용된다. `ES6+`와는 다르게 `TypeScript`에서는 인터페이스를 지원하고 여러가지 범주에 대하여 약속을 정의할 수 있다.

약속을 정의할 수 있는 범위는 다음과 같다
- 객체의 스펙 (속성 및 속성의 타입)
- 함수의 파라미터
- 함수의 스펙 (파라미터, 반환타입 등)
- 배열과 객체를 접근하는 방식
- 클래스

## 변수의 타입으로 사용

인터페이스는 변수의 타입으로 사용이 가능하다. 인터페이스를 타입으로하여 선언한 변수는 반드시 해당 인터페이스를 준수하여야한다

```typescript
    interface Student {
        name: string;
        age: number;
        grauation: boolean;
    }

    let students: Student[] = [];

    // 함수의 파라미터로 사용
    function addTypeCheck(student: Student) {
        students = [...students, student]
    }
```

## 함수의 타입으로 사용

함수의 타입으로 사용할 수 있으며, 인터페이스 안에는 타입이 선언된 파라미터 리스트와 리턴타입을 정의한다

```typescript
    interface Multi {
        (num1: number, num2: number): number;
    }

    let multiplication: Multi;
    multiplication = function(n1: number, n2: number) {
    return n1 * n2;
    }

    console.log(multiplication(10, 20)); // 200
```

## 클래스의 타입으로 사용

`implements`를 인터페이스를 선언하면 해당 클래스는 반드시 지정한 인터페이스를 구현하여야 한다

```typescript
    interface StudentInfo {
        name: string;
        age: number;
        graduation: boolean;
    }

    class Student implements StudentInfo {
        constructor (
            public name: string,
            public age: number,
            public graduation: boolean
        ) {}
    }

    let student = new Student('홍길동', 16, false)
```

## 인터페이스 확장

클래스 뿐만 아니라 인터페이스간의 확장 또한 가능하다

```typescript
    interface Student {
        name: string;
    }
    interface Department extends Student{
        major: string;
    }

    let person = {} as Department
    person.name = '홍길동';
    person.major = 'mechanical';
```
## 선택적 속성

속성의 끝에 `?`를 붙히는 것으로 인터페이스에 정의되어 있는 속성을 사용하지 않아도 되도록 할 수 있다

```typescript
    interface instrument {
        type: string;
        price: number;
    }

    let bandIns = {
        type: 'guitar'
    };
```
## 덕 타이핑

`TypeScript`는 정적타입의 언어이지만 동적 타이핑의 한 종류인 **Duck Typing**의 특성을 가진다.
타입을 컴파일 단계에서 결정하면 **정적타이핑**, 런타임 단계에서 결정하면 **동적타이핑**이다. `TypeScript`는 컴파일 단계에서 타입을 결정하기 때문에 정적 타이핑이라고 한다. 다형성의 측면에서 보면 어떤 객체의 형태가 컴파일 단계에서 결정되면 **정적 다형성**, 런타임 단계에서 결정되면 **동적 다형성**이라 한다.
`TypeScript`는 컴파일 단계에서 실제로 지정된 타입인지 파악하지 않는 대신 런타임 단계에서 지정된 타입이 가지고 있는 변수와 메서드가 있는지 판단한다.

> "만약 어떤 새가 오리처럼 걷고, 헤엄치고, 꽥꽥거리는 소리를 낸다면, 나는 그 새를 오리라고 부를 것이다."

위의 문장처럼 어떤 새가 정말 오리인지의 여부를 판단하는 것이 아닌, 오리처럼 행동한다면 오리가 아닐리 없다고 생각하는 것을 **덕 타이핑**이다.

```typescript
    interface Student {
    name: string;
    age: number;
    }

    interface OfficeWorker {
    name: string;
    age: number;
    isGraduation: boolean;
    }

    const kim: Student = {
    name: 'gildong';
    age: 19;
    };

    const park: OfficeWorker = {
    name: 'younghi';
    age: 26;
    isGraduation: true;
    }

    function introduce({name, age}: Student): string {
    return `My name is ${name} and I'm ${age} years old.`;
    }

    console.log(introduce(park));
```
아래의 `introduce`함수에서는 `Student`타입을 매개변수로 받아 문자열을 리턴한다. 하지만 `OfficeWorker`타입을 매개변수로 받았음에도 실행됨을 알 수 있다. 

# 참조

* https://poiemaweb.com/typescript-interface
* https://joshua1988.github.io/ts/guide/interfaces.html#%EC%98%B5%EC%85%98-%EC%86%8D%EC%84%B1
* https://inpa.tistory.com/entry/TS-%F0%9F%93%98-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4-%F0%9F%92%AF-%ED%99%9C%EC%9A%A9%ED%95%98%EA%B8%B0
* https://sambalim.tistory.com/158