# Git 한글깨짐



### ✨git status 한글깨짐

- 문제상황

  - `git status` 명령어를 통해 git 상태를 확인하면 한글이 깨지는 경우

- 해결방안

  ```bash
  git config --global core.quotepath false
  ```

  - 위 명령어 입력
  - `core.quotepath`는 0x80보다 큰 바이트 문자를 unusual로 판단하여 `\302\265` 처럼 문자가 깨지게 됨
  - 기본 설정은 `true`
  - `false`로 설정하면 한글깨짐 현상을 해결할 수 있음
  - [공식문서](https://git-scm.com/docs/git-config#Documentation/git-config.txt-corequotePath)