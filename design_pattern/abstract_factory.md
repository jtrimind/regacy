[전체 패턴 보기](index.md)

## Abstract Factory

### 정의
`Provide an interface for creating families of related or dependent objects without specifying their concrete classes`
- 관련된 객체군을 생성하기 위한 인터페이스를 제공
- 플랫폼이나 제품군을 캡슐화시키는 계층

### 적용 가능한 상황
- 앱을 다양한 플랫폼(OS, DB, etc)에 이식시키기 위해서는 플랫폼 디펜던시를 캡슐화해야한다.
  이러한 플랫폼 캡슐화를 사전에 고려하지 않아서 #ifdef가 코드에 증식하기 시작한다.

### 다른 패턴과의 관계
- Abstract Factory 클래스는 Factory Method나 Prototype을 사용하여 구현할 수 있다.
