# ABAS
[상위 페이지로](index.md)

## Table of Contents
- [Reference](#reference)
- [Abstract](#abstract)

## Reference
[Attribute-Based Architectural Styles](https://resources.sei.cmu.edu/asset_files/TechnicalReport/1999_005_001_16781.pdf)

## Abstract
아키텍처 스타일은 `구성요소 유형들과 그들의 토폴로지(component types and their topology)`, `데이터의 패턴과 구성요소들 간의 제어 상호작용(pattern of data and control interaction among the components)`, `그 스타일을 사용함으로써 얻는 이득과 손해(benefits and drawbacks of using that style)`에 대한 설명이다.  
아키텍처 스타일은 관련되어 알려진 속성들과 함께 설계의 부류를 정의하기 때문에 중요한 엔지니어링 산출물이다.  
아키텍처 스타일과 속성들은 각 부류가 역사적으로 어떻게 사용되었는지에 대한 경험 기반의 증거와 함께 각 부류가 왜 특정한 속성을 갖는지를 설명하기 위한 질적인 추론을 제공한다.  
  
Attribute-Based Architectural Styles(ABASs)는 아키텍처 스타일을 기반으로 질적이거나 양적인 추론 프레임워크 명시적으로 연관시킨다. 이를 통해 ABAS는 아키텍처 디자인에 대한 좀 더 정확한 추론을 위한 토대를 제공한다.  
이러한 추론 프레임워크는 품질 특성에 특화(quaility attribute-specific)된 모델에 기반을 두고 있다. 이러한 모델은 다양한 품질 속성 커뮤니티(performance, reliablity, etc...)에 존재한다.  
  
과거 설계자들은 비슷한 문제들을 직면하며 지혜를 축적해왔으며, ABAS는 설계자에게 이러한 집약된 지혜를 제공하기 때문에 강력하다.  
이 보고서에서 우리는 설계와 분석 모두에서 ABAS의 사용 예시를 보여준다.  
우리는 ABAS가 아키텍처 설계 공학 분야를 만드는 기반을 제공한다고 주장한다. 이는 설계가 애드혹이 아닌 예측가능한 프로세스로 만들기 위함이다.  

## Performance Characterization
```
Performance ┬ Stimuli ┬ Mode ┬ Regular
            │         │      └ Overload
            │         ├ Source ┬ Internal Event
            │         │        ├ Clock Interrupt
            │         │        └ External Event
            │         └ Frequency Regularity ┬ Periodic
            │                                └ Aperiodic ┬ Sporadic
            │                                            └ Random
            ├ Architectural Parameter ┬ Resource ┬ CPU Memory
            │                         │          ├ Network
            │                         │          └ Device & Sensors
            │                         ├ Resource Arbitration ┬ Queuing Policy
            │                         *TBD*
            └ Responses ┬ Latency ┬ Response Window
                        │         ├ Criticality
                       │         ├ Best/Avg/Worst Case
                       │         └ Jitter
                       ├ Throughput ┬ Criticality
                       │            ├ Best/Avg/Worst Case
                       │            └ Observation Window
                       └ Precedence ┬ Criticality
                                    └ Ordering ┬ Partial
                                             └ Total
```