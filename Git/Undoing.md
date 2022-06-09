# 📌Undoing

되돌리기

--------



### ✨파일 내용을 수정 전으로 되돌리기

- Modified 파일 되돌리기

#### git restore

- `git restore <파일 이름>`
- git의 추적이 되고 있는, 즉 버전 관리가 되고 있는 파일만 되돌리기 가능



1. 이미 버전 관리가 되고 있는 test.md 파일을 변경 후 저장

   ```markdown
   # test.md
   
   Hello
   World <- "World"라는 새로운 내용 추가
   -------------------------------------
   이후 저장
   ```

2. test.md는 modified 상태

   ```markdown
   $ git status
   On branch master
   Changes not staged for commit:
     (use "git add <file>..." to update what will be committed)
     (use "git restore <file>..." to discard changes in working directory)
           modified:   test.md
   
   no changes added to commit (use "git add" and/or "git commit -a")
   ```

3. `git restore`를 통해 수정 전으로 되돌림

   ```bash
   $ git restore test.md
   ```

   ```markdown
   # test.md
   
   Hello
   -------------------------------------
   World가 삭제 되면서, 수정 전으로 되돌아감
   ```



- 주의사항

  - 원래 파일로 덮어썼기 때문에 수정한 내용은 전부 사라짐
  - 한 번 `git restore`를 통해 수정을 취소하면 해당 내용을 복원할 수 없음

- git 2.23 이전 명령어

  ```bash
  $ git checkout -- <파일 이름>
  ```





### ✨파일 상태를 Unstage로 되돌리기

- `git add`를 통해 Staging Area에 올라간 파일을 다시 Unstage 상태(Working Directory)로 내리기



#### (1) git rm --cached

1. test.md 파일 생성, `git add` → Staging Area

   ```bash
   $ git init
   $ touch test.md
   $ git add test.md
   ```

   ```bash
   $ git status
   On branch master
   
   No commits yet
   
   Changes to be committed:
     (use "git rm --cached <file>..." to unstage)
           new file:   test.md
   ```

2. Staging Area에 올라간 test.md를 다시 Unstage 상태로 내리기

   ```bash
   $ git rm --cached test.md
   rm 'test.md'
   ```

   ```bash
   $ git status
   On branch master
   
   No commits yet
   
   Untracked files:
     (use "git add <file>..." to include in what will be committed)
           test.md
   
   nothing added to commit but untracked files present (use "git add" to track)
   ```



#### (2) git restore --staged

1. test.md 파일 생성, `git add`, `git commit`

```bash
$ git init
$ git touch test.md
$ git add test.md
$ git commit -m "first commit"
```

2. test.md의 내용을 변경하고 `git add`진행

```bash
# test.md 파일 변경 후
$ git add test.md
```

```bash
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   test.md
```

3. Staging Area에 올라간 test.md를 다시 Unstage 상태로 내리기

```bash
$ git restore --staged test.md
```

```bash
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   test.md

no changes added to commit (use "git add" and/or "git commit -a")
```



- Unstage로 되돌리는 명령어가 다른 이유
  1. `git rm --cached <파일 이름>`
     - 기존에 커밋이 없는 경우
     - “to unstage and remove paths only from the staging area”
  2. `git restore --staged <파일 이름>`
     - 기존에 커밋이 존재하는 경우
     - “the contents are restored from HEAD”

- git 2.23 이전 명령어

  ```bash
  $ git reset HEAD <파일 이름>
  ```





### ✨바로 직전 완료한 커밋 수정하기

#### git commit --amend

- 상황별 2가지 기능

  1. 커밋 메시지만 수정

     - 마지막으로 커밋하고 수정한 것이 없을 때

       (커밋하자마자 바로 이 명령을 실행하는 경우)

  2. 이전 커밋 덮어쓰기

     - Staging Area에 새로 올라온 내용이 있을 때



#### (1) 커밋 메시지만 수정하는 경우

1. A 기능 완성 후 커밋 → B 기능으로 잘못 작성

   ```bash
   $ git commit -m 'B feature completed'
   ```

