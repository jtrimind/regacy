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
  1. Present the ATAM
  2. Present Business Drivers
  3. Present Architecture
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
