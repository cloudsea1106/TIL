# ๐GitLab์์ GitHub ๋ณต์ฌํ๊ธฐ

์๋, ๋ธ๋์น, ์ปค๋ฐ๋ก๊ทธ๊น์ง ํจ๊ป ๋ณต์ฌ ๊ฐ๋ฅ

GITLAB์ ์๋ณธ์ด ์ฌ๋ผ์ง์ง ์์

-------------------------------------



### โจ๋ณต์ฌํ๊ธฐ

GitLab๊ณผ GitHub์ ์ด๋ฉ์ผ์ด ๋ค๋ฅด๋ค๋ฉด ๋ฏธ๋ฆฌ `[Settings]-[Emails]-[Add email address]`์์ ์ด๋ฉ์ผ ์ถ๊ฐ

1. ํฐ๋ฏธ๋ ์ด๊ธฐ (์์น ์๊ด ์์)

2. ๋ณต์ฌํ  GitLab ์ ์ฅ์๋ฅผ bare clone

   ```bash
   $ git clone --bare https://gitlab.com/<์ ์  ์์ด๋>/<GitLab ์ ์ฅ์ ์ด๋ฆ>.git
   
   # https://gitlab.com/<์ ์  ์์ด๋>/<GitLab ์ ์ฅ์ ์ด๋ฆ>.git ์ฃผ์๋ GitLab ์ ์ฅ์ ์ฃผ์
   ```

3. ์๋ก์ด GitHub ์ ์ฅ์๋ก mirror push

   - GitHub์ ๋จผ์  ์๋ก์ด ์ ์ฅ์ ์์ฑํด๋๊ธฐ

   ```bash
   # ๋จผ์ , ์ด๋์ํฌ ์ ์ฅ์๋ก ์ด๋
   $ cd <GitLab ์ ์ฅ์ ์ด๋ฆ>.git
   
   # mirror push
   $ git push --mirror https://github.com/<์ ์  ์์ด๋>/<GitHub ์ ์ฅ์ ์ด๋ฆ>.git
   ```

4. GitLab์์ ๋ก์ปฌ์ bare clone ํ ์ ์ฅ์ ํด๋ ์ญ์ 





### โจbare, mirror

[๊ณต์๋ฌธ์ ์ฐธ๊ณ ](https://git-scm.com/docs/git-clone#Documentation/git-clone.txt---bare)

- bare
  - Make a *bare* Git repository. That is, instead of creating `<directory>` and placing the administrative files in `<directory>/.git`, make the `<directory>` itself the `$GIT_DIR`. This obviously implies the `--no-checkout` because there is nowhere to check out the working tree. Also the branch heads at the remote are copied directly to corresponding local branch heads, without mapping them to `refs/remotes/origin/`. When this option is used, neither remote-tracking branches nor the related configuration variables are created.
  - bare ๊น ๋ ํฌ์งํ ๋ฆฌ๋ฅผ ์์ฑ
  - `<directory>`๋ฅผ ์์ฑํ๊ณ  `<directory>/.git`์ ๊ด๋ฆฌํ์ผ์ ๋ฐฐ์นํ๋ ๊ฒ ๋์ ์, `<directory>` ์์ฒด๋ฅผ `$GIT_DIR` ๋ก ์์ฑ
  - working tree๋ฅผ ์ฒดํฌ์์ ํ  ๊ณณ์ด ์๊ธฐ ๋๋ฌธ์ `--no-checkout`์ ํฌํจ
  - ์๊ฒฉ ์ ์ฅ์์ branch heads๋ ์ด์ ์์ํ๋ ๋ก์ปฌ branch heads์ `refs/remotes/origin/`๋งคํ ์์ด ๋ฐ๋ก ๋ณต์ฌ๋จ
  - ์๊ฒฉ ์ถ์  ๋ธ๋์น์ ๊ด๋ จ ํ๊ฒฝ์ค์  ๋ณ์๋ ์์ฑ๋์ง ์์



- mirror

  - Set up a mirror of the source repository. This implies `--bare`. Compared to `--bare`, `--mirror` not only maps local branches of the source to local branches of the target, it maps all refs (including remote-tracking branches, notes etc.) and sets up a refspec configuration such that all these refs are overwritten by a `git remote update` in the target repository.

  - ์๋ณธ ์ ์ฅ์์ mirror๋ฅผ ์ค์ 

  - `--bare` ์ต์์ ํฌํจ
  - ์๋ณธ์ ๋ก์ปฌ ๋ธ๋์น๋ฅผ ํ๊ฒ์ ๋ก์ปฌ ๋ธ๋์น์ ๋งคํ
  - ์๊ฒฉ ์ถ์  ๋ธ๋์น, notes ๋ฑ์ ํฌํจํ ๋ชจ๋  refs ๋งคํ
  - refspec configuration์ ์ค์ ํ์ฌ ๋ชจ๋  refs๋ ํ๊ฒ ์ ์ฅ์์์ `git remote update`๋ฅผ ํตํด overwritten๋จ