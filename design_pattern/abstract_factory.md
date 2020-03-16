[전체 패턴 보기](index.md)

## Abstract Factory

### 정의
`Provide an interface for creating families of related or dependent objects without specifying their concrete classes`
- 관련된 객체군을 생성하기 위한 인터페이스를 제공
- 플랫폼이나 제품군을 캡슐화시키는 계층
- Factory는 클래스들의 생성에 관련된 기능을 분리한다.  
  Abstract Factory는 이러한 Factory들을 추상화함으로써 공통된 부분은 고정시키고 구상 객체는 Abstract Factory를 상속한 Concrete Factory가 생성한다.
- 변경되지 않는 것 : 객체군을 생성하기 위한 인터페이스
- 확장 가능한 것 : 구상 객체군

### 적용 가능한 상황
- Factory를 사용하여 객체군을 생성하다가 다양한 종류의 구상 객체군을 생성해야하는 경우
  - 앱을 다양한 플랫폼(OS, DB, etc)에 이식시키기 위해서는 플랫폼 디펜던시(windowing system, OS, DB, etc.)를 캡슐화해야한다.
    이러한 플랫폼 캡슐화를 사전에 고려하지 않아서 #ifdef가 코드에 증식하기 시작한다.
- Factory Method나 Prototype로 객체를 생성하다가 객체군을 생성해야 하는 경우

### 다른 패턴과의 관계
- Abstract Factory 클래스는 Factory Method나 Prototype을 사용하여 구현할 수 있다.

### 예제
#### 처음의 코드
```c++
#include <iostream>

using namespace std;

class Shape
{
  public:
	virtual void draw() = 0;
};

class LinuxCircle : public Shape
{
  public:
	void draw() { cout << "LinuxCircle\n"; }
};

class Person
{
  public:
	void draw()
	{
		Shape *face = new LinuxCircle();
		face->draw();
        Shape *eyes[] = {new LinuxCircle(), new LinuxCircle()};
        eyes[0]->draw();
        eyes[1]->draw();
	}
};

int main()
{
	Person *c = new Person();
	c->draw();
}
```
Linux용으로 짜둔 위와 같은 코드가 있다고 하자. 보면 알겠지만 사람을 그리겠다고 하고 원으로 얼굴과 눈 2개를 그렸다.  
코드란 변화하기 마련이므로 다음과 같은 변화가 생길 것이다.  

1. Window에서 돌아가게 해주세요.
2. 삼각형으로 코 그려주세요.

#### Window에서 돌아가게 해주세요: #ifdef
```c++
#include <iostream>

#define LINUX

using namespace std;

class Shape
{
  public:
	virtual void draw() = 0;
};

class LinuxCircle : public Shape
{
  public:
	void draw() { cout << "LinuxCircle\n"; }
};

class WindowsCircle : public Shape
{
  public:
	void draw() { cout << "WindowsCircle\n"; }
};

class Person
{
  public:
	void draw()
	{
#ifdef LINUX
		Shape *face = new LinuxCircle;
#else
		Shape *face = new WindowsCircle;
#endif
		face->draw();
#ifdef LINUX
		Shape *eyes[] = {new LinuxCircle, new LinuxCircle};
#else
		Shape *eyes[] = {new WindowsCircle, new WindowsCircle};
#endif
		eyes[0]->draw();
		eyes[1]->draw();
	}
};

int main()
{
	Person *c = new Person();
	c->draw();
}
```
C의 전처리기를 좀 사용해본 솜씨다. 사실 2번정도 사용하기엔 저 방법도 좋을 수 있다. 하지만 100번 이상 사용하기엔 너무 고통스럽다.  
Factory Method를 사용하면 고통이 좀 줄어들 수 있다.

#### Window에서 돌아가게 해주세요: Factory Method
```c++
#include <iostream>

#define LINUX

using namespace std;

class Shape
{
  public:
	virtual void draw() = 0;
};

class LinuxCircle : public Shape
{
  public:
	void draw() { cout << "LinuxCircle\n"; }
};

class WindowsCircle : public Shape
{
  public:
	void draw() { cout << "WindowsCircle\n"; }
};

class CircleFactoryMethod
{
  public:
	virtual Shape *create_circle() = 0;
};

class LinuxCircleFactoryMethod : public CircleFactoryMethod
{
  public:
	Shape *create_circle() { return new LinuxCircle(); }
};

class WindowsCircleFactoryMethod : public CircleFactoryMethod
{
  public:
	Shape *create_circle() { return new WindowsCircle(); }
};

class Person
{
	CircleFactoryMethod *circleFactoryMethod;

  public:
	Person(CircleFactoryMethod *c)
	{
		circleFactoryMethod = c;
	}
	void draw()
	{
		Shape *face = circleFactoryMethod->create_circle();
		face->draw();
		Shape *eyes[] = {circleFactoryMethod->create_circle(), circleFactoryMethod->create_circle()};
		eyes[0]->draw();
		eyes[1]->draw();
	}
};

int main()
{
	CircleFactoryMethod *circleFactoryMethod;
#ifdef LINUX
	circleFactoryMethod = new LinuxCircleFactoryMethod();
#else
	circleFactoryMethod = new WindowsCircleFactoryMethod();
#endif
	Person *c = new Person(circleFactoryMethod);
	c->draw();
}
```
객체의 생성을 subclass로 지연시키는 Factory Method를 이용하여 #ifdef를 main함수 한 곳에서만 사용하도록 하였다.  
만약 #ifdef가 적은 경우에는 오히려 비효율적일 수도 있다. 하지만 #ifdef가 많고 Linux와 Windows외에 추가적인 os로 확장이 될 것이 예상된다면 좋은 선택일 것이다.  

