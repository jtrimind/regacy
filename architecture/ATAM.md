# ATAM: Method for Architecture Evaluation

## Reference
[ATAM: Method for Architecture Evaluation](https://resources.sei.cmu.edu/asset_files/TechnicalReport/2000_005_001_13706.pdf)

---

## Table of Contents
- [Abstract](#abstract)
- [Introduction](#introduction)
- [The Underlying Concepts](#the-underlying-concepts)
- [A Brief Introduction to the ATAM](#a-brief-introduction-to-the-atam)
- [Quality Attribute Characterizations](#quality-attribute-characterizations)
- [Scenarios](#scenarios)
- [Attribute-Based Architectural Styles](#attribute-based-architectural-styles)
- [Outputs of ATAM](#output-of-atam)
  - [Risks and Non-Risks](#risks-and-non-risks)
  - [Sensitivity and Tradeoff Points](#sensitivity-and-tradeoff-points)
  - [A Structure for Reasoning](#a-structure-for-reasoning)
- [The Steps of ATAM](#the-steps-of-atam)
  1. [Present the ATAM](#present-the-atam)
  2. [Present Business Drivers](#present-business-drivers)
  3. [Present Architecture](#present-architecture)
  4. [Identify Architectural Approaches](#identify-architectural-approaches)
  5. Generate Quality Attribute Utility Tree
  6. [Analyze Architectural Approaches](#analyze-architectural-approaches)
  7. Brainstorm and Prioritize Scenarios
  8. Analyze Architecture Approaches
  9. [Present Results](#present-results)
- The Two Phases of ATAM
- A Sample Evaluation: The BCS
- Results Of The BCS ATAM
- Conclusions

---

## Abstract
소프트웨어 아키텍처가 조직의 핵심 비즈니스 자산이라면, 아키텍처 분석 또한 조직의 핵심 실무가 되어야 한다.  
왜냐하면 아키텍처는 복잡하고 설계 트레이드오프를 포함하기 때문이다.  
엄밀한 분석 프로세스를 수행하지 않고서는 아키텍처 결정이 바람직한지 보장할 수 없다.  
(바람직한 아키텍처 결정은 품질 속성의 달성에 영향을 미치고, 리스크를 적절히 완화시킨다.)  
이 보고서에는, 아키텍처 분석을 수행하기 위한 기술적, 조직적 토대 일부를 논의하고, Architecture Tradeoff Analysis Method(ATAM)을 소개한다.  

## Introduction

## The Underlying Concepts

## The Brief Introduction to the ATAM

## Quality Attribute Characterizations

## Scenarios

## Attribute-Based Architectural Styles

## Output of ATAM
### Risks and Non-Risks
```
Risks: potentially problematic architectural decisions
Non-Risks: good decisions that rely on assumptions that are frequently implicit in the architecture
```
- Risk는 아키텍처 결정이 완전하지 못해서 존재하는 위험
- Non-Risk는 빈번히 발생하지만 명시되어있지 않은 상황에 대한 아키텍처 결정을 내려서 안위험 
- Risk와 Non-Risk는 명시적으로 기록되어야 함
- 구성요소
  1. 아키텍처 결정(또는 아직 정해지지 않은 결정)
  2. 품질 요소에 대한 영향
  3. 긍정적이거나 부정적인 효과에 대한 이유
- 예시
  - Risk
```
1. The rules for writing business logic modules in the second tier of your three-tier clientserver style are not clearly articulated.
2. This could result in replication of functionality thereby compromising modifiability of the third tier.
3. Unarticulated rules for writing the business logic can result in unintended and undesired coupling of components
```
  - Non-Risk
```
1. Assuming message arrival rates of once per second, a processing time of less than 30 ms, and the existence of one higher priority process,
2. a one-second soft deadline seems reasonable
3. since the arrival rate is bounded and the preemptive effects of higher priority processes is known and can be accommodated.
```

### Sensitivity and Tradeoff Points
```
Sensitivity point: a property of one or more components (and/or component relationships) that is critical for achieving a particular quality attribute response
Tradeoff point: a property that affects more than one attribute and is a sensitivity point for more than one attribute
```
- Sensitivity point는 하나의 품질 요소를 달성하기 위한 중요한 속성이나 컴포넌트
- Tradeoff point는 여러 개의 품질 요소에 관련된 속성이나 컴포넌트

### A Structure for Reasoning
- 아키텍처 평가의 목표는 reasoning을 명시적으로 하고 후대를 위해 기록하는 것
- reasoning은 formal할 필요는 없으나 predictive하고 repeatable 해야함
- [ABAS](ABAS.md)와 quality attribute characterizations은 resoning model을 만드는 기술기반을 제공

## The Steps of ATAM
### Present the ATAM
이 단계에서, 평가팀은 ATAM을 이해관계자들에게 소개한다.  
이 시간은 모든 사람들에게 이후에 진행될 프로세스를 설명하고, 질의응답을 하고, 남은 활동들에 대한 맥락과 기대를 설정하는데 사용된다.  
모든 사람들이 어떤 정보들이 수집되고, 어떻게 자세히 조사될 것인지, 누구에게 보고될 것인지 아는 것이 중요하다.  
특히 프리젠테이션은 이하의 내용을 설명한다.  
- ATAM의 간략한 절차
- 도출 및 분석에 사용될 기법: 유틸리티 트리 생성, 아키텍처 접근 기반 도출/분석, 시나리오 브레인스토밍/매핑
- 평가의 산출물: 도출되고 우선순위가 지정된 시나리오, 아키텍처를 이해/평가하기 위해 사용되는 질문, 유틸리티 트리, 아키텍처 동인 요구사항 설몇 및 우선순위 지정, 확인된 아키텍처 접근 및 스타일 집합, 발견된 리스크, 논-리스크 집합, 발견된 센서티비티 포인트 및 트레이드오프

### Present Business Drivers
평가에 참여하는 모든 사람들은 시스템을 이해할 필요가 있다.  
이 단계에서 프로젝트 매니저는 비즈니스 관점에서 전체적인 시스템 개요를 소개한다.  
시스템은 높은 추상화 수준에서 제시되어야 한다.  
일반적으로 이하의 내용을 설명한다.
- 가장 중요한 기능적 요구사항
- 기술적, 관리적, 경제적, 정치적 제약
- 비즈니스 목표와 맥락
- 주요 이해관계자
- 아키텍처 동인(아키텍처를 정하는 주요 품질속성 목표)

#### Business Case/Architecture Presentation
단계 2,3(비즈니스 동인과 아키텍처 제시)에서 제시된 정보의 품질, 일관성, 풍부함을 보장하기 위해, 우리는 발표자에게 문서 템플릿을 일반적으로 제공한다.  
비즈니스 케이스를 위해 제공되는 문서 템플릿의 예시는 아래와 같다.
```
비즈니스 문맥/동인 제시 (~ 12 슬라이드; 45분)

- 비즈니스 환경, 역사, 시장 차별화 요소, 동인 요구사항, 이해관계자, 현재 요구와 어떻게 제안된 시스템이 이러한 요구를 충족시킬지, 요구사항들에 대한 설명(3-4 슬라이드)

- 비즈니스 제약 사항에 대한 설명(예를 들어, 출시 날짜, 고객 요구사항, 표준, 비용 등) (1-3 슬라이드)

- 기술적 제약 사항에 대한 설명(COTS, 다른 시스템과의 호환성, 필요한 하드웨어/소프트웨어 플랫폼, 레거시 코드 재활용 등.) (1-3 슬라이드)

- 원하는 품질 속성(performance, availability, security, modifiability, interoperability, integrability) 및 파생되는 비즈니스 요구 사항 (2-3 슬라이드)

- 용어집 (1 슬라이드)
```

### Present Architecture
아키텍처는 아키텍트에 의해 적절한 수준의 디테일을 가지고 제시될 것이다.  
적절한 수준은 무엇인가?  
이는 몇가지 요인에 따라 결정된다: 얼마나 많은 정보들이 결정되고 문서화되었는지; 얼마나 많은 시간을 쓸 수 있는지; 시스템이 직면한 리스크가 얼마나 많은 지  
이용 가능하고 문서화된 아키텍처 정보의 양은 수행 가능한 분석과 분석의 품질에 직접적으로 영향을 미친다. 그러므로 이것은 중요한 단계이다.  
좀 더 실질적인 분석을 하기 전에, 평가팀은 수집해야하고 문서화해야하는 추가적인 아키텍처 정보를 지정할 것이다.  

이 발표에서 아키텍처는 다음을 포함해야 한다.
- 기술적 제약조건(사용을 위해 규정된 OS, 하드웨어, 미들웨어)
- 시스템이 상호작용해야하는 다른 시스템
- 품질 특성 요구사항을 충족하기 위해 사용되는 아키텍처 접근 방식

이 때, 평가 팀은 아키텍처 접근에 대한 초기 탐색을 시작한다.

아키텍처 발표를 위한 템플릿은 아래와 같다.
ATAM에 앞서 이러한 템플릿을 적절한 이해관계자(이 경우, 아키텍트)에게 제공하는 것은, 그들이 제시하는 정보의 변동성을 줄이고, 우리가 스케쥴에 맞추고 있다는 것에 도움을 준다.

### Identify Architectural Approaches

### Analyze Architectural Approaches

- 템플릿
  - *Scenario*: **a scenario from the utility tree of from scenario brainstorming**
  - *Attribute*: **performance, security, availability, etc.**
  - *Environment*: **relevant assumptions about the environment in which the system resides**
  - *Stimulus*: **a precise statement of the quality attribute stimulus (e.g., failure, threat, modification, …) embodied by the scenario**
  - *Response*: **a precise statement of the quality attribute response (e.g., response time, measure of difficulty of modification)**
  - *Architectural Decisions, Risk, Sensitivity, Tradeoff*: **list of architectural decisions affecting quality attribute response, risk #, sens. point #, tradeoff #**
  - *Reasoning*: **qualitative and/or quantitative rationale for why the list of architectural decisions contribute to meeting the quality attribute response requirement**
  - *Architecture diagram*: **diagram or diagrams of architectural views annotated with architectural information to support the above reasoning. These may be accompanied by explanatory text.**

### Present Results
- ATAM으로 모은 정보들을 정리해서 stakeholder에게 발표하는 단계
- ATAM outputs
  - the architectural approaches/styles documented
  - the set of scenarios and their prioritization
  - the set of attribute-based questions 
  - the utility tree
  - risks, non-risks, sensitivity points and tradeoff points
