---
layout: post
title:  "[TIL] HADOOP 기초 개념 정리"
subtitle:   "HADOOP 기초 개념 정리"
categories: TIL
tags: dataengineering Hadoop
comments: true
header-img:
---

# Hadoop 기초 개념 정리

시작하기 앞서 본 문서는 제가 속한 연세대학교 빅데이터 동아리 YBigta 데이터 엔지니어링 팀의 정규세션 발표자료를 인용하고 정리한 자료임을 밝힙니다.

## 빅데이터

현대 사회의 데이터의 특징은 **빅데이터**라는 말로 쉽게 정의내릴 수 있을 것이다. 빅데이터란 무엇인가? 빅데이터란 디지털 환경에서 발생하는 대량의 모든 데이터를 의미한다. 현대 사회에서 다루는 데이터는 전통적인 테이블 형태의 정형 데이터를 넘어 영상/이미지/음성 등 비정형 데이터까지 영역을 넓히게 되었다. 이러한 빅데이터는 크기 면에서 기존의 데이터와 비교할 수 없을 만큼 거대하기에 새로운 데이터처리 시스템을 필요로 하게된다. 빅데이터의 특징은 아래와 같다.

### 5V

**Volume** : KB, MB 단위에서 GB, TB 단위로 증가

**Velocity** : 데이터의 생성속도 증가, 실시간 데이터 처리 등 속도의 중요성

**Variety** : 정형, 비정형, 반정형 등 다양한 형태의 데이터

**Veracity** : 대용량의 데이터를 정확하게 다루는 방법이 필요

**Value** : 수 많은 데이터 사이에서 유의미한 정보를 탐색

---

## 분산처리 (Distributed Computing)

빅데이터를 처리하는데 적합한 시스템으로 각광받고 있는 것이 **분산처리**이다. 분산 처리란 말 그대로 한 가지 일을 여러 개로 나누어 다른 컴퓨터에 보내 처리하고 결과를 모으는 것을 뜻한다. 산업 환경에서의 목표는 커다란 데이터를 적은 비용으로 처리하는 것이다. 이때 하나의 비싸고 고성능의 서버를 통해 데이터를 처리하는 것보다 성능은 떨어지지만 가격이 싼 여러 대의 서버를 사용하는 것이 비용적인 측면에서 유리하기 때문에 분산처리가 데이터 엔지니어링 분야에서 각광을 받게 되었다.

### Hadoop의 등장 배경

**하둡**은 2006년에 더그 커팅과 마이크 캐퍼렐라가 개발했고 여러 대의 컴퓨터 클러스터에서 대규모 데이터 세트를 분산 처리할 수 있게 해주는 프레임워크이다. 위에서 설명한 것처럼 하둡의 목적은 여러 대의 값싼 컴퓨터들로 클러스터를 구성하고 데이터를 고르게 나누어 **저장** 및 **처리**를 하는 것에 있다. 여기서 클러스터란 여러 대의 컴퓨터를 연결해 하나의 시스템처럼 동작하는 컴퓨터 집합을 말한다.

이 때 저장을 담당하는 부분을 **HDFS** (Hadoop Distribute File System; 분산 파일 시스템)이라고 하고, 처리를 담당하는 부분을 **MapReduce** (분산 파일처리 시스템)이라고 한다.

