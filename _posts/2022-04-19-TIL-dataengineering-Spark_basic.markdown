---
layout: post
title:  "[TIL] Spark 기초 개념 정리"
subtitle:   "Spark 기초 개념 정리"
categories: TIL
tags: dataengineering Spark
comments: true
header-img:
---

# Spark 기초

## Apache Spark

<img src="https://user-images.githubusercontent.com/47618340/163962783-8ff5e35d-bebc-4464-8737-5cb2058372b2.png" title="" alt="" data-align="center">

**아파치 스파크**는 한 마디로 빅데이터 처리를 위한 **오픈소스 통합 분산 처리 플랫폼**이라고 정의할 수 있다. Python, Java, Scala, R을 지원하며, SQL 뿐만 아니라 스트리밍, 머신러닝 등 넓은 범위의 라이브러리를 제공한다. 또한 단일 노트북 환경에서부터 수천 대의 서버로 구성된 클러스터까지 다양한 환경에서 실행할 수 있는 범용성을 자랑한다. 이러한 특성 덕분에 빅데이터 처리를 쉽게 시작할 수 있고 꾸준한 인기를 얻고 있다. 본 글에서는 스파크라고 줄여서 부르도록 하겠다.

---

## 1. Spark의 특징

스파크는 기존의 병렬처리 시스템인 하둡(맵리듀스)의 단점을 보완하기 위해 등장했다. 스파크의 장점은 다음과 같다.

- In-Memory 기반의 빠른 처리
  
  - 맵리듀스의 경우 디스크 기반으로 동작하므로 입력 데이터를 스토리지에서 읽고 분산처리 후 다시 스토리지에 보존하는 방식이다. 이러한 방식은 연속적이고 반복적인 데이터 처리에서는 비효율적이다. 반면 스파크는 메모리 기반이므로 매번 불필요한 디스크와 네트워크 I/O가 발생하지 않아 월등한 속도를 보여준다.

- 다양한 언어 지원

- 다양한 파일 포맷 지원 및 Hbase, Hive 등 다양한 프레임워크와 결합

- SQL 쿼리, 스트리밍 데이터, 머신러닝 등 고급 분석을 지원

---

### Hadoop vs Spark

<img src="https://user-images.githubusercontent.com/47618340/163962999-4e8216a5-8a8f-40d9-b235-86358b8a6c90.png" title="" alt="" data-align="center">

요약하면 하둡은 스토리지 기능을 담당하는 HDFS와 연산을 담당하는 MapReduce로 이루어진 **InfraStructure**이며 기본적으로 디스크/스토리지 중심의 운영을 하므로 I/O에 따르는 비효율이 발생한다. 스파크는 하둡 InfraStructure 위에서 동작할 수 있는 **데이터 프로세싱 툴** 중 하나로 속도가 느린 기존의 MapReduce를 보완한다. 스파크는 데이터를 메모리에 캐시로 저장하여 동작하므로 기존의 MapReduce에 비해 훨씬 빠르게 연산을 수행한다.

---

## 2. Spark Architecture

스파크 어플리케이션의 구조는 아래의 그림과 같이 Driver Process와 다수의 Executor Process로 구성된다.

<img src="https://user-images.githubusercontent.com/47618340/163963092-50cfd5f3-9c55-4250-941f-becd8aa8fff9.png" title="" alt="" data-align="center">

- Driver Process
  
  Driver Node(Master Node)에서 실행되는 프로세스로 스파크 어플리케이션의 정보를 유지하고 관리하는 역할을 한다. 또한 사용자 프로그램이나 입력에 대해 응답하고 전반적인 Executor Process의 작업과 관련된 분석, 배포 및 스케줄링을 수행한다.

- Executor Process
  
  Worker Node에서 실행되는 프로세스로 Driver Process가 할당한 작업을 실행하고 진행 상황을 Driver Process에 보고한다.

---

### Cluster Manager

<img src="https://user-images.githubusercontent.com/47618340/163963150-ca46a9f9-3dfa-4b93-85e9-3ace0cc40d29.png" title="" alt="" data-align="center">

클러스터 매니저는 여러 대의 서버로 구성된 클러스터 환경에서 다수의 어플리케이션이 함께 구동될 수 있도록 하는 역할을 수행한다. 특히 가장 중요한 것은 CPU, 메모리, 디스크와 같은 **컴퓨팅 리소스를 관리하고 분배**하는 것이다. 클러스터 매니저의 종류에는 Standalone, Apache Mesos, Hadoop YARN 등이 있다.

---

### Driver Program & Spark Context

<img src="https://user-images.githubusercontent.com/47618340/163963202-cc36a70a-f438-4c92-91e4-19a5453ff82e.png" title="" alt="" data-align="center">

- Driver Program
  
  스파크 어플리케이션의 메인함수를 실행시킨다. 이때 **Spark Context**를 생성하고 Spark Context와 함께 클러스터 내의 Job을 처리한다.

- Spark Context
  
  스파크 어플리케이션과 클러스터의 연결을 관리하는 객체이다. **모든 스파크 어플리케이션은 반드시 스파크 컨텍스트를 생성해야 하며 스파크로 수행하는 모든 동작이 스파크 컨텍스트를 지난다.** 클러스터 매니저와 함께 동작하며 여러가지 Job을 관리하고 작업의 수행, 중단, Worker Node의 분배를 관리한다.

---

### Worker Node

