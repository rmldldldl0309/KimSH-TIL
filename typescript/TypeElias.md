# 타입 엘리어스

타입 엘리어스는 새로운 커스텀 타입을 정의하는 방식으로 인터페이스와 유사하다

```typescript
    type Student = {
        name: string;
        age: number;
        birth?: string;
    }

    let student = {} as Student;
    student.name = 'Honggildong';
    student.age = 25;
    student.birth = '1999-01-01'
```
하지만 타입 엘리어스는 인터페이스와 달리 `extends`나 `implements`될 수 없다. 확장이 필요한 경우에는 인터페이스를 쓰는 것이 유리하고, 튜플이나, 유니온 타입을 사용해야 하는 경우에는 타입 엘리어스를 쓰는것이 좋다

* 인터페이스와 달리 타입 엘리어스는 원시값 유니온 타입, 튜플등을 타입으로 지정할 수 있다

```typescript
    // 유니온 타입
    type Uni = boolean | null;

    // 리터럴 타입
    type Num = 15;

    // 튜플
    type Tup = [number, string];

    // 객체 리터럴 타입
    type Obj = {name: 'gildong'};

    // 인터페이스
    type Job = Developer | Engineer | Teacher;
```

## ▶ 인터섹션 타입

타입 엘리어스를 이용하여 여러 타입을 모두 만족하는 하나의 타입을 만들어낼 수 있다. 

```typescript
    interface Person {
        name: string;
        age: number;
    }
    interface Student {
        name: string;
        studentId: number;
    }

    type Me = Person & Student;
    // Me 타입은 name, age, studentId 3가지의 속성을 가진다.
```

# 참조

* https://poiemaweb.com/typescript-alias
* https://joshua1988.github.io/ts/guide/operator.html#intersection-type