#### 삼각형으로 코 그려주세요 : 2개의 Factory Method
```c++
#include <iostream>

#define LINUX

using namespace std;

class Shape
{
  public:
	virtual void draw() = 0;
};

class LinuxCircle : public Shape
{
  public:
	void draw() { cout << "LinuxCircle\n"; }
};

class LinuxTriangle : public Shape
{
  public:
	void draw() { cout << "LinuxTriangle\n"; }
};

class WindowsCircle : public Shape
{
  public:
	void draw() { cout << "WindowsCircle\n"; }
};

class WindowsTriangle : public Shape
{
  public:
	void draw() { cout << "WindowsTriangle\n"; }
};


class CircleFactoryMethod
{
  public:
	virtual Shape *create_circle() = 0;
};

class LinuxCircleFactoryMethod : public CircleFactoryMethod
{
  public:
	Shape *create_circle() { return new LinuxCircle(); }
};

class WindowsCircleFactoryMethod : public CircleFactoryMethod
{
  public:
	Shape *create_circle() { return new WindowsCircle(); }
};

class TriangleFactoryMethod
{
  public:
	virtual Shape *create_triangle() = 0;
};

class LinuxTriangleFactoryMethod : public TriangleFactoryMethod
{
  public:
	Shape *create_triangle() { return new LinuxTriangle(); }
};

class WindowsTriangleFactoryMethod : public TriangleFactoryMethod
{
  public:
	Shape *create_triangle() { return new WindowsTriangle(); }
};

class Person
{
	CircleFactoryMethod *circleFactoryMethod;
    TriangleFactoryMethod *triangleFactoryMethod;

  public:
	Person(CircleFactoryMethod *c, TriangleFactoryMethod *t)
	{
		circleFactoryMethod = c;
        triangleFactoryMethod = t;
	}
	void draw()
	{
		Shape *face = circleFactoryMethod->create_circle();
		face->draw();
		Shape *eyes[] = {circleFactoryMethod->create_circle(), circleFactoryMethod->create_circle()};
		eyes[0]->draw();
		eyes[1]->draw();
        Shape *nose = triangleFactoryMethod->create_triangle();
        nose->draw();
	}
};

int main()
{
	CircleFactoryMethod *circleFactoryMethod;
    TriangleFactoryMethod *triangleFactoryMethod;
#ifdef LINUX
	circleFactoryMethod = new LinuxCircleFactoryMethod();
	triangleFactoryMethod = new LinuxTriangleFactoryMethod();
#else
	circleFactoryMethod = new WindowsCircleFactoryMethod();
	triangleFactoryMethod = new WindowsTriangleFactoryMethod();
#endif
	Person *c = new Person(circleFactoryMethod, triangleFactoryMethod);
	c->draw();
}
```
나쁘지 않다. FactoryMethod가 2개뿐이라면...
그런데 나중에 더 많은 도형들이 추가될 때 매번 Factory Method 클래스들을 추가하는 것은 번거로울 것이다.  
그래서 Abstract Factory를 사용한다.

#### 삼각형으로 코 그려주세요 : Abstract Factory
```c++
#include <iostream>

#define LINUX

using namespace std;

class Shape
{
  public:
	virtual void draw() = 0;
};

class LinuxCircle : public Shape
{
  public:
	void draw() { cout << "LinuxCircle\n"; }
};

class LinuxTriangle : public Shape
{
  public:
	void draw() { cout << "LinuxTriangle\n"; }
};

class WindowsCircle : public Shape
{
  public:
	void draw() { cout << "WindowsCircle\n"; }
};

class WindowsTriangle : public Shape
{
  public:
	void draw() { cout << "WindowsTriangle\n"; }
};


class AbstractFactory
{
  public:
	virtual Shape *create_circle() = 0;
	virtual Shape *create_triangle() = 0;
};

class LinuxAbstractFactory : public AbstractFactory
{
  public:
	Shape *create_circle() { return new LinuxCircle(); }
	Shape *create_triangle() { return new LinuxTriangle(); }
};

class WindowsAbstractFactory : public AbstractFactory
{
  public:
	Shape *create_circle() { return new WindowsCircle(); }
	Shape *create_triangle() { return new WindowsTriangle(); }
};

class Person
{
	AbstractFactory *factory;

  public:
	Person(AbstractFactory *f)
	{
		factory = f;
	}
	void draw()
	{
		Shape *face = factory->create_circle();
		face->draw();
		Shape *eyes[] = {factory->create_circle(), factory->create_circle()};
		eyes[0]->draw();
		eyes[1]->draw();
        Shape *nose = factory->create_triangle();
        nose->draw();
	}
};

int main()
{
	AbstractFactory *factory;
#ifdef LINUX
	factory = new LinuxAbstractFactory();
#else
	factory = new WindowsAbstractFactory();
#endif
	Person *c = new Person(factory);
	c->draw();
}
```
위의 경우와 같이 Abstract Factory를 객체군을 위한 Factory Method라고 이해할 수도 있다.  
만약 요구사항 2번째가 1번째보다 먼저 들어왔으면 어떻게 되었을까?  
Simple Factory를 이용하여 구상 객체군을 생성하게 한 뒤, Factory Method를 적용하여 다양한 os위에서 동작시켰을 것이다.  
그런 경우에는 Abstract Factory를 Simple Factory에 Factory Method를 적용한 것이라고 이해할 수도 있다.  
Abstract Factroy는 Prototype을 이용하여 구현할 수 있으니, Simple Factory를 추상화한 것이라고 이해하기로 했다.  
아마 Abstract Factory라는 이름이 여기에서 나왔을 것이다.  
