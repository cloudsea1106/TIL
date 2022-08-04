# 📌지워진 Git 원격 저장소 브랜치 로컬에 반영하기

원격 저장소에서는 삭제되었지만 로컬에는 남아있는 브랜치 삭제하기

--------------



### ✨로컬에 반영하기

```bash
$ git fetch --prune
$ git fetch --all && git remote prune
# 원격 저장소의 브랜치,데이터를 가져오고 가지치기
# 또는
$ git remote prune origin
# 가지치기만 하고 원격 저장소의 브랜치,데이터는 가져오지 않음

$ git remote prune origin --dry-run
# 수행될 작업 미리보기
```





### ✨자동으로 로컬에 반영하기

- [공식문서](https://github.com/git/git/commit/737c5a9cde708d6995c765b7c2e95033edd0a896)

```bash
$ git config remote.<name>.prune true
# $ git config remote.origin.prune true
# 또는
$ git config --global fetch.prune true
```





### ✨merge 후 로컬브랜치 삭제하기

```bash
$ git branch -d <브랜치명>
```



