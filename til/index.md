# Today I Learned
[상위 페이지로](../index.md)

## 190528
### Pedantic
`of or like a pedant.`  
pedant는 `a person who is excessively concerned with minor details and rules or with displaying academic learning.`, 즉 지나치게 규칙에 얽매이는 사람을 말한다.  
gcc의 pedantic 옵션은 ISO C, ISO C++ 규칙에 의거하여 경고를 해주는 옵션이다.  
[자세한 설명](https://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html)

## 190524
### Apparatus
```
1. the technical equipment or machinery needed for a particular activity or purpose.
2. a complex structure within an organization or system.
```
apparatus는 특정 활동이나 목적을 위해 필요한 기술적인 장비/기계류이다.  
정부 기관의 조직체를 의미하기도 한다.  

## 190523
### Geofence
`Geography + Fence`  
실제 위치에 기반해 가상의 경계나 구역을 만드는 기술  
위치정보에 기반한 광고나 배민의 경우 배달가능 여부를 판단하는데 사용  
  
ref)  
[itworld](http://www.itworld.co.kr/news/110361#csidxf935e45938d3942a2a9d1b8a849dc10)  
[우아한형제들 기술 블로그](http://woowabros.github.io/experience/2018/03/31/hello-geofence.html)  

## 190522
### Embodiment
`a tangible or visible form of an idea, quality, or feeling.`  
`embodiment of sth`은 sth의 전형, 화신이라는 의미이다.  

## 190521
### Borne
`carried or transported by the thing specified.`  
`-borne`은 -로 전달됨이라는 의미이다. `waterborne diseases`는 수인성 전염병을 의미한다.

## 190515
### De facto
`denoting someone or something that is such in fact.`  
'사실의'이라는 의미이다.  
널리 인정되는 비공식적 관습을 데 팍토 표준(de facto standard)이라고 한다.  
반의어로 데 유레(De jure)가 있다.  
`de facto standard(사실상 표준)` <-> `de jure standard(공식적 표준)`

## 190514
### Discipline
```
1. the practice of training people to obey rules or a code of behavior, using punishment to correct disobedience.
2. a branch of knowledge, typically one studied in higher education.
```
discipline이 훈육 외에도 지식 분야라는 의미가 있다. 따라서 `engineering discipline`은 공학 분야라는 의미이다.

### Exemplify
```
- be a typical example of.
- give an example of; illustrate by giving an example.
```
`전형적인 예가 되다`, `예를 들어 설명하다`라는 의미이다.

## 190513
### 2진수 8진수 숏코딩
[2진수 8진수](https://www.acmicpc.net/problem/1373)의 숏코딩 정답을 보고 바로 이해가 안되서 분석해보았다.
```c
char*p,c[1<<20]="00";main(){for(gets(c+2),p=c+strlen(c)%3;*p;p+=3)putchar(*p*4+p[1]*2+p[2]-32);}
```
  
일단 인덴트를 맞춰주고 필요한 헤더를 넣어주었다.
```c++
#include <stdio.h>
#include <string.h>

char *p, c[1 << 20] = "00";
int main()
{
	// gets는 unsafe해서 vs2015 이상에서는 바로 사용이 안되서 fgets로 치환
	for (fgets(c + 2, sizeof(c), stdin), p = c + strlen(c) % 3; *p; p += 3)
	{
		putchar(*p * 4 + p[1] * 2 + p[2] - 32);
	}
	return 0;
}
```
  
- gets와 putchar을 익숙한 scanf, printf로 바꿔주었다.
- scanf를 for문 전으로 이동시켰다.
- char *p는 for문에서만 사용되므로 for문 안으로 넣어주었다.
- p의 dereference를 p[0]으로 바꿔주었다.
- 배열 c의 길이를 문제의 조건인 1,000,000 + 1로 변환하였다.
- `p[0] * 4 + p[1] * 2 + p[2] - 32`의 경우 최적화를 위해 변경하진 않았다.

```c++
#include <stdio.h>
#include <string.h>

char c[1000001] = "00";
int main()
{
	scanf("%s", c + 2);
	for (char *p = c + strlen(c) % 3; p[0] != '\0'; p += 3)
	{
		// printf("%c", (p[0] - '0') * 4 + (p[1] - '0') * 2 + (p[2] - '0') + '0');
		// printf("%c", p[0] * 4 + p[1] * 2 + p[2] - 6 * '0');
		// printf("%c", p[0] * 4 + p[1] * 2 + p[2] - 256 - 32);
		printf("%c", p[0] * 4 + p[1] * 2 + p[2] - 32);
	}
	return 0;
}
```
  
코드를 간략히 설명하자면, 입력 스트링의 앞에 `00`을 추가하여 입력받는다.  
자리 수의 끝을 기준으로 3자리씩 자르는데, `00`이 추가되어있으므로 가장 큰 자리수도 3자리로 자를 수 있다.  
이진수 3자리의 값을 이용하여 8진수로 변환(`p[0] * 4 + p[1] * 2 + p[0]`)한 뒤 이를 char형으로 출력한다.  

## 190510
### Reasoning
`the action of thinking about something in a logical, sensible way.`  
Reasoning은 어떠한 것에 대해 논리적이고 합리적인 방법으로 생각하는 행동을 의미한다.  
한국어로는 추론으로 번역되며, 추론은 어떠한 판단을 근거로 삼아 다른 판단을 이끌어 냄을 의미한다.  
추론의 예로 연역추론(Deductive reasoning), 귀납추론(Inductive reasoning)이 있다.  
Reason이 이유라는 뜻을 가지고 있으니, Reasoning은 어떠한 것에 대한 이유를 만드는 것이라고 생각할 수 있다.  
따라서 `Reasoning about something`은 '어떤 것을 선택하는 것에 대한 이유를 합리적으로 제시하는 것' 정도로 이해할 수 있다.  

## 190509
### Topology
Topos는 그리스어에서 나온 단어로 위치라는 뜻이다. 따라서 토폴로지는 위치를 다루는 학문, 위상수학을 뜻한다.  
네트워크 토폴로지란, 노드들과 이에 연결된 회선들을 포함한 네트워크들의 배열이나 구성을 그림으로 표현한 것이다.(star, mesh, bus, etc...)  
알고리즘에서의 토폴로지컬 소트란, 유향 그래프의 버텍스를 엣지의 방향에 거스르지 않도록 나열하는 것이다.  
그래서 `어떤 구성요소들의 토폴로지`라고 쓰인다면, 구성요소들의 배치와 연결의 표현을 의미한다고 이해할 수 있다. 

## 190508
### I'd like(I would like)
 `~를 원한다, 했으면 좋겠다.`로 자신의 선호를 표현한다.  
`I'd like 명사`, `I'd like to 동사원형`의 형태로 사용한다.  
`want`의 경우 직접적이고 강한 어조이고 `would like`는 덜 직접적이고 공손한 어조이다.  
ex) I'd like two tickets to the 9:30 show.  
    I'd like to drink some beer.  

## 190507
### [Yoda Condtion](yoda_condition.md)

