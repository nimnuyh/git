# **TIL Git Github reset, revert, undoing**

> 2022년 07월 27일 수요일

## git reset

> 특정 commit 상태로 되돌림

```git bash
$ git reset [옵션] [commitid]
```

### 옵션
1. --mixed
   - 기본값
   - reset 시점 이후 commit된 파일들을 working directory로 돌려놓음 (add 하기 전 상태)
2. --soft
   - reset 시점 이후 commit된 파일들을 staging area로 돌려놓음 (commit 하기 전 상태)
3. --hard
   - reset 시점 이후 commit된 파일들을 모두 working directory에서 삭제
   - 삭제한 commit으로 다시 돌아가고 싶다면 git reflog를 사용

## git revert

> 특정 사건을 없었던 일로 만드는 행위, 이전 commit을 취소한다는 새로운 commit을 만듦

```git bash
$ git revert [commitid]
```

## Undoing

### git restore

> 파일 내용 수정 전으로 되돌리기

```git bash
$ git restore [filename]
```

*!!! git restore로 수정 취소하면, 해당 내용 복원할 수 없음 !!!*

### git rm --cached / git restore --staged 

> git add하여 Staging Area에 올린 파일 다시 Unstage

```git bash
# root-commit이 없는 경우 사용 (로컬 저장소에 commit이 1개도 없는 경우)
$ git rm --cached [filename]

# 로컬 저장소에 commit이 1개 이상 있는 경우 사용
$ git restore --staged [filename]
```

### git commit --amend

> 바로 직전 commit 수정

1. Staging Area에 새로 올라온 내용이 없다면, 단순히 직전 commit의 메시지만 수정
2. Staging Area에 새로 올라온 내용이 있다면, 직전 commit 내역에 같이 묶어 다시 commit