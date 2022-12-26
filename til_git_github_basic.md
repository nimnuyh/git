# **TIL Git Github Basic**

> 2022년 07월 25일 월요일

## Git & Github?

![Git로고](https://user-images.githubusercontent.com/49775540/168756716-68f9aebb-380f-4897-8141-78d8403f6113.png)

### Git

- 분산 버전 관리 프로그램
- 백업, 복구, 협업을 위해 사용
- Git 공식문서 https://git-scm.com/book/ko/v2

### Github

- Git을 사용하는 프로젝트의 협업을 위한 웹호스팅 서비스

---

## CLI

> CLI (Command Line Interface, 커맨드 라인 인터페이스)는 터미널을 통해 사용자와 컴퓨터가 상호 작용하는 방식을 뜻한다.

### 터미널 명령어 정리

|명령어|설명|옵션|
|---|---|---|
|mkdir|디렉토리 생성||
|cd|작업 디렉토리 변경||
|touch|파일 생성||
|ls|현재 디렉토리의 파일 목록 출력|-a : 숨김파일 보기<br> -l : 확장자 등 모든 정보 보기|
|rm|파일 삭제/디렉토리 삭제|-r : 재귀적으로 폴더 하단 내역도 삭제<br> -rf : 강제 삭제|
|mv|이름 변경<br> 위치 변경|이름 : [oldname] [newname] <br>위치 : [filename] [dirname]|
|pwd|현재 작업 디렉토리||

ex)
```git bash
$ mkdir [dirname]

$ cd ..
$ cd [dirname]

$ touch [filename]

$ ls
$ ls -a
$ ls -l

$ rm [filename]
$ rm -r [dirname]
$ rm -rf [dirname]

$ mv [newname] [oldname]
$ mv [filename] [dirname]

$ pwd
```

### git 명령어 기초
```git bash
# git으로 관리 시작, 디렉토리당 한번만
$ git init 

# 상태 확인
$ git status

# 작업 디렉토리 변경사항 스테이징 영역으로 추가
$ git add 

# 변경사항 기록
$ git commit -m "commit name"

# config 설정
$ git config --global user.email "you@example.com"
$ git config --global user.name "Your Name"
# 확인
$ git config --global --list

# 커밋 내역 확인
$ git log --oneline

# 커밋 간 변경사항 비교
$ git diff [commitid] [commitid]

# github 연결
$ git remote add origin URL
# 확인
$ git remote -v
# 삭제
$ git remote rm origin

# github에 local commits 올리기
$ git push origin [branchname]
```