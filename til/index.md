# Today I Learned
[상위 페이지로](../index.md)

## 200116
### have a lot on one's plate
해야 할 일이 산더미처럼 있다.  
ex) Now I have a lot on my plate. So please don't bother me.  

## 200114
### nerve-racking
안절부절못하게 하는  
ex) It was very nerve-racking.

### git fetch --prune
remote 저장소에서 지워진 브랜치를 로컬에 반영한다

## 200113
### The early bird cathes the worm
일찍 일어나는 새가 벌레를 잡는다.

### ModuleNotFoundError: No module named 'tensorflow.examples.tutorials'
[텐서플로우 깃허브](https://github.com/tensorflow/tensorflow)를 받아서 `tensorflow/example/tutorials` 폴더를 `anaconda3/lib/python3.7/site-packages/tensorflow_core`로 복사한다.  
`python -m site` 명령어로 site-packge 위치를 알 수 있다.

## 191231
### 볼린저 밴드(Bollinger Bands)
#### 구성요소
- 중심선 : 이동평균선
- 상한선 : 이동평균선 + 2σ
- 하한선 : 이동평균선 - 2σ
#### 특성
- 밴드의 상/하한선 폭이 축소되면 가격의 변동성이 커질 가능성이 높다.
- 밴드의 상/하한선 폭이 확대되면, 추세전환이 이루어질 가능성이 높다.
- 가격이 상/하한선을 돌파했을 경우, 주가가 과대/과소평가된 상황이므로 추세가 반전될 확률이 높다.
#### 매매기법
- 밴드의 폭이 축소되면서 밀집구간을 거친 후에 주가가 상한선을 돌파시에는 매수, 하한선을 하향이탈시에는 공매도한다.
- 주가가 상한선에 접근하고 지표가 강세를 확증할 때에는 매수, 주가가 하한선에 접근하고 지표가 약세를 확증할 때는 매도
- 주가가 상한선을 여러번 건드리지만 주가지표가 약세를 보이면 상한선 근처에서 매도, 주가가 하한선을 여러번 건드리지만 주가지표가 강세를 보이면 하한선 근처에서 매수

## 191219
### Go well with
~와 잘 어울린다.  
ex)  
We order beer. It went well with the food.  

## 191218
### Drink in moderation
술을 적당히 마시다.  
ex)  
One of the biggest concerns is overdrinking when it comes to gatherings.  
People often drink to much and get drunk.  
When they get drunk, they can make mistakes.  
People should always drink in moderation at gatherings.  

## 191213
### Grab a bite
간단히 먹다.  
ex)  
I mostly go to coffee shops to hang out with my friends or coworkers.  
I sometimes get coffee to go or sometimes drink it on the spot.  
I sometimes grab a bite when I am hungry.  

## 191127
### glib.h만 giochannel.h를 include할 수 있도록 하는 법
```c++
// glib.h
#define __GLIB_H_INSIDE__
#include <glib/giochannel.h>
#undef __GLIB_H_INSIDE__
```
```c++
// giochannel.h
#if !defined (__GLIB_H_INSIDE__)
#error "Only <glib.h> can be included directly."
#endif
```

### Get a good night's sleep
충분한 숙면을 취하다.  
ex)  
Getting a good night's sleep is very important.  
Having a good mattress helps me get quality sleep.  

## 191126
### back in the day
예전에  
ex)  
Back in the day, we used to sweep the floors with a broom.  
But now, we use vacuum cleaners to clean the floors.  
They suck up the dust very easily. 

## 191120
### busy street
번화가  
ex)  
There are tons of stores in Korea.  
There are everywhere these days.  
Many stores are on busy streets with a lot of foot traffic.  

## 191119
### Do some catching up
밀린 이야기를 하다.  
ex) First, we ask how each other is doing and do some catching up.

## 191115
### Tons of
다수의  
ex) People do tons of things on the internet these days.

## 191113
### Keep it together
침착함을 유지하다.  
ex) Finn, keep it together.  

## 191111
### Someone is full of it
거짓말쟁이다.  
ex) You're full of it, Jake!  

## 191106
### Take credit for
~의 공을 차지하다  
ex) Don't take credit for other people's ideas.  

## 191105
### Feel left out
소외감을 느끼다.  
ex) Oh, I see. You're feeling left out and you want to roughhouse too.  

### Give it another shot
다시 시도해 보다  
ex) Jake, I gotta give this another shot.

### So be it
그렇다면 좋다(그대로 받아들이겠다는 뜻)  
ex) So be it, brother.  

## 191104
### All (goes) according to plan
모든 것이 계획대로 진행되다

## 191031
### At your service
ex) Ricardio at your service.  
1. 처음 보는 다른 이에게 정중히 소개할 때 사용
2. 도와주거나 사용할 준비가 된

## 191030
### No, That is not the case.
아니, 사실은 그렇지 않아.

## 191029
### Yes, if that is what must be done.
그래, 해야만 한다면 말이지

### It was so close
아깝다.  

## 191028
### Apply lotion
로션을 바르다.  
ex) Apply lotion to prevent dry skin  

## 191023
### How did it go?
어떻게 됐어?
ex)
"How did it go in Sinapore?"  
"It was awful, everything went wrong."

