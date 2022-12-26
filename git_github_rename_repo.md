# **Git Github Rename Repository**

1. Github Repository Setting에서 Repository Name 변경
2. 로컬 저장소 url 확인
```git bash
$ git remote -v
```
3. 로컬 저장소 url 변경
```git bash
$ git remote set-url origin new_url
```