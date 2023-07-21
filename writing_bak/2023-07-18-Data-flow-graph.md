---
title: Data flow graph
categories:
  - Verilog HDL 기초
tags:
  - Veriog HDL
---

본 내용은 책[1]의 Chapter 2를 기반으로 작성 되었음을 밝힌다.

## Block diagram

Data flow graph 설명에 앞서 block diagram의 정의에 대해서 설명한다.

Block digaram은 복잡한 시스템(산업 장치, 전자회로 등)을 명확하게 표현하기 위해 구성 요소들의 모음으로 나타낸 높은 수준의 표현이다.

```
block di·a·gram
/bläk ˈdīəˌɡram/
a diagram showing in schematic form the general arrangement of the parts or components of a complex system or process, such as an industrial apparatus or an electronic circuit.
```
정의 출처: Oxford Languages

## Data flow graph

블록 다이어그램은 시스템의 데이터 흐름만 지정하지만 기능의 실행 순서는 지정하지 않습니다

Data flow model은 블록 다이어그램과 매우 유사하다.
그러나 data flow model은 동시성(concurrnet)을 가진다.
동시성 모델 (concurrent model)은 병렬 또는 순차 구현에 매핑될 수 있어 하드웨어, 소프트웨어 모두 적용이 가능하다.

Data flow model은 분산되어 있어 개별 시스템 구성 요소를 보조하기 위해 중앙 컨트롤 장치가 필요하지 않다.
각 동작을 스스로가 결정할 수 있다.

Data flow model은 모듈식(modular)이다.
독립된 동작을 구현, 라이브러리로 개발할 경우 플러그 앤 플레이 방식으로 적용할 수 있다
<!--TODO: 플러그앤 플래이 설명 추가-->

Data flow 시스템은 분석이 용이, 교착 상태, 안정성등의 속성을 모델 검사를 기반으로 평가할 수 있다.
<!--왜죠??-->

### Data flow model의 구성요소
Tokens, Actors, and Queues

1. Actor
   - Actor는 실제 동작을 수행
   - 제한된 동작이 있으며 해당 동작을 항상 처음부터 끝까지 반복한다.
     - 제한된 동작는 정확한 시작과 끝이 있음을 의미한다.
   - Actor가 1회 작동하는 것을 ``actor firing``이라 한다.
2. Token
    - Actor와 actor가 주고 받는 데이터 단위를 token이라 정의한다.
3. Queue
    - Queue는 한 actor가 다른 actor로 전달하는 토큰을 전송하는 **단방향** 통신 링크이다.
    - Queue는 first-in first-out(FIFO) 방식으로 동작한다.
    - 내부에 저장된 데이터는 절대 손실이 발생하지 않는다.

<!--TODO: Data flow model Tokens, Actors, and Queues 예시 추가 Fig. 2.3, 2.4-->

Data flow model이 실행 되면 actor는 입력 queue에서 token을 읽어 처리를 하며, 출력 queue에 data token을 저장한다.
이 단일 동작을 actor firing이라 한다.

Data flow execution은 actor firing sequence로 표현이 가능하다.

실제로 actor가 수행하기 위한 시간이 존재하지만,
data flow model에서는 데이터 수행 시간이 개념적으로 존재하지 않는다.

토큰이 있는 그래프를 데이터 흐름 모델의 표시라고 합니다. 데이터 흐름 모델이 실행될 때 그래프는 데이터 흐름 모델의 입력에서 출력으로 데이터를 구동하는 일련의 표시를 거칩니다. 각 마킹은 시스템의 다른 상태에 해당하며 데이터 흐름 모델의 실행은 각 마킹이 나타나는 순서에 따라 결정됩니다. 외부 관찰자에게는 이 표시(즉, 대기열의 토큰 분포)가 시스템에서 관찰 가능한 유일한 상태입니다. 여기에는 미묘한 부작용이 있습니다. 액터의 동작은 내부 상태 변수를 포함할 수 없습니다. 해결 방법은 상태 변수를 토큰으로 표현하는 것입니다.
<!--TODO: 이 부분 수정-->

Actor가 fire되는 조건을 firing rule of actor라 정의한다.

Firing rule of actor는 아래의 예시 그림을 이용해 설명한다.
한 개의 `add` actor는 2개의 queue가 각각 연결되어 있다.
`add` actor가 동작하기 위해서는 2개의 queue에 적어도 각 한 개의 데이터가 포함되어야 fire할 수 있다.

<!--TODO: fig 2.5-->

따라서 firing rule은 각 queue에 token의 존재 여부를 테스트 하는 것도 포함된다.

Actor 옆에 필요한 token의 수를 기록할 수 있다.

These numbers are called the token consumption rate (at the actor inputs) and token production rate (at the actor outputs).



## Synchronous data flow (SDF)

Synchronous data flow (SDF)의 정의는 소비/생산되는 토큰의 수가 고정되고 일정한 값인 결과 클래스를 지칭한다.

여기서 동기라는 용어는 토큰의 소비/생산 속도가 고정된 값임을 의미한다.




### Synchronous data flow (SDF) 구성요소
### 예시

## SDF to hardware/software


technique for formal analysis of data flow models called Synchronous Data Flow (SDF) graphs
After that, we look into systematic conversion of SDF graphs into a hardware or software implementation.

## 2.1 The Need for Concurrent Models: An Example

Data Flow Modeling and Implementation

노드 $V$

## References

[1] Data Flow Modeling and Implementation