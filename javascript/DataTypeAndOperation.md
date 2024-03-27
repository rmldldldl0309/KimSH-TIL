# 데이터 타입

* 자바스크립트의 데이터 타입은 맥락에 맞춰 유연하게 변화
* 총 8가지의 데이터 타입이 존재
    * 기본형: Number, String, Boolean, undeifined, null, Symbol, Bigint
    * 참조형: object
* `var`, `let`, `const` 키워드를 이용하여 변수를 선언하는데, 어떤 형태의 데이터를 저장하느냐에 따라 변수의 타입이 결정된다
* `typeof`연산자를 사용하여 피연산자의 자료형을 나타내는 문자열을 반환할 수 있다

## 기본타입

### Number

* 자바스크립트에서 숫자 리터럴은 정수가 아닌 부동 수소점 값이다
* 다른 타입의 값일 경우 Number()함수를 통해 숫자로 형변환할 수 있다
* 일반적인 숫자외에 `Infinity`, `-Infinity`, `NaN`과 같은 특수 숫자 값이 존재한다

### BigInt

* `Number`가 안정적으로 나타낼 수 있는 최대치 2^53 - 1 보다 큰 정수를 표현 할 수 있다
* 정수 리터럴 끝에 n을 붙여 만들 수 있다

```java
    const bigInt 9007199254740992n;
```

### String

* `''`, `""`, `\`\`\`, 총 3개의 따옴표로 문자열을 묶어 사용할 수 있다
* 문자열은 유사 배열로 인덱스를 통해 접근할 수 있다
* 한번 정한 문자열은 변하지 않는다
* `${}`안에 변수나 표현식을 `\`\`\`로 감싸 넣으면 문자열 중간에 집어 넣을 수 있다

```java
    const car1 = 'sonata';
    const car2 = "avante";
    const car3 = `K5`

    for (index = 0; index < car1.length; index ++){
        console.log(car1[index]);
    }

    console.log(`내 차는 ${car2}` );
```

### Boolean

* `boolean`타입의 값이 요구될 때 조건식이나 불린 타입의 값 뿐만아니라 다른 타입의 값을 사용할 수 있다
* 참으로 볼 수 있는 값을 Truthy, 거짓으로 볼 수 있는 값을 Falsy라 한다
    * Falsy : false, null, undefined, NaN, 0, ''
    * Truthy : 나머지 모든 값 ({}, [] 포함)

### null

* 자바스크립트에서 `null`값은 존재하지 않는 값, 비어있는 값, 알수 없는 값을 나타낸다
* 자바스크립트에서는 대소문자를 구별하기 때문에 `null`은 Null, NULL등과 다르다
* `typeof`연산자를 이용했을 때 Object가 반환된다
    * https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/typeof#null

### undefined

* 변수 선언시에 값을 할당하지 않으면 자동으로 `undefined`가 할당되며, 이는 값이 할당되지 않은 상태를 의미한다
* 변수에 의도적으로 할당할 수 있으나 권장되지 않는다

## 참조타입 (객체 타입)

### 객체 생성

* `{}`를 이용하여 만들 수 있으며, `key : value`의 한 쌍으로 구성된 프로퍼티를 여러가지 넣을 수 있다
    * 키는 문자열이나 심볼, 값은 어느 자료형이던 상관 X
* 객체를 생성하는 방법으로는 `Object()`객체 생성자 함수 이용, 객체 리터럴 이용, 생성자 함수이용이 있다

```java
    let snack = {
        name: "whiteheim",
        make: "crown",
    }

    // Object 생성자 이용
    let objectValue = new Object();

    // 객체 리터럴 이용
    let objectValue = {};

    // 생성자 함수 이용
    function User(name, age) {
        this.name = name;
        this.age = age;
    };
    const user1 = new User('ksh', 25);
```

### 객체 접근

* 점 표기법, 대괄호 표기법 두 가지를 이용하여 객체의 프로퍼티에 접근할 수 있다
 
 ```java
    let student = {
        'name' : 'ksh',
        'gender' : 'male',
        'school-name' : 'JEIL',
    }

    console.log(student.name);
    console.log(student["school-name"]);
 ```

* 객체가 소유한 프로퍼티에 새로운 값 할당 시 프로퍼티값 갱신
* 객체가 소유하지 않는 프로퍼티에 새로운 값 할당 시 새로운 프로퍼티가 동적으로 생성된다

```java
    student.name = 'kwm';
    console.log(student.name);
    
    student.age = 20;
    console.log(student.age);
```

* for in 문을 사용하여 객체에 포함된 모든 프로퍼티에 대해 루프 수행 가능

```java
    for (info in student){
    console.log(info, student[info])
    }
```

### Symbol

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

# 배열

## 배열 생성

### 배열 리터럴

* 값들을 쉼표로 구분하여 대괄호로 묶어 표기, 인덱스를 이용하여 접근이 가능하다

```java
    let rank = [
        'first', 'second', 'third', 'fourth', 'fifth' 
    ]
```

### 배열 생성자

* Array() 생성자 함수를 이용

```java
    const rank = new Array(5);
        console.log(rank);
```

## 배열 요소

### 요소 추가 및 삭제

* 인덱스를 사용하여 값을 할당할 수 있으며, 순서는 상관이 없다
* 값이 할당되지 않은 요소는 `undefined`값을 가진다

```java
   const refrigerator = [];

   refrigerator[1] = 'egg';
   refrigerator[10] = 'milk';

   console.log(refrigerator[1]) // egg
   console.log(refrigerator[2]) // undefined
```

* `delete`연산자를 사용하여 요소를 삭제할 수 있다, 이때 배열의 길이는 변함이 없다

```java
    console.log(refrigerator.length);   // 11
    delete refrigerator[1];
    console.log(refrigerator.length);   // 11
```

### 프로퍼티

* Array.length
    * 배열의 길이(요소의 개수)를 나타낸다
    * ***희소 배열*** : 배열 요소의 개수와 length 프로퍼티 값이 일치하지 않는 배열, 배열의 요소가 연속적이지 않다
    * 가장 큰 인덱스가 변했을 경우에만 변경된다

# 연산자

특이점에 대해서만 기재

## 논리 연산자

### 동등 연산자와 일치 연산자

* == : 동등 연산자, 피연산자의 타입이 다른 경우 타입 변환을 거친 후 비교
* === : 일치 연산자, 피연산자의 타입과 관계없이 비교

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

### typeof 연산자

* 피연자의 타입을 문자열 형태로 반환

|          |           | return      |
| -------- | --------- | ----------- |
| 기본타입 | 숫자      | 'number'    |
| 기본타입 | 문자열    | 'string'    |
| 기본타입 | 불린값    | 'boolean'   |
| 기본타입 | null      | 'object'    |
| 기본타입 | undefined | 'undefined' |
| 참조타입 | 객체      | 'object'    |
| 참조타입 | 배열      | 'object'    |
| 참조타입 | 함수      | 'function'  |

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

* https://developer.mozilla.org/ko/docs/Glossary/Type , https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Property_accessors
* https://ko.javascript.info/types , https://ko.javascript.info/object , https://ko.javascript.info/array
* https://prickle-textbook-12d.notion.site/1e8e3a82090f41a580f3c46a8c37e15b , https://prickle-textbook-12d.notion.site/f37f01f4efeb4b5382d06ba76a0f4ad2