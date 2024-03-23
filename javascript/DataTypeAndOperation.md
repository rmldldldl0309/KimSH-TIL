# 데이터 타입

* 자바스크립트의 데이터 타입은 맥락에 맞춰 유연하게 변화

* 총 8가지의 데이터 타입이 존재
    * 기본형: number, string, boolean, undeifined, null, null, Symbol, Bigint
    * 참조형: object

## Symbol

* 객체에 속성을 추가할 때 고유한 키를 부여하여 다른 코드와 충돌하지 않도록 한다

```JS
    const myCar = Symbol('sonata');
    const yourCar = Symbol('sonata');

    // 어떤 값과 비교하여도 true값이 될 수 없다
    myCar === 'true';   
    myCar === 'false'
    myCal === 'avante';
    mayCar === yourCar;

```

## boolean

* `boolean`타입의 값이 요구될 때 조건식이나 불린 타입의 값 뿐만아니라 다른 타입의 값을 사용할 수 있다
* 참으로 볼 수 있는 값을 Truthy, 거짓으로 볼 수 있는 값을 Falsy라 한다
    * Falsy : false, null, undefined, NaN, 0, ''
    * Truthy : 나머지 모든 값 ({}, [] 포함)

## BigInt

* `Number`가 안정적으로 나타낼 수 있는 최대치 2^53 - 1 보다 큰 정수를 표현 할 수 있다

## typeof

* `typeof`연산자를 사용하여 피연샂나의 자료형을 나타내는 문자열을 반환

```JS
    typeof Symbol(); // symbol
    typeof [];       // Object
    typeof true;     // boolean

    function graduate{
        console.log('Congratulation!');
    }
    typeof funct     // function

    typeof null      // Object

```

> null의 경우 문자열로 `Object`가 반환된다.<br/> https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/typeof#null

# 연산자

## 논리 연산자

### AND & OR 연산

```JS
    console.log(true && 'milk');    // true
    console.log(false && 'milk');   // milk
    console.log(true || 'milk');    // milk
    console.log(false || 'milk');   // false

```

### null 병합 연산자

* 왼쪽 피연산자가 null 또는 undefined 일 때 오른쪽 피연산자를 반환하고, 그렇지 않으면 왼쪽 피연산자를 반환하는 논리 연산자

```JS
    const value1 = null ?? 'A';
    const value2 = undefined ?? 'B';
    const value3 = 'C' ?? 'D';

    console.log(value1);    // A
    console.log(value2);    // B
    console.log(value3);    // C

```

# 변수

* 데이터를 저장하는 공간에 이름을 부여한 것

## var

* `var`로 선언한 변수는 여러가지 문제가 존재하여 사용하지 않는다

### 호이스팅

* 인터프리터가 코드를 실행하기 전에 함수, 변수, 클래스등의 선언문을 해당 범위의 맨위쪽으로 올리는 것처럼 보이는 현상

```JS
    console.log(hi);    // 오류가 발생하는 것이 아닌 undefined가 출력
    var hi = 'Hello';
    console.log(hi)     // hello
```

### 중복선언 가능

* 코드가 길어질 경우 변수가 선언되는 경우가 생겨 문제가 발생할 수 있다

### 스코프(유효범위)

* `var`키워드로 선언한 변수는 함수 레벨 스코프를 지니기 때문에 for문이나 if문 안에서 선언했을때 지역변수가 아닌 전역변수로 취급된다

## const / let

* `var`이 가진 위와 같은 문제점들 때문에 현재는 `let`, `const` 키워드로 변수를 선언한다
* `const` : 재할당이 필요없는 경우에 사용
* `let` : 재할당이 필요한 경우 사용

* `const`, `let`로 선언한 함수들은 블록 레벨 스코프를 가진다

```JS
    const sum = 0;

    function sum(x, y) {
    const sum = x + y;

    return sum;
    }

    if (sum(3, 3) > 5) {
    const sum = 7 + 8; 
    }
    
    console.log(sum); //0
```

# Reference

* https://developer.mozilla.org/ko/
* https://prickle-textbook-12d.notion.site/6c89fd9693e648aa9db794aab2832408