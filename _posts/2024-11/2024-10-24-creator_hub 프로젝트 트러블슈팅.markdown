---
title: TIL(20241104) [Creator_hub 프로젝트 - 트러블 슈팅]
author: hanni
date: 2024-11-04 23:50:00 +0800
categories: TIL
tags: [SpringBoot, Apache spark, spring scheduling, spring batch]
---

----------------------------------------------------------------------------


spring boot 3.X.X버전에서 Apache spark를 사용하기는 하늘의 별따기라는 것을 느끼고 있다.

일단 3.X.X버전이하로 간신히 연결했는데, 여기서 부터 알 수 있다.

나는 spark를 사용하려면 자바 17버전은 사용하지 못한다. 여기저기 블로그와 서치를 한 결과

```
Spring Boot 3.x에서 Apache Spark를 사용하는 데 어려움을 겪는 이유 중 하나는 호환성 문제입니다. Spring Boot 3.x는 Java 17 이상을 요구하지만, Apache Spark는 3.x 버전에서 Java 8 또는 11에 최적화되어 있습니다. 따라서, Spark 3.x 버전을 사용할 때 Java 17을 사용할 수 없는 경우가 많습니다. 
```

뚜둥.. ㅎㅎ

그래서 일단 spring boot를 2.7.18버전과 자바 11버전으로 낮추었다. 

```
- spring Boot 2.x 버전은 Java 8과 11을 지원합니다. 이 버전대에서는 Java 11을 사용할 수 있습니다.
- Spring Boot 3.x 버전부터는 Java 17 이상을 요구합니다. 따라서, Spring Boot 3.x를 사용하려면 Java 17 이상을 사용해야 합니다.
요약하자면, Spring Boot 2.x는 Java 11과 호환되지만, Spring Boot 3.x는 Java 17 이상만 지원합니다.
```

spark는 최신버전을 사용해도 문제가 없었다. spark 3.5.3버전을 사용 중이다.

이제 왜 이렇게까지 되어야 하는지에 대해서 궁금증이 생겼다.

Apache spark view에서 javax패키지의 servlet을 사용하는데 spring boot 3버전은 javax-> jakarta로 변경되었다.

즉, spark를 사용하기 위해서는 jakarta.로 시작하는 패키지를 사용할 수 없다. 기존 코드와의 호환성 때문이다.

내가 spark를 사용하려고 했던 이유는 대용량 데이터를 빠르게 처리



