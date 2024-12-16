---
title: TIL(20241209) [Linux & Ubuntu]
author: hanni
date: 2024-12-09 14:50:00 +0800
categories: TIL
tags: [VMware, Ubuntu]
---

----------------------------------------------------------------------------

VM ware는 가상 머신 소프트웨어로 보통 하나의 PC를 가지고 여러 대의 PC가 있는 효과를 누리기 위해 주로 사용된다.

나는 리눅스 명령어를 익히고 공부를 위해 우분투 PC가 필요해서 VMware를 사용하게 되었다.

[VMware 설치](https://catnip-archive.tistory.com/entry/VMware-VMware-%EB%AC%B4%EB%A3%8C%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0Player-Window)

먼저 VMware 설치 후에 ubuntu 를 설치한다. 

[ubuntu 다운로드](https://releases.ubuntu.com/focal/)

Desktop Image 옆에 있는 64-bit PC desktop image 를 선택해서 설치했다.

![image](https://github.com/user-attachments/assets/b58e15bc-1696-4d01-ad82-6c5d8a9a543b)

세팅 부분에서 하드디스크 30GB, Processors 1로 수정

CD/DVD 쪽에 Use ISO image file 에 ubuntu-20.04.6-desktop-amd64.iso 파일을 입력해준 후 OK


## 💡 파이썬 설치 및 실행

![image](https://github.com/user-attachments/assets/a3bf65e5-4320-4354-8331-d6a99d92da50)

기존에 설치 되어있던 파이썬을 지우고 다시 재설치!

패키지 까지 완벽하게 삭제하기 위해서 아래 명령어 

```
sudo apt autoremove
```

![image](https://github.com/user-attachments/assets/634bc0b5-e078-431a-83b5-85efdc5989e1)

![image](https://github.com/user-attachments/assets/7831ac57-c391-4d5f-b190-4c00ba5b2f2f)


**참고**
파이썬을 다시 삭제하고 설치했더니 GUI로 들어가지지 않는다..

오로지 터미널만 열리는 점 ! 주의.. 다시 설치해야할 수 있으니 선택...


## 💡 리눅스 명령어

```
who 
- 사용자 정보 확인
uname 
- 운영체제 확인
uname man
- 메뉴얼 확인
which echo 
- 경로에 대해서 알려주는?
history
- 내가 사용했던 내역들을 보여줌
pwd
- 내가 현재 작업중인 디렉터리를 알려줌
ls -la
-폴더에 대한 상세내역
clear 
- 명령어 정리
cd ~
- home 디텍토리 나의 집? 으로 이동
ls -i
-i.node 번호 확인

(read 읽기 / write 쓰기 / x 실행) 
chmod u+rwx 디렉토리경로 또는 경로 + 파일명
- 권한 설정

gedit 경로/텍스트파일명
- 텍스트 파일 편집기
```

nano와 vim 자주 쓰는 명령어

```
// nano
ctrl + o -> enter -> ctrl + x  저장 후 나감

// vim
:wq 저장 후 나감
:q 저장 안하고 나감
:q! 저장 안하고 강제종료
```

[리눅스 환경에서 nano에디터 단축키 모음](https://techplay.blog/%EC%9D%B4%EA%B2%83%EB%A7%8C-%EA%BC%AD-%EA%B8%B0%EC%96%B5%ED%95%98%EC%9E%90-%EB%82%98%EB%85%B8nano-%EC%97%90%EB%94%94%ED%84%B0-%ED%95%84%EC%88%98-%EB%8B%A8%EC%B6%95%ED%82%A4-30%EA%B0%80%EC%A7%80/)