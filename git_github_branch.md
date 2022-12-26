# **Git Github branch**

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