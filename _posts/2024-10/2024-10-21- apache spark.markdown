---
title: TIL(20241021) [Apache Spark 설치]
author: hanni
date: 2024-10-21 11:13:00 +0800
categories: TIL
tags: [Apache Spark, Framework]
---

----------------------------------------------------------------------------

다음 spark 를 활용한 빅데이터 처리 관련 프로젝트를 진행하기 위해 spark 설치가 필요했는데, 블로그를 참고하여 설치했다.  

크게 어려운 부분은 없었다. 하라는 대로 따라만 잘하면 설치는 간편했는데,
이제 spark를 어떻게 활용하냐는 점에서 .. 달라지겠지...😂


## 📌 Apache Spark의 등장배경?
- Spark는 MapReduce 형태의 클러스터 컴퓨팅 패러다임의 한계를 극복하고자 등장했는데, MapReduce는 Disk로 부터 데이터를 읽은 후, Map을 통해 흩어져 있는 데이터를 Key-Value 형태로 연관성이 있는 데이터끼리 묶은 후에 Reduce를 하여 중복된 데이터를 제거하고, 원하는 데이터로 가공하여 다시 Disk에 저장한다. 이러한 파일 기반의 Disk I/O는 성능이 좋지 못했고, In-memory연산을 통해 처리 성능을 향상시키고자 Spark가 등장하게 되었다고 한다.

## 💡 Apache Spark란?
- Apache Spark는 오픈소스이며, 분산 클러스터 컴퓨팅 프레임워크로 RDD, Data Frame, Data Set의 3가지 API를 제공하는데, 이러한 데이터를 바탕으로 In-memory 연산을 가능하도록 하여 디스크 기반의 Hadoop에 비해 성능을 약 100배 정도 끌어올렸다. 

RDD와 DataFrame , Data Set에 대해서 간략하게 알아보도록 한다.

**1. RDD (Resilient Distributed Dataset)**<br>
- 정의: <br>
RDD는 Spark의 기본 데이터 구조로, 분산된 불변의 데이터 컬렉션입니다. 각 RDD는 클러스터의 여러 노드에 걸쳐 분산되어 저장됩니다.<br>
- 특징: <br>
1) 불변성: RDD는 생성 후 변경할 수 없습니다. 새로운 RDD는 기존 RDD를 변환하여 생성됩니다.<br>
- 저수준 API: <br>
RDD는 저수준의 데이터 처리 API로, 복잡한 데이터 변환을 직접 구현해야 합니다. <br>
- 성능: <br>
RDD는 데이터의 구조를 알지 못하기 때문에, 효율성이 떨어질 수 있습니다.<br>

**2. DataFrame**<br>
- 정의:<br>
 DataFrame은 RDD의 확장으로, 구조화된 데이터를 나타내는 분산 데이터 구조입니다. RDBMS의 테이블과 유사한 형태로, 열과 행으로 구성됩니다.<br>
- 특징:<br>
1) 스키마 지원: DataFrame은 각 열의 데이터 유형(스키마)을 알고 있으므로, SQL 쿼리를 통해 쉽게 데이터를 처리할 수 있습니다.<br>
2) 고수준 API: 사용자가 더 간단하게 데이터를 조작할 수 있도록 설계되었습니다. SQL과 비슷한 구문을 사용할 수 있습니다.<br>
- 성능: <br>
Catalyst 옵티마이저를 통해 쿼리 최적화를 수행하여 성능이 향상됩니다.<br>

**3. Dataset**<br>
- 정의: <br>
Dataset은 DataFrame의 타입 안전성을 제공하는 API로, 스칼라와 자바에서 사용됩니다. DataFrame과 유사하지만, 강력한 타입 시스템을 통해 컴파일 타임에 오류를 잡을 수 있습니다. <br>
- 특징: <br>
1) 타입 안전성: Dataset은 클래스 타입에 기반하므로, 컴파일 시 오류를 발견할 수 있습니다.<br>
2) API의 조합: Dataset API는 DataFrame API의 기능을 포함하고 있어, SQL 쿼리와 Dataset의 강력한 타입 기능을 함께 사용할 수 있습니다.<br>
3) 유연성: Dataset은 RDD와 DataFrame의 장점을 결합하여 더 유연하게 사용할 수 있습니다.<br>

**정리**<br>
- RDD: 저수준의 API로, 데이터의 구조를 알지 못하며 불변의 분산 데이터셋.<br>
- DataFrame: 구조화된 데이터를 지원하는 고수준 API로, SQL 쿼리 사용 가능. <br>
- Dataset: 타입 안전성을 제공하는 API로, DataFrame과 유사하나 더 강력한 타입 시스템을 가짐. <br>

데이터 분석관련 기능을 구현 계획에 있기 때문에 DataFrame과 DataSet 둘 중 하나를 상황에 맞춰서 사용하지 않을까 생각중이다.

일단 프로젝트 가명은 My Youtube라고 생각하긴 했는데.... 
채널, 또는 비디오 분석이나 추천 시스템 관련 기능을 생각해보고 있다.
조금 더 설계를 구체적으로 잡아야할 듯 하다. 

어쨋든 Youtube 를 활용한 프로젝트로, 대용량 데이터를 다룰 목적으로 기반을 잡았기에 Spark를 사용해서 연산하는 부분에서 빠른 처리를 할 수 있다고 생각해서 응용해보려고 한다. 

[hadoop설치-github](https://github.com/cdarlint/winutils)
- 나는 3.0.1 버전을 설치했다.
[Window에서 Apache Spark설치하기](https://dibrary.tistory.com/89)
[로컬 환경에서 apache spark설치하기](https://it-is-my-life.tistory.com/23)