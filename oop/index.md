[Home](https://jtrimind.github.io/)

## Index
- [Object Oriented Programming vs. Procedural Programming](#object-oriented-programming-vs.-procedural-programming)
- [Dynamic Binding](#dynamic-binding)
- [Encapsulation](#encapsulation)
- [Polymorphism](polymorphism.md)
- [Abstarct Class vs. Interface](#abstarct-class-vs.-interface)

### Object Oriented Programming vs. Procedural Programming

| Procedural Programming                    | Object Oriented Programming           |
| ----------------------------------------- | ------------------------------------- |
| 프로그램은 함수로 나누어짐                | 프로그림은 클래스와 객체로 나누어짐   |
| 행위에 강조                               | 데이터에 강조                         |
| 현실 문제를 모델링하기에 부적합           | 현실 문제를 모델링하기에 적합         |
| 프로젝트가 복잡하다면 유지보수하기가 힘듦 | 프로젝트가 복잡해도 유지보수하기 쉬움 |
| 확장성이 낮은 프로그래밍 언어             | 확장성이 높은 프로그래밍 언어         |
| 생산성이 낮음                             | 생산성이 높음                         |
| 함수가 프로그래밍의 단위                  | 클래스가 프로그래밍의 단위            |
| Top-Down                                  | Botton-Up                             |

### Dynamic Binding
- Late binding, Dynamic linkage
- 런타임에 메서드를 호출한 객체나, 함수에 불려지는 인수에 의해 바인딩 됨.

### Encapsulation
- 객체의 일부 구성 요소를 직접적으로 접근하는 것을 제한한다.
- 데이터와 메소드를 묶는다.

### Abstarct Class vs. Interface
- Abstract Class는 공통적인 기능을 하는 객체들의 추상화하기 위해 사용된다.
- Interface는 객체가 공통적인 method를 가지고 있다는 것을 보장한다.

#### Reference
https://brunch.co.kr/@kd4/6

### Coupling vs. Cohesion
#### Coupling
- 요소가 다른 것과 얼마나 강하게 연결되어 있는지 나타내는 정도이다.
- 모듈 간의 관계의 척도이다.
- 느슨할 수록 좋다.
- Coupling이 강하다는 것은 연관된 클래스가 변경되면 더불어 변경해야 한다.

#### Cohesion
- 요소가 해당 기능을 수행하기 위해 얼마나 연관된 책임과 아이디어가 뭉쳐있는지 나타내는 정도이다.
- 모듈 내부의 관계의 척도이다.
- 높을 수록 좋다.
- Cohesion이 낮으면 가독성 및 재사용성이 낮다.
