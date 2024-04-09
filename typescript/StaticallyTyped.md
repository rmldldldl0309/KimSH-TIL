# 정적 타입 언어

정적타입 언어란 컴파일 시 변수의 타입이 결정되는 언어를 일컫는다. 정적타입 언어로는 대표적으로 `C`, `C++`, `C#`, `Java` 그리고 `TypeScript`등이 있다

## 타입 선언

`TypeScript`에서의 타입 선언은 변수명 뒤에 변수의 타입을 명시하는 것으로 가능하다. 이러한 타입의 선언은 타입체크를 가능하게 하여 개발자가 코드를 예측할 수 있도록 돕는다. <br/>`TypeScript`는 `ES6+`의 상위 확장이므로 `JavaScript`의 타입을 그대로 사용할 수 있으며, `TypeScript`만의 고유 타입 또한 존재한다.

```typescript
    // ▶ JS 와 공통적으로 존재하는 타입

    // number
    const num: number = 10;

    // string
    const name: string = '홍길동';

    // boolean
    const yes: boolean = true;

    // null
    const nul: null = null;

    // undefined
    const unf: undefined = undefined;

    // object
    const obj: object = {};

    // 외에 Symbol 타입이 존재한다

    // ▶ TypeScript에만 존재하는 타입

    // array
    const arr1: number[] = [1, 2, 3];
    const arr2: Array<number> = [4, 5, 6];

    // tuple : 고정된 요소수 만큼 타입을 미리 선언 후 배열을 표현
    let tuple: [number, string];
    tuple = [10, '십'];

    // enum
    enum Instrument {Piano, Guitar, Base, Drum}
    let myPosition: Instrument = Instrument.Piano;

    // any : 모든 타입 가능, 타입 추론 필요 X
    let value: any = 100;
    value = '100';

    // void
    const exFunc = (): void => {};

    // 외에 never타입이 존재한다
```
`TypeScript`의 타입은 대소문자 구분이 이루어진다.

```typescript
    // string : 원시 타입 문자열
    let example1: string;
    example1 = 'a';

    // String : 생성자로 생성된 String 래퍼 객체 타입
    let exmaple2: String;
    example2 = 'b';
    example2 = new String('b');
```

## 정적 타이핑

`TypeScript`는 정적 타이핑을 지원하는 언어이다. 변수 선언 시 할당된 값에 따라 사전에 타입을 명시적으로 선언 하여야 하며 선언한 타입에 맞는 값을 할당하여야 한다. 타입이 결정된 후 에는 타입을 변경할 수 없다

## 타입 추론

타입을 선언하지 않고 값을 할당하는 것이 가능한데, 이때는 할당된 값에 따라 타입이 동적으로 결정되고 이를 ***타입 추론***이라 한다

```typescript
    let value = 10; // number
    // value = '10' >  error
```

## 타입 캐스팅

`as`키워드를 통해 정의할 수 있다. 

```typescript
    interface Student {
        name: string,
        age: number
    }

    const schoolPresident = {} as Student;
    schoolPresident.name = '홍길동';
    schoolPresident.age = 18;
```

## 유니온 타입

서로 다른 두 개 이상의 타입들을 사용하여 만드는 것으로 조합에 사용된 타입 중 하나를 타입으로 가질 수 있다

```typeScript
    let uni: number | string;
    uni = 15;
    uni = '15';
```

## 리터럴 타입

지정한 리터럴 값만을 가질 수 있는 타입이다. 하나의 값만을 가질 수 있는 변수로 리터럴 타입 그 자체만으로는 그다지 유의미하지 않다. 유니온 타입과 같이 사용하는 것으로 유용한 개념들을 표현할 수 있게 된다.

### 문자열 리터럴 타입

```typescript
    type Color = "RED" | "GREEN" | "BLUE" ;

    const color1: Color = "RED"; // O
    const color2: Color = "PINK"; // Error: Type 'PINK' is not assignable to type 'Color'.
```

### 숫자형 리터럴 타입

```typescript
    type Color = 10 | 20 | 30 ;

    const color1: Color = 30; // O
    const color2: Color = 75; // Error
    
```

# 참조

* https://poiemaweb.com/typescript-typing
* https://www.typescriptlang.org/ko/docs/handbook/2/everyday-types.html
