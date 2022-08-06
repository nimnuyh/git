# **TIL Git Github .gitignore, clone, pull**

> 2022년 07월 26일 화요일

## .gitignore

> 특정 파일 혹은 폴더에 대해 Git이 버전 관리를 하지 못하도록 지정하는 것

### .gitignore에 작성하는 목록

- 민감한 개인 정보가 담긴 파일
- OS에서 활용되는 파일
- IDE, Text editor 등에서 활용되는 파일
- 개발 언어, 프레임워크 등에서 사용되는 파일

### .gitignore 작성 시 주의 사항

- 반드시 이름을 .gitignore로 작성(점(.)은 숨김 파일이라는 뜻)
- .gitignore 파일은 .git 폴더와 동일한 위치에 생성
- 제외 하고 싶은 파일은 반드시 git add 전에 .gitignore에 작성

### 참고 자료

- [gitignore.io](https://www.toptal.com/developers/gitignore/)

- [gitignore 저장소](https://github.com/github/gitignore)
  
### .gitignore 작성 규칙

1. 아무것도 없는 라인이나, `#`로 시작하는 라인은 무시
2. '/`로 시작하면 하위 디렉터리에 재귀적으로 적용되지 않음
3. 디렉터리는 `/`를 끝에 사용하는 것으로 표현
4. `!`로 시작하는 패턴의 파일은 ignore하지 않음
5. 표준 Glob 패턴 사용
   - `*`는 문자가 하나도 없거나 하나 이상을 의미
   - `[abc]`는 중괄호 안에 있는 문자 중 하나를 의미
   - `?`는 문자 하나를 의미
   - `[0-9]`처럼 중괄호 안에 -이 있는 경우 0에서 9사이의 문자 중 하나를 의미
   - `**`는 디렉터리 내부의 디렉터리까지 지정할 수 있음<br>(`a/**/z`라고 작성하면 `a/z`, `a/b/z`, `a/b/c/z` 까지 모두 영향을 끼침)

---

## 원격 저장소 가져오기

### git clone

- 원격 저장소의 커밋 내역을 모두 가져와서 로컬 저장소를 생성
- git clone을 통해 생성된 로컬 저장소는 git init과 git remote add가 이미 수행되어 있음
- 처음에 한 번만 실행

ex)
```git bash
$ git clone URL
```

### git pull

- 원격 저장소의 변경 사항을 가져와서, 로컬 저장소를 업데이트하는 명령어

ex)
```git bash
$ git pull origin [branch]
```