## 191022
### reach
```
verb
1. to arrive at a place, especially after spending a long time or a lot of effort travelling
2. to get to a particular level, especially a high one
3. to strech out your arm in order to get or touch something

noun.
1. your reach is the distance within which you can stretch out your arm and touch something
2. the limit within which someone can achieve something
```
ex) It's out of reach
1. 손에 닿지 않는 곳에 있다.
2. 능력 밖이다.

## 191021
### congratulate on
~를 축하하다.  
ex) Let me congratulate you on your promotion

## 191016
### no-brainer
`something that requires or involves little or no mental effort.`  
머리를 쓰지 않아도 되는 쉬운 것  
ex) it's a no-brainer  

## 191015
### as much as + if not more
더 많이는 아니더라도 ~만큼
ex) I think (that) the people (that) we work with can have just as much impact on our overall job satisfaction as the job itself, if not more.  

## 191014
### happen to
공교롭게, 혹시, 마침  
ex) I happen to have some cash on me right now.

## 191012
### as far as I know
내가 알기로는,  
ex) As far as I know, that movie is releasing this week.  

### from what I hear
내가 듣기로는,  
ex) From what I hear, the man was a drug addict.  

### the way I see it
내가 보기에는  
ex) The way I see it, the timing was the problem.  

## 191011
### That's all I have to say
그게 내 할말의 전부이다.  
ex) Yeah, I guess that's all I have to say  

## 191010
### as long as
~하는 한  
ex) whatever I chose to do in life, as long as I would do my best, he would be very proud of me.

### full of warmth
정감이 넘치는  
ex) His performance is always full of warmth.

## 191008
### fast
단식  
ex) I have been fasting all day.  

### I don't really know much about
~에 대해 잘 모른다.  
ex) I don't really know much about recycling in the media  

## 191007
### big of a deal
대단한 일  
ex) It's not really that big of a deal.  

### That's all I remember
내가 기억하는 전부에요  

## 1901004
### have no clue(=have no idea)
전혀 이해하지 못하다  
ex) I have no clue what you're saying  

### let alone
~는 커녕  
ex) There isn't enough room for us, let alone any guests.

## 191002
### I would have to say
말해야 할 것 같아  
ex) I would have to say my biggest influence in muisc is probably growing up in my mother's house  

## 191001
### When it comes to
~에 관한 한  
ex) When it comes to getting things done, he's useless.  

### Let me start with
~부터 시작해보자  
ex) Let me start with the past.  

## 190930
### At one's fingertips
`convient and easy to find`
편하고 사용하기 쉬운  
ex) Our tablet has a sleek design and all the tools you need at your figertips

### My understanding of sth
내가 이해하기로는
ex) My understanding of the situation is that the strike will end as soon as serious negotiations begin.`  
    So my understanding of it is that the garbage guys... can't... have to be able to recognize that it's recycling as opposed to normal trash.`  

### My experience overall
내 경험 상 대체로,

## 190909
### Rule of thumb
`a broadly accurate guide or principle, based on experience or practice rather than theory`  
rule은 규칙이 아닌 척도라는 의미. 경험 상 통용되는 결정. 관행.  
ex) It's a rule-of-thumb decision

## 190819
### Surrogate
```
noun
1. a substitute, especially a person deputizing for another in a specific role or office.

adjective
1. relating to the birth of a child or children by means of surrogacy.
```
대리인, 대리의  
ex) Provide a surrogate or placeholder for another object to control access to it.

## 190726
### Famished
`extremely hungry`  
아사할 정도로 배고픈 상태  
ex) I'm famished--is there anyting to eat?  

## 190703
### Bipartite Graph
- 그래프의 정점의 집합을 둘로 분할하여, 각 집합에 속한 정점끼리는 서로 인접하지 않도록 분할할 수 있을 때, 그러한 그래프를 특별히 이분 그래프 (Bipartite Graph) 라 부른다.
- 인접한 정점끼리 서로 다른 색으로 칠해서 모든 정점을 두 가지 색으로만 칠할 수 있는 그래프.
  
ret) https://gmlwjd9405.github.io/2018/08/23/algorithm-bipartite-graph.html

## 190620
### Spectacles
굉장한 구경거리라는 의미 외에도 안경이라는 의미도 있다.

### Json-glib code snippet
```c
static const gchar *foo_object_json = 
" { \"bar\" : 42, \"baz\" : \"foo\" }";

int main(void)
{
	GError *error = NULL;
	JsonParser *parser = json_parser_new();
	json_parser_load_from_data(parser, foo_object_json, -1, &error);
	if (error) {
		g_error("Unable to create instance: %s", error->message);
	}

	JsonNode *root = json_parser_get_root(parser);
	JsonObject *object = json_node_get_object(root);

	JsonNode *bar = json_object_get_member(object, "bar");
	gint64 bar_int = json_node_get_int(bar);
	JsonNode *baz = json_object_get_member(object, "baz");
	const gchar *baz_string = json_node_get_string(baz);

	g_print("bar_int : %ld baz_string : %s\n", bar_int, baz_string);
	g_object_unref(parser);
}
```

## 190611
### Pisano Period
피보나치 수열을 n으로 나누면 그 수열은 주기를 가지게 되는데, 이를 피사노 주기라고 하고, π(n)이라고 쓴다.
예를 들어 π(3)은  
피보나치 수열인 {0,1,1,2,3,5,8,13}을  
각각 3으로 나눈 나머지인 수열 {0,1,1,2,0,2,2,1}  
의 길이 8이다.  

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

