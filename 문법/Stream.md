# JAVA Stream

## 스트림이란?

스트림은 "데이터의 흐름"이다.
1. 배열 또는 컬렉션 인스턴스에 함수 여러개를 필터링하고 가공할 수 있다.
2. 람다를 이용해서 코드의 양을 줄이고 간결하게 표현할 수 있다.
3. 병렬 처리가 가능하다.

스트림의 단계 
1. 생성 : 스트림 생성  
2. 가공 : 필터링 , 맵핑
3. 결과 : 최종 결과 도출

과정 요약
스트림 생성 -> 맵핑 -> 필터링 -> 결과 만들기

## 생성하기
#### 배열 / 컬렉션 / 빈 스트림
1. 배열 스트림
3. 컬렉션 스트림
3. 빈 스트림

배열 , 컬렉션을 이용하여여 스트림을 만들 수 있고 비어있는 (null) 스트림도 만들 수 있다.

#### Stream.builder() / Stream.generate() / Stream.iterate()
Stream.builder()
- 빌더를 사용하여서 원하는 값을 직접적으로 넣을 수 있다.
Stream.generate()
- Supplier<T> 에 해당하는 람다로 값을 넣을 수 있다.
- 크기가 무한하기 때문에  최대크기를 지정해주어야한다.
Stream.iterate()
- 초기값과 해당 값을 다루는 람다를 이용하여 스트림에 들어갈 요소를 만든다.
  
#### 기본 타입형 / String / 파일 스트림
- 제네릭을 사용하지 않고 해당 타입의 스트림을  다룰 수 있다.
  range : 종료지점 포함 안됨
  ranged : 종료 지점 포함
이 외에도 문자열 스트림 , 파일 스트림 등을 만들 수 있다.

#### 병렬 스트림 / 스트림 연결하기
- parallel 메소드를 이용하여 병렬 스트림을 만들 수 있다.

- concat 메소드를 통하여 스트림을 연결할 수 있다.

 
## 가공하기

-  원하는 것만 뽑아내는 단계를 "가공"이라고 한다.

- 가공은 중간 단계에  이루어지는데 여러작업을 이어서 "체이닝"할 수 있다.


#### Filtering
- 조건에 맞는 스트림 내 요소들을 거른다.

- Predicate 인터페이스로 평가식을 받음

  
#### Mapping
- 스트림 내 요소들을 특정값으로 변환해줌

- 값을 변환하기 위한 람다를 인자로 받는다.


#### Sorting
- Compatator를 이용하여 정렬한다.
#### peek
- peek() 메소드를 이용하여 연산  결과에 영향을 미치지 않고 값 확인 가능


## 결과 만들기
#### Calculating
- 최대,최소 , 합 , 평균 값을 도출할 수 있다.

- ifPresent 메소드를 통하여 바로 Optional 처리 가능
#### Reduction
- 총 3가지의 파라미터를 받아서 결과를 만든다.

1. accumulator : 각 요소를 처리하는 계산  로직

2. identity : 계산 초기값

3. combiner : 병렬 스트림에서 나눠 계산한 결과를 하나로 합친다.


#### Collecting



Collectors.toList()

- 결과를 리스트로 변환한다

Collectors.joining()

- 결과를 하나의 스트링으로 이어붙인다.

Collectors.averageingInt()

- 결과값의 평균을 도출한다.

Collectors.summingInt()

- 결과값의 합을 도출한다.

Collectors.summarizingInt()

- 결과값의 평균과 합을 계산한다.

Collectors.groupingBy()

- 특정 조건으로 요소들을 그룹짓는다.

Collectors.partitioningBy()

- 스트림 내 요소를 평가하여 true,false 그룹으로 나눈다.

Collectors.collectingAndThen()

- 결과를 collect한 이후에 추가 작업이 필요할 때 사용한다.

Collector.of()

- 필요한 로직을 직접 만듦

#### Matching

anyMathch

- 하나라도 만족하는가?

allMatch

- 모두 만족하는가?

noneMatch

- 모두 만족하지 않는가?




