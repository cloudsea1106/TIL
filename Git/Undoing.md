# ๐Undoing

๋๋๋ฆฌ๊ธฐ

--------



### โจํ์ผ ๋ด์ฉ์ ์์  ์ ์ผ๋ก ๋๋๋ฆฌ๊ธฐ

- Modified ํ์ผ ๋๋๋ฆฌ๊ธฐ

#### git restore

- `git restore <ํ์ผ ์ด๋ฆ>`
- git์ ์ถ์ ์ด ๋๊ณ  ์๋, ์ฆ ๋ฒ์  ๊ด๋ฆฌ๊ฐ ๋๊ณ  ์๋ ํ์ผ๋ง ๋๋๋ฆฌ๊ธฐ ๊ฐ๋ฅ



1. ์ด๋ฏธ ๋ฒ์  ๊ด๋ฆฌ๊ฐ ๋๊ณ  ์๋ test.md ํ์ผ์ ๋ณ๊ฒฝ ํ ์ ์ฅ

   ```markdown
   # test.md
   
   Hello
   World <- "World"๋ผ๋ ์๋ก์ด ๋ด์ฉ ์ถ๊ฐ
   -------------------------------------
   ์ดํ ์ ์ฅ
   ```

2. test.md๋ modified ์ํ

   ```markdown
   $ git status
   On branch master
   Changes not staged for commit:
     (use "git add <file>..." to update what will be committed)
     (use "git restore <file>..." to discard changes in working directory)
           modified:   test.md
   
   no changes added to commit (use "git add" and/or "git commit -a")
   ```

3. `git restore`๋ฅผ ํตํด ์์  ์ ์ผ๋ก ๋๋๋ฆผ

   ```bash
   $ git restore test.md
   ```

   ```markdown
   # test.md
   
   Hello
   -------------------------------------
   World๊ฐ ์ญ์  ๋๋ฉด์, ์์  ์ ์ผ๋ก ๋๋์๊ฐ
   ```



- ์ฃผ์์ฌํญ

  - ์๋ ํ์ผ๋ก ๋ฎ์ด์ผ๊ธฐ ๋๋ฌธ์ ์์ ํ ๋ด์ฉ์ ์ ๋ถ ์ฌ๋ผ์ง
  - ํ ๋ฒ `git restore`๋ฅผ ํตํด ์์ ์ ์ทจ์ํ๋ฉด ํด๋น ๋ด์ฉ์ ๋ณต์ํ  ์ ์์

- git 2.23 ์ด์  ๋ช๋ น์ด

  ```bash
  $ git checkout -- <ํ์ผ ์ด๋ฆ>
  ```





### โจํ์ผ ์ํ๋ฅผ Unstage๋ก ๋๋๋ฆฌ๊ธฐ

- `git add`๋ฅผ ํตํด Staging Area์ ์ฌ๋ผ๊ฐ ํ์ผ์ ๋ค์ Unstage ์ํ(Working Directory)๋ก ๋ด๋ฆฌ๊ธฐ



#### (1) git rm --cached

1. test.md ํ์ผ ์์ฑ, `git add` โ Staging Area

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

2. Staging Area์ ์ฌ๋ผ๊ฐ test.md๋ฅผ ๋ค์ Unstage ์ํ๋ก ๋ด๋ฆฌ๊ธฐ

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

1. test.md ํ์ผ ์์ฑ, `git add`, `git commit`

```bash
$ git init
$ git touch test.md
$ git add test.md
$ git commit -m "first commit"
```

2. test.md์ ๋ด์ฉ์ ๋ณ๊ฒฝํ๊ณ  `git add`์งํ

```bash
# test.md ํ์ผ ๋ณ๊ฒฝ ํ
$ git add test.md
```

```bash
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   test.md
```

3. Staging Area์ ์ฌ๋ผ๊ฐ test.md๋ฅผ ๋ค์ Unstage ์ํ๋ก ๋ด๋ฆฌ๊ธฐ

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



- Unstage๋ก ๋๋๋ฆฌ๋ ๋ช๋ น์ด๊ฐ ๋ค๋ฅธ ์ด์ 
  1. `git rm --cached <ํ์ผ ์ด๋ฆ>`
     - ๊ธฐ์กด์ ์ปค๋ฐ์ด ์๋ ๊ฒฝ์ฐ
     - โto unstage and remove paths only from the staging areaโ
  2. `git restore --staged <ํ์ผ ์ด๋ฆ>`
     - ๊ธฐ์กด์ ์ปค๋ฐ์ด ์กด์ฌํ๋ ๊ฒฝ์ฐ
     - โthe contents are restored from HEADโ

- git 2.23 ์ด์  ๋ช๋ น์ด

  ```bash
  $ git reset HEAD <ํ์ผ ์ด๋ฆ>
  ```





### โจ๋ฐ๋ก ์ง์  ์๋ฃํ ์ปค๋ฐ ์์ ํ๊ธฐ

#### git commit --amend

- ์ํฉ๋ณ 2๊ฐ์ง ๊ธฐ๋ฅ

  1. ์ปค๋ฐ ๋ฉ์์ง๋ง ์์ 

     - ๋ง์ง๋ง์ผ๋ก ์ปค๋ฐํ๊ณ  ์์ ํ ๊ฒ์ด ์์ ๋

       (์ปค๋ฐํ์๋ง์ ๋ฐ๋ก ์ด ๋ช๋ น์ ์คํํ๋ ๊ฒฝ์ฐ)

  2. ์ด์  ์ปค๋ฐ ๋ฎ์ด์ฐ๊ธฐ

     - Staging Area์ ์๋ก ์ฌ๋ผ์จ ๋ด์ฉ์ด ์์ ๋



