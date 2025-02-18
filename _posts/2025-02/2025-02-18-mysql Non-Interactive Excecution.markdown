---
title: [Database Non-Interactive Execution]
author: hanni
date: 2025-02-18 11:00:00 +0800
categories: TIL
tags: [MySQL, Cli]
---

----------------------------------------------------------------------------

프로젝트를 진행하면서 .sql 파일의 명렁어를 자동으로 실행해주는 방법


## 📌 MySQL 명령어와 함께 실행 (< 연산자 사용)

- 터미널에서 바로 실행하는 방법입니다. <br>

```
mysql -u root -p my_database < /path/to/my_dump.sql\
```

- my_database: SQL 파일을 실행할 데이터베이스 <br>
- /path/to/my_dump.sql: 실행할 SQL 파일 경로 <br>

- 💡 장점: <br>
1) MySQL에 직접 접속할 필요 없이 한 번에 실행 가능<br>
2) 자동으로 파일의 모든 SQL 문이 실행됨<br>


위의 방법은 비대화식 실행 또는 입력 리다이렉션 이라고 한다.

#### 비대화식 실행 (Non-Interactive Execution)

- 사용자가 명령어를 하나씩 입력하지 않고, 파일을 실행하면 모든 SQL 문이 자동으로 실행되는 방식<br>
- 예) mysql -u root -p my_database < my_dump.sql <br>
- 터미널에서 명령 실행 후, 자동으로 SQL 파일이 실행되고 종료됨 <br>
