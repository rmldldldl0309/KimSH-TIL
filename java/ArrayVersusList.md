# Array versus List

## Array (배열)

```java
    int[] arr = new int[5];
```

* 배열이란?

    * 같은 특성을 가지는 원소들이 순서대로 구성된 집합
        * 메모리 상에 데이터가 연속적으로 저장되는 순차 리스트에 해당

* 배열의 특징

    * 고정된 크기를 가지며, 선언 시 크기를 지정해야 함
        * 메모리가 낭비될 수 있음
        * 오버헤드가 거의 없다
    * Cache Hit Rate 가 높다
    * 식별자(index)를 통해 빠른 접근이 가능하다
        * 시간복잡도 = O(1)
    * 데이터 삭제 및 수정 시 연속적인 형태 유지를 위해 shift 연산이 필요하다
        * 시간복잡도 = O(n)

## List

* 리스트란?

    * 같은 특성을 가지는 원소들이 순서대로 구성된 집합
        * 메모리 상에 데이터가 비연속적으로 저장된 연결리스트에 해당
    * 배열의 문제점을 해결하기 위한 자료구조

* 리스트의 특징

    * 크기가 가변적이며 빈공간을 허용하지 않는다
    * 데이터들이 순차적으로 구성되어 있으나, 일반적으로 데이터가 메모리 상에 연속적으로 존재 X
    * Cache Hit Rate 가 낮다
    * 데이터에 접근할 때 순차접근방식을 사용
        * 시간복잡도 = O(n)
    * 데이터 삭제 및 수정 또한 순차접근방식을 사용한다
        * 시간복잡도 = O(n)



    > Cache Hit : CPU가 참조하고자 하는 메모리가 캐시에 존재하는 경우, 비율이 높을 수록 좋은 성능
    
    > 시간복잡도 : 컴퓨터 프로그램의 입력값 및 연산 수행 시간의 상관관계를 나타내는 척도

# ArrayList

```java
     ArrayList<String> arraylist = new ArrayList<String>(5);
```

## ArrayList란?

* 배열을 통해 리스트를 구현한 것

## ArrayList의 특징

* 내부적으로 `Object[]`배열을 이용하여 요소를 저장
* 배열을 이용하기에 인덱스를 이용하여 빠르게 요소에 접근이 가능
* 데이터 적재량에 따라 공간의 크기들 동적으로 사용가능
* 데이터 삽입/삭제 시 요소들의 위치를 자동으로 앞, 뒤로 이동시키기 때문에 동작이 느림

# 참조

- https://ongveloper.tistory.com/403
- https://inpa.tistory.com/entry/JAVA-%E2%98%95-ArrayList-%EA%B5%AC%EC%A1%B0-%EC%82%AC%EC%9A%A9%EB%B2%95
- https://jy-tblog.tistory.com/38