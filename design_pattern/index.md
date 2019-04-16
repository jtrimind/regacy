## Index

|            | Creational patterns                     | Structural patterns           | Behavioral patterns                                  |
|------------|-----------------------------------------|-------------------------------|------------------------------------------------------|
| **Class**  | [Factory Method](factory_method.md)     | [Adapter(class)](adapter.md)  | [Interpreter](interpreter.md)                        |
|            |                                         |                               | [Template Method](template_method.md)                |
| **Object** | [Abstract Factory](abstract_factory.md) | [Adapter(object)](adapter.md) | [Chain of Reponsibility](chain_of_responsibility.md) |
|            | [Builder](builder.md)                   | [Bridge](bridge.md)           | [Command](command.md)                                |
|            | [Prototype](prototype.md)               | [Composite](composite.md)     | [Iterator](iterator.md)                              |
|            | [Singleton](singleton.md)               | [Decorator](decoartor.md)     | [Mediator](mediator.md)                              |
|            |                                         | [Facade](facade.md)           | [Memento](memento.md)                                |
|            |                                         | [Flyweight](flyweight.md)     | [Observer](observer.md)                              |
|            |                                         | [Proxy](proxy.md)             | [State](state.md)                                    |
|            |                                         |                               | [Strategy](strategy.md)                              |
|            |                                         |                               | [Visitor](visitor.md)                                |

### Creational patterns
- [Abstract Factory](abstract_factory.md) : 클라이언트에서 구상 클래스를 지정하지 않으면서도 일군의 객체를 생성
- [Builder](builder.md) : 객체 생성과 표현을 분리
- [Factory Method](factory_method.md) : 생성할 구상 클래스를 서브클래스에서 결정
- [Prototype](prototype.md) : 복제되기 위한 완전히 초기화된 인스턴스
- [Singleton](singleton.md) : 딱 한 객체만 생성

### Structural patterns
- [Adapter](adapter.md) : 객체를 감싸서 다른 인터페이스를 제공
- [Bridge](bridge.md) : 객체의 인터페이스와 구현를 분리
- [Composite](composite.md) : 클라이언트에서 객체 컬렉션과 개별 객체를 똑같이 다룸
- [Decorator](decoartor.md) : 객체를 감싸서 새로운 행동을 제공
- [Facade](facade.md) : 일련의 클래스에 대해서 간단한 인터페이스를 제공
- [Flyweight](flyweight.md) : 효율적인 공유를 위한 잘 나눠진 인스턴스
- [Proxy](proxy.md) : 객체를 감싸서 그 객체에 대한 접근을 제어

### Behavioral patterns
- [Chain of Reponsibility](chain_of_responsibility.md) : 연쇄적으로 객체들에게 요청을 전달하는 방법
- [Command](command.md) : 요청을 객체로 감쌈
- [Interpreter](interpreter.md) : 프로그램에서 언어요소를 포함하는 방법
- [Iterator](iterator.md) : 컬렉션이 어떤 식으로 구현되었는지 드러내진 않으면서도 컬렉션 내에 있는 모든 객체에 대해 반복 작업을 처리
- [Mediator](mediator.md) : 클래스들 간의 간결한 커뮤니케이션을 정의
- [Memento](memento.md) : 객체의 내부상태를 캡쳐하고 복원
- [Observer](observer.md) : 상태가 변경되면 다른 객체들한테 연락
- [State](state.md) : 상태를 기반으로 한 행동을 캡슐화한 다음 위임을 통해서 필요한 행동을 선택
- [Strategy](strategy.md) : 교환 가능한 행동을 캡슐화한 다음 위임을 통해서 필요한 행동을 선택
- [Template Method](template_method.md) : 알고리즘의 개별 단계를 구현하는 방법을 서브클래스에서 결정
- [Visitor](visitor.md) : 클래스의 변경없이 새로운 오퍼레이션을 정의

## Reference
- [SourceMaking](https://sourcemaking.com/design_patterns)
- [Wikipedia](https://en.wikipedia.org/wiki/Software_design_pattern)
- Head First Desgin Patterns

