# 함수

* 자바스크립트에서 함수는 매개변수, 반환값으로 사용 등 변수처럼 다루어질 수 있다 (= 일급함수)

* 자바스크립트에서 함수를 생성하는 방법

    * 함수 선언문: `function`키워드를 사용하여 함수를 선언
        
    ```JS
        function sum(a, b) {
            return a + b;
        }
    ```

    * 함수 표현식 : 변수에 함수를 할당하여 선언

    ```JS
        let sum = function (a, b) {
            return a + b;
        }
    ```

## 매개변수와 인수

* 매개변수 (parameter) : 함수의 내부에서 해당 함수 로 전달된 값을 가리키기 위한 변수
* 인수 (argument) : 함수에 전달되는 값

```JS
    const func (parameter1, parameter2 = 'A') {
        console.log(parameter1, parameter2);
    };

    func(argument1)             // argument1 undefined
    func(argument2 undefined)   // argument2 A
```

* 함수도 매개변수 자리에 위치할 수 있다 (= 콜백함수)
* 매개변수에 값의 전달이 없을 시 `undefined`를 반환
* 매개변수에 기본 값을 할당했을 때 `undefined`를 전달받으면 기본 값을 출력한다

### argument 객체

* 함수 안에서 `argumnes` 객체를 사용하여 인덱싱을 통해 각 요소에 접근 할 수 있도록 할 수 있다
* 이

```JS
    function hello() {
    let word = '';

    for (index = 0; index < arguments.length; index++){
        word = word + arguments[index];
    }

    console.log(word);
    };

    hello('안', '녕'); // 안녕
    hello('안', '녕', '하', '세', '요');

```

* 배열처럼 인덱싱을 통해 각 요소에 접근이 가능하지만 배열의 메서드를 사용하지 못한다

### Rest Parameter

* `argument`와 다르게 인덱싱할 수 있을 뿐만 아니라 배열의 메서드를 자유롭게 사용할 수 있다

```JS
    function introduce(...arg) {
    for(index=1; index < arg.length; index++)
        console.log(arg[index])
    };

    introduce('1', '2', '3');

```

## 함수의 형태

### Callback Function

* 전달인자로 다른 함수에 전달되는 함수

### IIFE (즉시 실행 함수)

* 함수가 선언됨가 동시에 실행되는 함수

```JS
    (function () {
    console.log('Hi!');
    })();

```

### Arrorw Function

* 본문이 한줄인 함수를 작성할 때 유용
* 본문이 한줄이 아닌 경우 중괄호를 포함하여 화살표함수를 작성

```JS
    // 기본 형태
    const func = function(a, b, c) {
        return { 0: a, 1: b, 3: c };

    // 화살표 함수로 변환
    const func = (a, b, c) => ({ 0: a, 1: b, 3: c });
    }

```

## this

* `this`의 값은 웹브라우저에서 사용될 때는 전역객체, Window 객체를 가지며 객체의 메서드를 정의하기 위한 함수 안에서는 메서드를 호출한 객체를 가리킨다

```JS
    function printThis() {
        console.log(this.title);
    }

    const a = {
    title: 'a',
    printText: printThis,
    };

    const b = {
    title: 'b',
    printText: a.printThis,
    };

    a.printText();  // a
    b.printText();  // b, 

```

# 참조

* https://developer.mozilla.org/ko/
* https://ko.javascript.info/arrow-functions-basics
* https://ko.wikipedia.org/wiki/%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98_(%EC%BB%B4%ED%93%A8%ED%84%B0_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D)
* https://prickle-textbook-12d.notion.site/e598e465514a465f9a8a1d788390d117

