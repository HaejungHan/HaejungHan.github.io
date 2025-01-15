---
title: [Docker<-Mysql 덤프 및 마운트]
author: hanni
date: 2025-01-08 15:00:00 +0800
categories: TIL
tags: [Docker, Docker-compose, Mysql]
---

----------------------------------------------------------------------------

## 📌 MySQL 덤프 
- Mysql 데이터베이스의 내용을 백업하거나 복원하는데 사용되는 SQL 형식 파일
- mysqldump 명령어로 사용

## 📌 MySQL 마운트
- Docker에서 파일시스템을 docker 컨테이너에 연결하는 방법
- 마운트를 통해 컨테이너가 호스트 시스템의 특정 디렉토리나 파일에 접근할 수 있게 되며, MySQL 데이터베이스의 데이터를 Docker 컨테이너 종료 후에도 지속적으로 저장할 수 있게 해줌

## 📌 로컬의 mysql -> Docker 덤프 및 마운트 과정
1) 로컬에서 데이터베이스 생성 
2) mysql 덤프
``` 
mysqldump -u root -p 데이터베이스 명 > 데이터베이스 명.sql
```
3) 컨테이너에 sql 파일 복사
``` 
docker cp 데이터베이스 명.sql DB컨테이너 명:/데이터베이스 명.sql
```
4) 도커 실행
5) 도커 컨테이너 접속
```
docker exec -it DB컨테이너 명 bash
```
6) SQL 파일 마운트 
```
mysql -u root -p 데이터베이스 명 < /데이터베이스 명.sql
```

**데이터베이스 수정 후**
1) workbench에서 수정 후 저장
2) 2번 부터 다시 실행
3) docker컨테이너로 들어간 후에 수정된 내용이 잘 반영되었는지 확인할 것

```
mysql -u root -p
use 데이터베이스 명;
show tables;
```
