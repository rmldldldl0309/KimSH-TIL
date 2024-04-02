# 제네릭(Generics)

제네릭은 클래스 내부에서 사용할 데이터 타입을 외부에서 지정하는 기법으로 이를 타입의 일반화라 한다. 변수를 선언할 때 변수의 타입을 지정하듯 제네릭은 객체에 타입을 지정해주는것이라고 볼 수 있다. 

## ▶ 사용시 이점

1. 여러 타입의 파라미터를 삽입하여 객체를 생성할 수 있기에 코드가 간결해지고, 재사용성이 높아진다
2. 잘못된 타입의 객체가 저장되는 것을 컴파일 시점에서 방지할 수 있어 실행 시간 오류를 줄일 수 있다
3. 미리 타입을 지정 및 제한하기 때문에 형 변환의 번거로움을 줄일 수 있다

## ▶ 제너릭 클래스

클래스 외부에서 데이터 타입을 지정하는 방식을 이용하며, 동적으로 데이터 타입을 변경할 수 있어 코드의 재사용성을 높일 수 있다


```java
    class NumberOneExpression<T> {
        private T expression;

        public T getExpression() {
            return expression;
        }

        public void setExpression (T expression) {
            this.expression = expression;
        }
    }
```
 
 * 클래스 외부에서 타입이 동적으로 지정된다
```java
    NumberOneExpression<String> english = new NumberOneExpression<>();
    english.setExpression("one");

    NumberOneExpression<Integer> number = new NumberOneExpression<>();
    number.setExpression(1);
```

## ▶ 제네릭 메서드

메서드의 선언부에 `<T>`가 선언된 메서드를 제네릭 메서드라 명명한다. 위의 코드처럼 클래스의 타입 파라미터를 받아 사용하는 메서드는 일반 메서드이며, 제네릭 메서드와는 별개이다. 제네릭 메서드에 선언된 타입 파라미터는 클래스의 타입 파라미터와 같은 것이 아닌 메서드에서 독립적으로 이용하는 파라미터이다.

```java
    class InstrumentShop<T, M> {
        private T instrument;
        private M price;    

        InstrumentShop(T instrument, M price){
            this.instrument = instrument;
            this.price = price;
        }

        // 일반 메서드
        public T getInstrument() {
            return instrument;
        }
        public void setInstrument(T instrument) {
            this.instrument = instrument;
        }
        // 일반 메서드
        public T getPrice() {
            return instrument;
        }
        public void setprice(M price) {
            this.price = price;
        }

        // 제너릭 메서드
        public static <T, M> boolean priceCompare(InstrumentShop<T, M> instrument1, InstrumentShop<T, M> instrument2) {
            boolean instrumentCompare = instrument1.getInstrument().equals(instrument2.getInstrument());
            boolean priceCompare = instrument1.getPrice().equals(instrument2.getPrice());
            return instrumentCompare && priceCompare;
        }
    
    }
```

```java
    InstrumentShop<String, Integer> instrument1 = new InstrumentShop<String, Integer>("guitar", 500000);
    InstrumentShop<String, Integer> instrument2 = new InstrumentShop<>("piano", 1200000);
    boolean result = InstrumentShop.priceCompare(instrument1, instrument2);
```

## ▶ 제너릭 타입 파라미터

위의 코드들에서 보이는 `<T>`나 `<T, M>`같이 꺽쇠괄호 사이에 위치하는 것을 타입 파라미터라 한다. 제네릭 클래스 선언문 부분에서 타입 파라미터가 지정된 타입으로 변환되어 클래스의 타입이 동적으로 정해진다.

### - 제한된 타입 파라미터

* `extends`키워드를 사용하는 것으로 제한된 타입 파라미터를 선언할 수 있다. 이를 통해 클래스나 인터페이스의 하위타입들만 받을 수 있도록 파라미터 범위를 제한할 수 있다

```java
    class Example<T extends X>{
        // ...
    }
```

* 두 개이상의 타입 파라미터를 제한하는 경우에는 `&&`를 통해 다중 제한이 가능하다

```java
    class Example<T extends X && Y>{
        // ...
    }
```

### - 와일드 카드를 이용한 타입 파라미터

알 수 없는 타입을 의미하는 `?`키워드를 통해 파라미터 타입을 미정을 둘 수 있다

* 와일드 카드의 종류
    * `?`: 모든 타입이 될 수 있다
    * `? extends T` : T 또는 T의 하위 타입
    * `? super T` : T 또는 T의 상위 타입

# 참조

* https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EC%A0%9C%EB%84%A4%EB%A6%ADGenerics-%EA%B0%9C%EB%85%90-%EB%AC%B8%EB%B2%95-%EC%A0%95%EB%B3%B5%ED%95%98%EA%B8%B0#%ED%83%80%EC%9E%85_%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0_%EC%A0%95%EC%9D%98
* https://hahahoho5915.tistory.com/69
* https://www.nextree.io/generic-ihaehagi/
* https://www.tcpschool.com/java/java_generic_concept
* https://f-lab.kr/insight/understanding-java-generics?gad_source=1&gclid=Cj0KCQjw2a6wBhCVARIsABPeH1sbBHC6n5Qlr4XwXPJR-zkqgHjsZuoWi6l0iL1n-ClmR3IF5Qy930oaAm-tEALw_wcB