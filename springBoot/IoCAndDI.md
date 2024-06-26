# 제어의 역전 (IoC)

> IoC (Inversion of Control) : 제 3자에게 코드의 흐름이 위임되는 것

* 생성자에서 직접 생성하여 필드를 초기화하는 경우 (의존성 주입을 적용하지 않은 경우)
```java
    public class A {
        // ...
    }
```
```java
    public class Control  {
        private A a;
        
        public Control() {
            a = new A();
        }
    }
```
* 외부(Spring Container)에서 관리하는 객체를 가져와 사용 (의존성 주입이 적용된 경우)
```java
@Component
    public class A {
        // ...
    }
```
```java
    public class Control  {
        @Autowired
        private A a;
    }
```
어노테이션을 통해 스프링 컨테이너에 `Bean`을 등록하기만 하면, 스프링 컨테이너에서 `Bean`의 생명주기를 전부 관리해준다.

* 제어의 역전을 통하여 얻을 수 있는 것
    * 진행 흐름과 구체적인 구현을 분리하여 응집도를 높이고 결합도를 낮출 수 있다
    * 개발자가 비즈니스 로직에 집중할 수 있게 한다
    * 구현체 사이의 변경이 용이
    * 객체간의 의존성이 낮아진다

> Bean : 스프링 컨테이너에 의해 인스턴스화, 조립 및 관리되는 객체

#  의존성 주입 (DI)

> 의존성이란? : 객체를 생성 및 사용함에 있어 의존 관계가 있는 경우를 일컫는다.

DI는 객체를 직접 생성하는 것이 아닌 외부에서 생성 후 주입시켜 객체간의 관계를 동적으로 주입하여 유연성을 확보하고 결합도를 낮추는 방식이다. 

## DI 방식

### ▶ Setter 주입

`@Autowired`를 이용하여 `Setter`메서드를 주입하는 방식

```java
    public class SetterInjection {
        private Injection injection;

        @Autowired
        public void setInjection(Injection injection) {
            this.injection = injection;
        }
    }
```

### ▶ Field 주입

의존 관계 주입을 간단하게 할 수 있지만, 참조 관계를 눈으로 확인하기 어려우며, 순환 참조를 막을 수 없다.

```java
    public class FieldInjection {
        @Autowired
        private Injection injection;
    }
```

### ▶ 생성자 주입

스프링 공식에서 권장하는 주입 방식으로, 다른 방식들과 다르게 `final`키워드를 사용할 수 있다

```java
    public class ConstructorInjection {
        private Injection injection;

        public ConstructorInjection( Injection injection) {
            this.injection = injection;
        }
```
Lombok 라이브러리를 사용하면 `@RequiredArgsConstructor`어노테이션을 통해 생성자를 생략할 수 있다

```java
    @RequiredArgsConstructor
    public class ConstructorInjection {
        private Injection injection;
        }
```
<br/>

> `@RequiredArgsConstructor`어노테이션은 `final`키워드가 붙은경우에만 생성자를 생성해준다. `final`키워드를 사용하지 않는 경우 `@AllArgsConstructor`어노테이션을 사용한다.

# 참조

* https://docs.spring.io/spring-framework/reference/core/beans/dependencies/factory-collaborators.html#page-title
* https://backendcode.tistory.com/249
* https://shinsunyoung.tistory.com/133
* https://oneul-losnue.tistory.com/364
