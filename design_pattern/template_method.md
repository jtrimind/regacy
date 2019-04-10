[전체 패턴 보기](index.md)

## Template Method

### 정의
`Defines the program skeleton of an algorithm in an operation, deferring some steps to subclasses`
- 알고리즘을 여러 단계로 분할하고, 서브클래스에서 구체화함
- 알고리즘의 구조를 바꾸지 않고 특정 단계만 서브클래스에서 재정의하도록 할 수 있음

### 적용 가능한 상황
- 다른 컴포넌트가 의미있는 부분에서 유사점을 가지는데, 공통된 인터페이스와 같이 재사용을 안하고 있다.
- 유사점에 변경이 있을 때 모든 컴포넌트들의 중복된 수정이 필요하다.

### 다른 패턴과의 관계
#### vs. [Strategy](stragtegy.md)
- Strategy는 Template Method와 세분성(granularity)를 제외하면 비슷하다.
- Template Method는 알고리즘의 부분을 달리하기 위해 상속을 이용하지만, Strategy는 전체 알고리즘을 달리하기 위해 delegation을 사용한다.
- Strategy는 각각의 객체들의 로직을 변경한다. Template Method는 전체 클래스의 로직을 변경한다.

#### vs. [Factory Method](factory_method.md)
- Factory Method는 Template Method의 생성 패턴 버전이다.