Worker Node를 설명하기 앞서 몇 가지 용어에 대해 짚고 넘어가도록 하자.

- RDD : 스파크에서 데이터를 처리하는 가장 기본적인 단위이다. 여러 노드에 흩어져 있으며 병렬처리 될 수 있는 아이템들의 모음이다.

- Job : 어플리케이션에서 스파크에 요청하는 일련의 작업이다. 여러 Task로 나뉘어 실행된다.

- Task : Executor에서 수행되는 최소 작업 단위

<img src="https://user-images.githubusercontent.com/47618340/163963262-5a000407-c2a5-44c3-bdbf-17eaada268a7.png" title="" alt="" data-align="center">

각 Worker Node에는 RDD가 분산되어 있고 RDD에서 Task가 실행된다. Worker Node는 Task의 결과를 스파크 컨텍스트에 반환한다. 이때 Worker Node의 숫자를 늘리게 되면 Job을 더 많은 파티션으로 나누어 병렬로 실행할 수 있게 된다.

---

### Spark Application 실행 과정

1. 먼저 사용자가 Spark-Submit을 통해 어플리케이션을 제출한다. (클러스터 매니저에게 작업 제출)

2. 스파크 드라이버가 main 함수를 실행하며, 스파크 컨텍스트 생성

3. 스파크 컨텍스트가 클러스터 매니저와 연결

4. 스파크 드라이버가 클러스터 매니저로부터 Executor 실행을 위한 리소스 요청

5. 스파크 컨텍스트는 작업 내용을 Task 단위로 분할해 Executor에 전송

6. 각 Executor는 작업을 수행하고 결과 저장

---

## 3. Spark API

API (Application Programming Interface)란 쉽게 말해 사용자가 특정 기능을 사용하기 쉽도록 미리 정해진 규격을 제공해주는 것이다. 스파크에서 사용자는 간단한 명령어만 입력한다면 분산된 형태의 데이터를 사용자 친화적인 형태의 규격으로 받아볼 수 있다.

<img src="https://user-images.githubusercontent.com/47618340/163963325-7849a778-c669-4c5b-8260-d95be55a180f.png" title="" alt="" data-align="center">

Spark의 API는 위의 그림과 같이 구성되어 있다. 여기서는 저수준 API인 **RDD**, 구조적 API인 **Dataset**과 **DataFrame**에 대해 간략히 알아볼 것이다. 자세한 내용은 다음 게시글에서 다룰 예정이다.

---

### RDD vs DataFrame vs Dataset

<img src="https://user-images.githubusercontent.com/47618340/163963399-83e18df5-8681-412e-9003-ec999ecf14a9.png" title="" alt="" data-align="center">

---

## 4. Transformation / Action

### Spark with RDD

스파크를 구성하는 가장 기초적인 데이터 구조는 **RDD**이다. RDD의 R은 Resillient의 약자로 회복력 있는, **변하지 않는** 이라는 뜻을 갖는다. 즉 RDD는 **변경이 불가능한** 데이터 구조이므로 기존의 RDD로부터 새로운 RDD를 생성하는 식으로 조작을 가할 수 있다. 이러한 특성으로 인해 Spark는 RDD에 포함된 데이터를 직접 저장하는 것이 아니라 RDD를 생성하는데 사용한 작업 내용을 기록하는데 이것을 **Lineage**라고 한다.

<img src="https://user-images.githubusercontent.com/47618340/163963472-c13b9bc5-85a2-4837-8a78-fe0b84b99da3.png" title="" alt="" data-align="center">

위와 같은 Lineage Graph를 통해 스파크는 RDD를 재연산하거나 유실된 RDD를 복구하는데 활용한다.

---

### RDD Operation

Spark의 RDD는 **Transformation**과 **Action**이라는 두 가지 종류의 연산만을 지원한다.

- Transformation
  
  RDD의 형태를 변형하는 연산을 의미한다. 위에서 언급했듯이 RDD의 핵심은 불변성이므로 실제로는 형태가 변형된 **새로운 RDD**를 생성하는 것이다. 대표적인 예시는 **map**과 **filter** 연산이 있다.
  
  - map : RDD의 각 요소에 함수를 적용하고 결과 RDD를 반환
  
  - filter : 전달된 함수의 조건을 통과한 값으로만 이루어진 RDD 반환

Transformation는 **Lazy Execution**이라는 특이한 특성을 가진다. Lazy Execution이란 Action 연산이 호출되기 전까지는 실제로 Transformation 연산을 수행하지 않고 기록만 해둔다. 이러한 방식을 통해 계산의 결과값이 필요할 때만 계산이 이루어지며 연산 최적화로 효율적인 작업 재구성이 가능해진다.

- Action
  
  드라이버 프로그램에 최종 결과 값을 되돌려 주거나 외부 저장소에 값을 기록하는 연산을 의미한다. 이를 통해 RDD가 아닌 다른 데이터 타입의 결과를 반환해준다. reduce, collect, count 등이 있다.
  
  - reduce : RDD의 값들을 병렬로 병합 연산
  
  - collect : RDD의 모든 데이터 요소 리턴
  
  - count : RDD의 모든 데이터 수를 합산하고 정수로 리턴

Lazy Execution에 따라 Action이 지정되면 스파크의 Job이 시작된다. 또한 Executor에 할당된 RDD의 내용을 확인하기 위해서는 반드시 Action 연산이 필요하다.
