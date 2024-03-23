# 자바의 4대 특징

## 1. 상속 (Inheritance)

* 기존의 클래스에 기능을 추가하거나 재정의하여 새로운 클래스를 정의하는 것
* 상속을 통하여 코드 재사용, 확장성, 유지 보수가 용이한 설계를 가능하게 함
* 다중 상속은 다이아몬드 문제를 일으킬 수 있으므로, 단일 상속만을 허용

> 다이아몬드 문제 : 두 개 이상의 상위클래스가 동일한 메서드를 가질 때 어떤 메서드를 호출해야 할지 모호해지는 문제

### 클래스 상속

* `extends` 키워드를 사용

```java
    // 부모
    public class Parent{}
    // 자식
    public class Child extends Parent {}
```
### 부모 호출

* `super`/`super()`키워드를 이용하여 상위 클래스의 필드나 메서드에 접근
* 부모의 생성자도 호출이 가능하다

```java
    public class Furniture{
        Private String type;

        // 부모 생성자
        public Furniture(String type){
            this.type = type;
            this.price = price;
        }

        // 부모 메서드
        public void purchase (){
            System.out.println("가구 구매")
        }
    }

    public class Chair extends Furniture{
        Private int price;
        
        public class Chair(String type, int price){
            // 부모 생성자 호출
            super(type);
            this.price = price;
        }

        @Override
        public void purchase (){
            // 부모 메서드 접근
            super.purchase();
            System.out.println("의자 구매")
        }
    }

```
### 오버라이딩

* 부모 클래스의 메서드를 자식 클래스에서 재정의 하는 것
* 오버라이딩 규칙
    * 메서드 이름, 매개변수 리스트, 반환 타입은 같아야 한다
    * 상위 클래스 메서드 보다 더 좁은 범위의 접근제어자 사용 X
    * `final`로 선언된 메서드는 오버라이딩 불가
* `@Override`어노테이션을 사용하여 오버라이딩 메서드임을 명시


## 2. 캡슐화 (Encapsulation)

* 서로 연관되어 있는 속성과 기능들을 하나의 캡슐로 만들어 외부로부터 데이터를 보호하는 것
* 상세한 구현은 숨기고 오직 정의된 메서드를 통해서만 접근할 수 있도록 데이터를 은닉
* 객체 내부의 동작의 외부 유출을 최소화하여 객체의 자율성을 높이고 객체간 결합도를 낮출 수 있다

### 접근제어자

* 변수나 메서드의 사용 권한을 설정
* 종류 (아래로 갈수록 접근허용성 증가)
    * `private` : 해당 클래스 안에서만 접근 가능
    * `default` : 접근제어자를 설정하지 않았을 때 자동으로 설정, 동일한 패키지 안에서만 접근 가능
    * `protected` : 동일 패키지 또는 해당 클래스를 상속받은 클래스에서만 접근 가능
    * `public` : 모든 곳에서 접근 가능

### getter / setter 메서드

* `getter` : 객체의 속성 값을 반환하는 메서드
* `setter` : 객체의 속성 값을 설정 및 변경하는 메서드

```java
    public class Computer {
        private String maker;

        public String getMaker() {
            return maker;
        }

        public void setMaker() {
            this.maker = maker;
        }
    }

```

## 3. 추상화 (Abstration)

* 불필요한 사항들은 제거하고, 공통적인 속성과 기능을 추출하여 정의하는 것

### 추상 클래스

* `abstract`키워드를 사용하여 선언
* 추상 메서드는 선언부만 존재하고 구현부는 존재하지 않는다
* 인스턴스를 만들 수 없다
* 추상 클래스를 상속받는 하위 클래스는 추상 클래스에서 선언된 모든 추상 메서드를 반드시 구현해야한다
* 생성자를 가질 수 있지만 하위 클래스의 생성자에서 호출되는 용도로만 사용된다

```java
    abstract class Animal {
        abstract void cries();
    }

    // 하위클래스에서 추상 메서드 구현
    class Cat extends Animal {
        void cries() {
            Sysyem.out.println("Meow")
        }
    }

```

### 인터페이스

* `interface`키워드를 사용하여 정의하며, 클래스에서 `implements`키워드를 사용하여 인터페이스를 구현
* 모든 변수는 `public static final`로 선언된다
* 모든 메서드는 `public abstract`로 선언된다
* 다중 상속이 가능하다

```java
    public interface Animal {
        public static final string name = "동물";

        public abstract void cries();
    }

    public class Cat implements Animal {

        @Override
        Public void cries(){
            System.out.println("Meow");
        }
    }

```

## 4. 다형성

* 객체의 속성이나 기능이 상황에 따라 다른 역할을 수행할 수 있는 객체 지향의 특성
* 오버로딩이나 오버라이딩 / 업캐스팅, 다운캐스팅을 통해 실현된다

### 업캐스팅 / 다운캐스팅

* 업캐스팅 : 자식 클래스가 부모 클래스 타입으로 캐스팅 되는 것 

```java
    Parent p = new Child();
```

* 다운캐스팅 : 부모 클래스가 자식 클래스 타입으로 캐스팅 되는 것

```java
    Child c = (Child) p();
```


# 참조

- https://prickle-textbook-12d.notion.site/e00c4cbb06ca49539613e14542818b54
- https://xangmin.tistory.com/152
- https://www.codestates.com/blog/content/%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%8A%B9%EC%A7%95

* 오버라이딩   
    - https://caffeineoverflow.tistory.com/38
    - https://chanhuiseok.github.io/posts/java-1/

* 캡슐화
    - https://wikidocs.net/232

* 추상화
    - https://coding-factory.tistory.com/867

* 다형성
    - https://velog.io/@smallcherry/Java-UpCastingAndDownCasting
