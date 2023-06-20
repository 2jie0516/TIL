# Spring Framework(2)  

## 스프링 컨테이너
```java
ApplicationContext applicationContext = new AnnotationConfigApplicationContext(AppConfig.class);
```

ApplicationContext 
- 스프링 컨테이너
- 인터페이스
- xml , 자바 두 가지 형식 지원

#### 스프링 컨테이너를 생성하는 법
- 구성 정보를 지정해준다. ex) AppConfig.class
- 자바 코드 혹은 XML로 설정 정보를 만들 수 있음

#### 어떻게 생성이 될까 ?
- 설정 클래스 정보를 활용해 스프링 컨테이너에 *빈 등록
- 스프링 컨테이너는 빈을 등록할 때 설정정보를 참고한다.

* 빈 이름은 메서드 이름을 활용한다.

#### 빈을 조회하는 법
1. ac.getBean(빈이름,타입)
- 빈 이름으로 조회
2. ac.getBean(타입)
- 빈 타입만으로 조회
3. ac.getBean(빈이름, 구체타임)
- 구체 타입으로 조회

* 구체타입으로 조회하면 유연성이 떨어짐

조회 대상 스프링 빈이 업으면 예외가 발생한다.

#### 상속 관계

부모 타입으로 조회하면 자식 타입도 함께 조회한다.

## Application Context

#### BeanFactory 와 Application Context의 차이

Application Context(AC) 는 BeanFactory 의 기능을 상속받아서 제공한다.
하지만 어플리케이션을 개발할 때는 Bean 관리 말고도 여러 기능이 필요하다.

ex) 
1. 국제화 기능
2. 환경 변수
3. 이벤트
4. 리소스 조회

이와 같은 기능을 제공하기 위해 AC 를 사용한다(빈 관리 + 부가 기능).

BeanFactory나 AC 를 스프링 컨테이너라고 한다.

## 설정 형식 

자바코드 , XML 등을 이용해서 설정 정보를 만들 수 있다.

#### 자바코드로 만드는 법  
```java
new AnnotationConfigApplicationContext(AppConfig.class);
```

#### XML 코드로 만드는 법  
```java
new GenericXmlApplicationContext("appConfig.xml");
```


## 싱글톤


#### 싱글톤 패턴이란?  

클래스의 인스턴스가 딱 1개만 생성되는 것을 보장하는 디자인 패턴

#### 싱글톤이 필요한 이유
웹에서 요청이 올 때마다 객체를 새로 만든다면 메모리 낭비가 심해진다.

해결책 : 객체를 하나만 만들고 공유하자 ! -> 싱글톤

#### 싱글톤 패턴의 문제점

1. 싱글톤 구현 코드의 복잡성
2. 클라이언트가 구체 클래스에 의존한다(DIP,OCP 위반).
3. 테스트 하기 어렵다.
4. 유연성이 떨어진다.
5. 내부 속성을 변경하거나 초기화하기 어렵다.
6. private 생성자로 자식 클래스를 만들기 어렵다.

#### 싱글톤 컨테이너

스프링은 따로 구현할 필요없이 싱글톤 패턴으로 관리한다.
따라서 싱글톤의 단점들을 보완할 수 있다.

스프링 컨테이너에서는 요청이 올때마다 객체를 생성하지 않고 기존 객체를 공유한다.

#### 싱글톤 방식의 주의점

싱글톤 객체는 stateless 하게 설계해야 한다 !!
- 가급적 읽기만 가능해야한다.
- 특정 클라이언트에 의존적인 필드가 있으면 안된다.