#### (1) ์ปค๋ฐ ๋ฉ์์ง๋ง ์์ ํ๋ ๊ฒฝ์ฐ

1. A ๊ธฐ๋ฅ ์์ฑ ํ ์ปค๋ฐ โ B ๊ธฐ๋ฅ์ผ๋ก ์๋ชป ์์ฑ

   ```bash
   $ git commit -m 'B feature completed'
   ```

2. ํ์ฌ ์ปค๋ฐ ํด์ ๊ฐ ํ์ธ

   ```bash
   $ git log
   commit 56aa4ab6383deeaafde207955cc468db5bea42b1 (HEAD -> master)
   ```

3. ์ปค๋ฐ ๋ฉ์์ง ์์  ๋ช๋ น์ด ์๋ ฅ

   ```bash
   $ git commit --amend
   ```

4. Vim ํธ์ง๊ธฐ๊ฐ ์ด๋ฆฌ๋ฉด์ ์ง์  ์ปค๋ฐ ๋ฉ์์ง๋ฅผ ์์ ํ  ์ ์์

   ๊ฐ์ฅ ์์ ์ ํ `B feature completed`๊ฐ ๊ธฐ์กด์ ์ปค๋ฐ ๋ฉ์์ง

   ํค๋ณด๋ `i` โ ํค๋ณด๋ ํ์ดํ๋ก ์ปค์ ์ด๋ ๊ฐ๋ฅ (์๋ ฅ ๊ฐ๋ฅ ์ํ๋ก ๋ณํ)

   ์ํ๋ ์ปค๋ฐ ๋ฉ์์ง๋ก ์์ , ํค๋ณด๋ `esc` โ ์๋ ฅ๋ชจ๋ ์ข๋ฃ

   `:wq`์๋ ฅ ํ `Enter`

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

5. ์ปค๋ฐ ๋ฉ์์ง๋ฅผ ์์ ํ๊ณ  ์ ์ฅํ๋ฉด, ์๋ก์ด ๋ฉ์์ง๋ก ๋ณ๊ฒฝ๋๋ฉฐ ์ปค๋ฐ ํด์๊ฐ ๋ํ ๋ณ๊ฒฝ๋จ

   ```bash
   $ git log
   commit 9d081ac7d64274e229b8483f00cf9ffed8b35ced (HEAD -> master)
   ```



#### (2) ์ปค๋ฐ ์ฌ์์ฑ

- ๋๋ฝ๋ ํ์ผ์ด ์๋ ๊ฒฝ์ฐ

1. a.md์ b.md ์์ฑ, a.md๋ง ์ปค๋ฐ

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

2. ๋๋ฝ๋ ํ์ผ์ Staging Area๋ก ์ด๋

   ```bash
   $ git add b.md
   
   $ git status
   On branch master
   Changes to be committed:
     (use "git restore --staged <file>..." to unstage)
           new file:   b.md
   ```

3. `git commit --amend`์๋ ฅ

   ```bash
   $ git commit --amend
   ```

4. Vim ํธ์ง๊ธฐ๊ฐ ์ด๋ฆฌ๋ฉด์ ์์  ๊ฐ๋ฅ (์ปค๋ฐ ๋ฉ์์ง๋ ์์  ๊ฐ๋ฅ)

   `:wq`์๋ ฅ ํ `Enter`

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

   Vim ํธ์ง๊ธฐ๋ฅผ ์ ์ฅ ํ ์ข๋ฃํ๋ฉด ์ง์  ์ปค๋ฐ์ด ๋ฎ์ด ์์์ง (์ปค๋ฐ ์๋ก ์ถ๊ฐ X)

   ๋ง์ฐฌ๊ฐ์ง๋ก ์ปค๋ฐ ํด์๊ฐ ๋ํ ๋ณ๊ฒฝ๋จ

   ```bash
   $ git commit --amend
   [master e1332bc] a & b
    Date: Thu Jun 9 15:33:09 2022 +0900
    2 files changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 a.md
    create mode 100644 b.md
   ```



- `git commit --amend`๋ ๋ง์ง๋ง ์ปค๋ฐ ์์์์ ๋ญ๊ฐ ๋น ๋จ๋ฆฐ ๊ฒ์ ๋ฃ๊ฑฐ๋ ๋ณ๊ฒฝํ๋ ๊ฒ์ ์ ์ปค๋ฐ์ผ๋ก ๋ถ๋ฆฌํ์ง ์๊ณ  ํ๋์ ์ปค๋ฐ์์ ์ฒ๋ฆฌ
- ์คํ ํน์ ๋น ์ง ํ์ผ๋ก ์ธํ ์ถ๊ฐ ์ปค๋ฐ์ ์์ฑํ์ง ์์
- ์ฃผ์์ฌํญ
  - ์ด์ ์ ์ปค๋ฐ์ ์์ ํ ์๋ก ๊ณ ์ณ์ ์ ์ปค๋ฐ์ผ๋ก ๋ณ๊ฒฝํ๋ ๊ฒ
  - ์ด์ ์ ์ปค๋ฐ์ ์ผ์ด๋์ง ์์ ์ผ์ด ๋๋ ๊ฒ์ด๊ณ , ํ์คํ ๋ฆฌ์๋ ๋จ์ง ์์ โ ์ด์  ์ปค๋ฐ์ ๋ค์ ๋ณผ ์ ์์