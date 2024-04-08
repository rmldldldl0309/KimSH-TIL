# 디스트럭처링 (구조 분해 할당)

배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있도록 하는 표현식으로 필요한 데이터만 추출하여 사용할 수 있도록 한다

## 배열 디스트럭처링

### ES5

ES5에서의 배열 디스트럭처링은 아래와 같이 행해졌다

```JS
    let animal = [dog, cat, cow];

    let first_animal = animal[0];
    let second_animal = animal[0];
    let third_animal = animal[0];

    console.log(first_animal, second_animal, third_animal); // dog cat cow
```

### ES6+

ES6+의 배열 디스트럭처링은 각 요소를 배열의 인덱스를 기준으로 추출하여 변수 리스트에 할당하는 것이다.

```JS
    let animal = [dog, cat, cow];

    let [first_animal, second_animal, third_animal] = animal;

    console.log(first_animal, second_animal, third_animal); // dog cat cow
```

배열 디스트럭처링을 위해서는 할당 연산자 왼쪽에 배열 형태의 변수 리스트가 필요하다

```JS
    let book1, book2 = 'Mobidic', book3;

    [book1, , book3] = ['Three_Kingdoms', , 'Children of the Rune'];
    console.log(book1, book2, book3);   // Three_Kingdoms Mibidic Children of the Rune

    [book1, book2] = ['Three_Kingdoms', 'Robinhood'];
    console.log(book1, book2);          // Three_Kingdoms Robinhood
```
하나의 구조 분해 표현식으로 두 변수의 값을 교환할 수 있다

```JS
    let x = `10`;
    let y = `20`;

    [x, y] = [y, x];
    console.log(x + ' ' + y );  // 20 10
```

## 객체 디스트럭처링

### ES5

객체의 각 프로퍼티를 객체로부터 디스트럭처링하여 변수에 할당하기 위해서는 프로퍼티 키를 사용

```JS
    const instrument = {main_instrument: 'guitar', sub_instrument: 'piano'};

    const first = instrment.main_instrument;
    const second = instrument.sub_instrument;

    console.log(first, second); // guitar piano
```

### ES6+

ES6+의 객체 디스트럭처링은 각 프로퍼티를 프로퍼티 이름을 기준으로 추출하여 변수 리스트에 할당하는 것이다
객체 디스트럭처링을 위해서는 할당 연산자 왼쪽에 객체 형태의 변수 리스트가 필요하다

```JS
    const object = {major: 'electronic' ,minor: 'mechatronic'};

    const {major, minor} = object;

    console.log(major, minor);  // electronic mechatronic
```

중첩 객체의 경우

```JS
    const student = {
        name: 'kim',
        university: {
            department: 'computer',
            studentID: '12345678'
        }
    };

    const {university: {department}} = student;
    console.log(studentID); // 12345678
```