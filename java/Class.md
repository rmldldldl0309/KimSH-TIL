# 클래스

* 공통적 성질을 가진 대상들을 정의한 것, 정의된 속성 및 메서드를 이용하여 객체를 생성할 수 있다
* 객체의 상태를 나타내는 필드(field)와 객체의 행동을 나타내는 메소드(method)로 구성

* 클래스 선언 방법+
```java
    [acess modifier] class ClassName {
        // 필드
        // 메서드
    }
```

> access modifier (접근 제어자) : `public`, `private`, `protected`, default

> ClassName : 클래스의 이름은 관례에 따라 항상 대문자로 시작해야 한다

## 필드

* 해당 클래스의 객체가 가질 수 있는 정보나 상태를 정의 (=속성)
* 클래스 내부에 선언되어 클래스의 모든 객체에서 공유되거나 개별적으로 값을 가질 수 있음
* 선언된 위치와 선언자에 따라 구분이 가능하다
    * 클래스 변수 (static variable) : `static`키워드를 가지는 변수
    * 인스턴스 변수 (instance variable) : `static`키워드를 가지지 않는 변수
    * 지역 변수 (local variable) : 메서드나 생성자 블럭 내에 위치한 변수

* 변수 선언
```java
    class Example {
    static int classVariable = 1;   // 클래스 변수 선언
    int instanceVariable = 2;       // 인스턴스 변수 선언
    
    int method() {
    	int localVariable = 3;      // 지역 변수 선언
        return localVariable;
    }
}
```

## 메서드

* 클래스 안에 있는 함수를 지칭, 객체의 행동을 구현
* `static`키워드 유무에 따라 2가지로 구별가능, 
    * 클래스 메서드 : `static` O, 내에서 인스턴스 변수 사용 불가
    * 인스턴스 메서드 : `static` X

* 메서드 정의
```java
    accessModifier returnType methodName(parameters) {
        // 구현부
    }
```
> return type : 메서드가 반환하는 값의 타입, 없는 경우 `void`

> methodName : 메서드 이름은 관례에 따라 소문자로 시작

> parameter : 메서드가 받아들이는 입력값 (매개변수)


# 객체 지향 프로그램

* 객체 지향 프로그램에서는 모든 데이터를 객체로 취급

## 객체

* 클래스에 의해 생성되는 인스턴스
* 실제로 존재하는 것, 사물 또는 개념

* 객체 생성 방법
```java
    ClassName variable =  new ClassName();
```

> new : 인스턴스를 생성해주는 역할, heap영역(메모리영역)에 저장할 공간 할당받아 참조값을 객체에 반환 후 생성자 호출

## 인스턴스 변수 및 메서드 접근

```java
    referenceVariable.Variable;   // 변수 접근
    referenceVariable.Method();   // 메서드 접근
```
## 오버로딩

* 같은 클래스 내에 같은 이름의 메서드를 중복하여 정의해서 사용하는 것
* Overloading 구현을 위해서는 다음과 같은 조건을 만족해야 한다
    * 메서드의 이름은 동일하게
    * 매개변수의 타입 또는 타입이 달라야한다

```java
    public class OverloadingExample {

    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }

    public int add(int a, int b, int c) {
        return a + b + c;
    }
}

```

## 생성자

* 객체가 생성될 때 동적으로 인스턴스 변수를 초기화하기 위해 실행되는 메서드
* 다른 메서드와 같이 생성자 또한 오버로딩이 가능하다
* 자동으로 기본 생성자가 제공되며, 직접 생성자 입력 시 기본 생성자는 제공되지 않는다
* 생성자 이름은 클래스 이름과 반드시 동일
* 생성자는 new를 통해 객체를 생성할 때 객체당 한번 호출되며 반드시 호출된다

```java
    public class Cat {
        String species;
        String name;

        public Cat() {}

        public Cat(String species, String name) {
            this.species = species;
            this.name = name;
    }
}

```

> `this` : 현재 객체 또는 현재 클래스의 인스턴스를 가리키는 키워드, 클래스 내의 다른 메서드에서 인스턴스 사용하려면 `this`를, 클래스 내부에서 다른 생성자를 호출하려면 `this()`를 사용할 수 있다

```java
    Cat myCat = new Cat('페르시안 고양이', '덕배')
```



# 참조
- https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5OOP-%ED%81%B4%EB%9E%98%EC%8A%A4-%EB%AC%B8%EB%B2%95-%F0%9F%92%AF-%EC%B4%9D%EC%A0%95%EB%A6%AC#recentEntries
- https://www.tcpschool.com/java/java_class_intro
- https://doozi0316.tistory.com/entry/JAVA-5%EC%A3%BC%EC%B0%A8-%ED%81%B4%EB%9E%98%EC%8A%A4%ED%81%B4%EB%9E%98%EC%8A%A4-%EA%B0%9D%EC%B2%B4-new-%EB%A9%94%EC%86%8C%EB%93%9C-%EC%83%9D%EC%84%B1%EC%9E%90-this
- https://opentutorials.org/course/2517/14133
