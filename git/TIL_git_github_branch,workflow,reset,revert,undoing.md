# **TIL Git Github (branch, workflow, reset, revert, undoing)**

> 2022년 07월 27일 수요일

## branch

> 여러 갈래로 작업 공간을 나누어 독립적으로 작업할 수 있도록 도와주는 Git의 도구

### git branch

``` git bash
# branch 목록 확인
$ git branch

# 원격 저장소의 branch 목록 확인
$ git branch -r

# 새로운 branch 생성
$ git branch [branchname]

# 특정 commit 기준으로 branch 생성
$ git branch [branchname] [commitid]

# 특정 branch 삭제
# 병합된 branch만 삭제 가능
$ git branch -d [branchname] 
# 강제 삭제 (병합되지 않은 branch도 삭제 가능)
$ git branch -D [branchname] 
```

### git switch

```git bash
# 다른 branch로 이동
$ git switch [branchname]

# branch 생성과 동시에 이동
$ git switch -c [branchname]

# 특정 commit 기준으로 branch 생성과 동시에 이동
$ git switch -c [branchname] [commitid]
```

## branch merge

> 각 branch에서 독립적으로 작업된 내용을 master에 반영하는 병합과정

### git merge

```git bash
$ git merge [branchname]
```

- merge의 종류
  1. Fast-Forward
     - branch가 가리키는 commit을 앞으로 이동
  2. 3-Way Merge
     - 각 branch의 commit 2개와 공통 조상 1개를 사용해 병합
     - 두 branch에서 다른 파일 혹은 같은 파일의 다른 부분을 수정했을 때 가능 
  3. Merge Conflict
     - 병합하는 2 branch에서 같은 파일의 같은 부분을 수정한 경우, Git이 어느 브랜치의 내용으로 작성해야 하는지 판단하지 못해서 발생하는 충돌 현상
     - 사용자가 직접 내용을 선택해서 Conflict를 해결해야 함

## Git Workflow

### 1. 원격 저장소 소유권이 있는 경우
> 원격 저장소가 자신의 소유이거나 collaborator로 등록되어 있는 경우

- master에 직접 개발하는 것이 아니라, 기능별 branch를 만들어 개발
- Pull Request를 같이 사용하여 팀원 간 변경 내용에 대한 소통을 진행

작업흐름

```git bash
# 1. 소유권이 있는 원격 저장소를 로컬 저장소로 clone
$ git clone URL

# 2. 작업할 기능에 대한 브랜치를 생성하고 기능을 구현
$ git switch -c [branchname]

# 3. 기능 구현이 완료되면, 원격 저장소에 해당 branch push
$ git push origin [branchname]

# 4. Pull Request를 통해 브랜치를 master에 반영해달라는 요청을 보냄

# 5. 병합이 완료되면 원격 저장소에서 병합이 완료된 branch는 불필요하므로 삭제

# 6. master에 branch가 병합되면 master로 이동
$ git switch master

# 7. 병합으로 인해 변경된 원격 저장소의 master 내용을 pull
$ git pull origin master

# 8. 기존 로컬 branch 삭제
$ git branch -d feature/login
```

### 2. 원격 저장소 소유권이 없는 경우
> 오픈 소스 프로젝트와 같이, 자신의 소유가 아닌 원격 저장소인 경우

- fork : 원본 원격 저장소를 그대로 내 원격 저장소에 복제
- 기능 완성 후 Push는 복제한 내 원격 저장소에 진행
- Pull Request를 통해 원본 원격 저장소에 반영될 수 있도록 요청

작업흐름

```git bash
# 1. 소유권이 없는 원격 저장소를 fork를 통해 내 원격 저장소로 복제

# 2. fork 후, 복제된 내 원격 저장소를 로컬 저장소에 clone
$ git clone URL

# 3. 로컬 저장소와 원본 원격 저장소 동기화 하기 위해 연결
$ git remote add upstream URL

# 4. 작업할 기능에 대한 branch 생성, 기능 구현
$ git switch -c [branchname]

# 5. 기능 구현 완료되면, origin에 해당 branch push
$ git push origin [branchname]

# 6. Pull Request 통해 origin branch를 upstream의 master에 반영해달라고 요청

# 7. upstream master에 branch 병합되면 origin branch 삭제, 로컬에서 master branch로 이동
$ git switch master

# 8. 병합으로 인해 변경된 upstream master 내용을 pull, 기존 로컬 branch 삭제
$ git pull upstream master
$ git branch -d [branchname]

```

## git reset