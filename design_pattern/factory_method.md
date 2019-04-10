[전체 패턴 보기](index.md)

## Factory Method

### 정의
`Define an interface for creating an object, but let subclasses decide which class to instantiate. The Factory method lets a class defer instantiation it uses to subclasses.(Gang of Four)`
- 객체를 생성하기 위한 인터페이스를 정의하되, 서브클래스가 어떤 인스턴스를 만들지 정함.  즉 Factory Method는 서브클래스가 인스턴스를 생성하도록 지연함
- virtual 생성자를 정의함

### 적용 가능한 상황
- 프레임워크가 다양한 앱들을 위한 아키텍처 모델을 표준화해야한다. 하지만 각각의 앱들은 자신의 도메인 객체를 정의하고 인스턴스를 생성할 수 있도록 허용해야한다.

### 다른 패턴과의 관계
#### vs. [Abstract Factory](abstract_factory.md)
 - Abstract Factory 클래스는 Factory Method로 구현되곤 한다.

#### vs. [Template Method](template_method.md)
 - Factory Method는 Template Method의 일종이다.

#### vs. [Prototype](prototype.md)
 - Factory Method는 상속을 사용하여 생성한다. Prototype은 delegation을 통해 생성한다.
 - Factory Method를 이용하여 사용하다가 Abstract Factory, Prototype, Builder로 진화하기도 한다.
 - Prototype은 서브클래스를 필요로 하지 않으나 초기화가 필요하다.  Factory Method는 서브클래스가 필요하나 초기화가 필요하지 않다.