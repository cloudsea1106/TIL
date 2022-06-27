# 📌GitLab에서 GitHub 복사하기

잔디, 브랜치, 커밋로그까지 함께 복사 가능

GITLAB의 원본이 사라지지 않음

-------------------------------------



### ✨복사하기

GitLab과 GitHub의 이메일이 다르다면 미리 `[Settings]-[Emails]-[Add email address]`에서 이메일 추가

1. 터미널 열기 (위치 상관 없음)

2. 복사할 GitLab 저장소를 bare clone

   ```bash
   $ git clone --bare https://gitlab.com/<유저 아이디>/<GitLab 저장소 이름>.git
   
   # https://gitlab.com/<유저 아이디>/<GitLab 저장소 이름>.git 주소는 GitLab 저장소 주소
   ```

3. 새로운 GitHub 저장소로 mirror push

   - GitHub에 먼저 새로운 저장소 생성해두기

   ```bash
   # 먼저, 이동시킬 저장소로 이동
   $ cd <GitLab 저장소 이름>.git
   
   # mirror push
   $ git push --mirror https://github.com/<유저 아이디>/<GitHub 저장소 이름>.git
   ```

4. GitLab에서 로컬에 bare clone 한 저장소 폴더 삭제





### ✨bare, mirror

[공식문서 참고](https://git-scm.com/docs/git-clone#Documentation/git-clone.txt---bare)

- bare
  - Make a *bare* Git repository. That is, instead of creating `<directory>` and placing the administrative files in `<directory>/.git`, make the `<directory>` itself the `$GIT_DIR`. This obviously implies the `--no-checkout` because there is nowhere to check out the working tree. Also the branch heads at the remote are copied directly to corresponding local branch heads, without mapping them to `refs/remotes/origin/`. When this option is used, neither remote-tracking branches nor the related configuration variables are created.
  - bare 깃 레포지토리를 생성
  - `<directory>`를 생성하고 `<directory>/.git`에 관리파일을 배치하는 것 대신에, `<directory>` 자체를 `$GIT_DIR` 로 생성
  - working tree를 체크아웃 할 곳이 없기 때문에 `--no-checkout`을 포함
  - 원격 저장소의 branch heads는 이에 상응하는 로컬 branch heads에 `refs/remotes/origin/`매핑 없이 바로 복사됨
  - 원격 추적 브랜치와 관련 환경설정 변수는 생성되지 않음



- mirror

  - Set up a mirror of the source repository. This implies `--bare`. Compared to `--bare`, `--mirror` not only maps local branches of the source to local branches of the target, it maps all refs (including remote-tracking branches, notes etc.) and sets up a refspec configuration such that all these refs are overwritten by a `git remote update` in the target repository.

  - 원본 저장소의 mirror를 설정

  - `--bare` 옵션을 포함
  - 원본의 로컬 브랜치를 타겟의 로컬 브랜치에 매핑
  - 원격 추적 브랜치, notes 등을 포함한 모든 refs 매핑
  - refspec configuration을 설정하여 모든 refs는 타겟 저장소에서 `git remote update`를 통해 overwritten됨