2. 현재 커밋 해시 값 확인

   ```bash
   $ git log
   commit 56aa4ab6383deeaafde207955cc468db5bea42b1 (HEAD -> master)
   ```

3. 커밋 메시지 수정 명령어 입력

   ```bash
   $ git commit --amend
   ```

4. Vim 편집기가 열리면서 직전 커밋 메시지를 수정할 수 있음

   가장 위에 적힌 `B feature completed`가 기존의 커밋 메시지

   키보드 `i` → 키보드 화살표로 커서 이동 가능 (입력 가능 상태로 변환)

   원하는 커밋 메시지로 수정, 키보드 `esc` → 입력모드 종료

   `:wq`입력 후 `Enter`

   ```bash
   B feature completed
   
   # Please enter the commit message for your changes. Lines starting
   # with '#' will be ignored, and an empty message aborts the commit.
   #
   # Date:      Thu Jun 9 15:12:20 2022 +0900
   #
   # On branch master
   #
   # Initial commit
   #
   # Changes to be committed:
   #       new file:   test.md
   ```

5. 커밋 메시지를 수정하고 저장하면, 새로운 메시지로 변경되며 커밋 해시값 또한 변경됨

   ```bash
   $ git log
   commit 9d081ac7d64274e229b8483f00cf9ffed8b35ced (HEAD -> master)
   ```



#### (2) 커밋 재작성

- 누락된 파일이 있는 경우

1. a.md와 b.md 작성, a.md만 커밋

   ```bash
   $ touch a.md b.md
   $ git add a.md
   ```

   ```bash
   $ git status
   On branch master
   
   No commits yet
   
   Changes to be committed:
     (use "git rm --cached <file>..." to unstage)
           new file:   a.md
   
   Untracked files:
     (use "git add <file>..." to include in what will be committed)
           b.md
   ```

   ```bash
   $ git commit -m "a & b"
   [master (root-commit) b0fc6db] a & b
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 a.md
   ```

   ```bash
   $ git status
   On branch master
   Untracked files:
     (use "git add <file>..." to include in what will be committed)
           b.md
   
   nothing added to commit but untracked files present (use "git add" to track)
   ```

2. 누락된 파일을 Staging Area로 이동

   ```bash
   $ git add b.md
   
   $ git status
   On branch master
   Changes to be committed:
     (use "git restore --staged <file>..." to unstage)
           new file:   b.md
   ```

3. `git commit --amend`입력

   ```bash
   $ git commit --amend
   ```

4. Vim 편집기가 열리면서 수정 가능 (커밋 메시지도 수정 가능)

   `:wq`입력 후 `Enter`

   ```bash
   a & b
   
   # Please enter the commit message for your changes. Lines starting
   # with '#' will be ignored, and an empty message aborts the commit.
   #
   # Date:      Thu Jun 9 15:33:09 2022 +0900
   #
   # On branch master
   #
   # Initial commit
   #
   # Changes to be committed:
   #       new file:   a.md
   #       new file:   b.md
   ```

   Vim 편집기를 저장 후 종료하면 직전 커밋이 덮어 씌워짐 (커밋 새로 추가 X)

   마찬가지로 커밋 해시값 또한 변경됨

   ```bash
   $ git commit --amend
   [master e1332bc] a & b
    Date: Thu Jun 9 15:33:09 2022 +0900
    2 files changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 a.md
    create mode 100644 b.md
   ```



- `git commit --amend`는 마지막 커밋 작업에서 뭔가 빠뜨린 것을 넣거나 변경하는 것을 새 커밋으로 분리하지 않고 하나의 커밋에서 처리
- 오타 혹은 빠진 파일로 인한 추가 커밋을 생성하지 않음
- 주의사항
  - 이전의 커밋을 완전히 새로 고쳐서 새 커밋으로 변경하는 것
  - 이전의 커밋은 일어나지 않은 일이 되는 것이고, 히스토리에도 남지 않음 → 이전 커밋을 다시 볼 수 없음