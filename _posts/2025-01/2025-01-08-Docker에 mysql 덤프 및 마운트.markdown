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