![](https://user-images.githubusercontent.com/47618340/162691035-e6a00318-c233-4d27-b64f-8c5caa6d7cb7.png)

위 그림은 HDFS와 MapReduce를 나타낸 간단한 모식도이다. HDFS는 데이터의 손실을 막기 위해 복사본을 만들고 관리하는 역할을 한다. MapReduce는 큰 데이터를 분할하여 처리하고 다시 결합하는 역할을 담당한다.

---

### HDFS(Hadoop Distributed File System)

HDFS의 가장 큰 특징은 **블럭구조 파일 시스템**이라는 점이다. 블럭구조 파일 시스템이란 수십 테라~페타 바이트 이상의 빅데이터를 특정 사이즈의 블록으로 나누어 분산된 서버에 저장하는 시스템을 의미한다.

HDFS는 대용량 데이터를 저장하며, 복제본을 저장한다.

HDFS는 **데이터 노드**와 **네임 노드**로 구성되며 마스터 - 슬레이브의 구조를 띈다. 여기서 네임노드는 마스터, 데이터노드는 슬레이브의 역할을 담당한다. 쉽게 말해 네임노드는 데이터 노드를 관리하고 일을 할당하며, 데이터 노드는 시키는대로 일을한다. 데이터 노드는 네임 노드로 **Heartbeat**를 전송하는 절차를 통해 노드의 상태를 체크한다.

HDFS는 **데이터 무결성**을 띤다. 즉 한 번 저장한 파일은 수정이 불가능하며, 만약 파일이 잘못되었다면 전체를 삭제하고 파일을 다시 작성해야만 한다.

#### HDFS의 Master - Slave 구조

![](https://user-images.githubusercontent.com/47618340/162691115-f9b8de38-c1b0-446d-a9fc-2a86055dc739.png)

- **네임 노드**
  
  - 파일 시스템 이미지 (파일명, 디렉토리, 크기 등), 블록 매핑 정보 (클라이언트가 파일에 접근할 수 있게 만들어주는 정보) 등 메타 데이터 관리
  
  - Heartbeat를 통해 데이터 노드의 실행 상태, 용량, 장애 노드 처리 등 모니터링 작업 수행
  
  - 데이터 노드에 장애 발생 시 해당 블록을 새로운 노드에 복제
  
  - 클라이언트가 HDFS에 접근하기 위해서는 반드시 네임노드에 먼저 접속해야함

- **데이터 노드**
  
  - 클라이언트의 파일을 블록 단위로 나누어 저장하는 장소
  
  - 주기적으로 네임 노드에게 Heartbeat 전송
  
  - Heartbeat에는 데이터의 원본 + 메타 데이터 정보가 들어있음
  
  ---

### MapReduce

MapReduce는 분할정복 방식으로 대용량 데이터를 병렬 처리하는 데이터 분석 프레임워크이다. **Map** 부분과 **Reduce** 부분으로 나눌 수 있다.

![](https://user-images.githubusercontent.com/47618340/162691274-1d775908-6a43-4985-95d5-e5ec3faff12f.png)

- Map : 데이터 변형 작업 (Data Transformation)
  
  - 데이터를 Key - Value 형태로 가공

- Reduce : 데이터 집계 작업 (Data Aggregation)
  
  - 같은 키를 가진 모든 key - value 쌍을 동일한 Reducer에 전달
  
  - Mapper의 Output을 input으로 받음

#### Mapping Process

1. Input File
   
   - HDFS에 있는 입력파일을 분할하여 FileSplit을 생성
   
   - FileSplit 하나 당 Map Task 하나씩을 생성

2. Map
   
   - 데이터를 읽어와 Key - Value Pair를 생성

3. Combine
   
   - 디스크에 작성하기 전, Key - Value List에 대한 전처리를 수행
   
   - Ex) Aggregation: Sum, count

4. 파티션
   
   - 키를 기준으로 디스크에 분할 저장
   
   - 분할된 파일은 Local File System에 저장되고, 각각 다른 Reduce Task에 저장

#### Reducing Process

1. Shuffle
   
   - 여러가지 Mapper에 있는 결과 파일을 각 Reducer에 할당
   
   - Reduce에 할당된 결과 파일을 Reduce의 Local File System으로 복사

2. Sort
   
   - 병합 정렬 (Merge Sort)를 이용하여 Mapper 결과를 정렬 / 병합 Key로 하나의 파일 생성

3. Reduce
   
   - 정렬 단계에서 생성된 파일을 처음부터 읽으면서 리듀스 함수를 실행

#### MapReduce Example (Word Count)

![](https://user-images.githubusercontent.com/47618340/162691314-9e2dd4a3-e140-4506-b465-3ba456ddeef3.png)

#### MapReduce의 한계점

1. Job Tracker Memory Issue
   
   - 하둡의 작업 단위를 Job이라고 하며 Job Tracker는 이러한 Job을 관리하는 역할을 한다.
   
   - MapReduce 작업은 Job Tracker가 메모리에 많은 정보를 유지하기를 요구하는데 메모리 부족 문제가 발생하게 되면 Job Tracker가 제 역할을 하지 못하는 문제가 생긴다.

2. MapReduce Resource Issue
   
   - MapReduce는 클러스터에서 실행할 수 있는 Task의 수를 Slot이라는 단위로 관리한다.
   
   - 이 때 Slot의 용도를 미리 정해두기 때문에 남는 Slot을 유동적으로 활용할 수 없어 잉여자원이 된다.

3. Cluster 확장성
   
   - 단일 클러스터에서는 4000대가 한계
   
   - 최대 동시 실행 Task는 40000개가 한계
   
   ---

### YARN (Hadoop 2.0)

- 위에서 본 MapReduce의 한계점을 극복하기 위해 Hadoop 2.0에서는 기존에 MapReduce에서 처리하던 Cluster 관리 기능을 YARN으로 분리했다.

- MapReduce는 데이터 처리 방법 중 하나로만 이용되며, 더이상 MapReduce로만 처리되지 않음

- 다양한 데이터 처리 방식을 지원 (Batch, Interactive, Online, Streaming)

#### YARN의 구성요소

- Resource Manager : 클러스터의 전반적인 자원관리, Scheduler, Application Manager 조정

- Application Manager : Application들의 실행 상태를 관리해 그 상태를 Resource Manager에게 통지

- Scheduler : Node Manager들의 자원 상태를 관리해 그 상태를 Resource Manager에게 통지

- Node Manager : 노드 당 하나씩 존재하여 Container의 리소스 사용량을 모니터링하고 관련 정보를 Resource Manager에게 보고

- Application Master : 어플리케이션 당 1개가 존재, Scheduler로부터 적절한 Container를 할당받고 프로그램의 실행 상태를 모니터링, Resource Manager에게 자원 요청

- Container : CPU, DISK, Memory 등의 리소스와 각 Task는 하나의 Container에서 점유되고 실행된다.

---

### Hadoop Streaming

Hadoop Streaming은 Python, Ruby, Shell Script 등 스크립트 언어를 하둡에서 실행하게 해주는 인터페이스이다. 기존의 MapReduce는 Java를 통해 실행되었고, 일정 시간 동안 쌓인 데이터를 한 번에 Batch 단위로 처리하는 개념이라면, Hadoop Streaming은 그때 그때 데이터를 처리할 때 쓰는 방식이다.
