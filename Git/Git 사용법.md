# 📌Git 사용법

분산 버전 관리 시스템 (DVCS, Distributed Version Control System)

------------------



### ✨Git Bash

- Command Line Interface

| 명령어       | 내용                     |
| ------------ | ------------------------ |
| pwd          | 현재 디렉토리 출력(경로) |
| cd <path>    | 디렉토리 이동            |
| ls           | 목록                     |
| mkdir <name> | 디렉토리 생성            |
| rm <name>    | 파일 삭제                |
| rm -r <name> | 폴더 삭제                |
| touch        | 빈 파일 생성             |



### ✨Git 저장소 생성

- 특정 폴더에 git 저장소 (repository)를 만들어 관리
- .git 폴더가 생성되며 master라는 표기 확인 가능

```
$ git init
```



### ✨Git 기초 흐름

- Working Directory
  - 내가 작업하고 있는 실제 디렉토리
  - `git add` 명령어를 통해 Staging Area로 이동
- Staging Area
  - 버전으로 기록하기 위한 파일 변경사항의 목록
  - `git commit` 명령어를 통해 Repository에 기록
- Repository
  - 커밋(버전)들이 기록되는 곳



### ✨기초 명령어

- git bash에 git을 입력하면 명령어 확인 가능

- git status
  - Git 저장소의 변경된 파일의 상태를 확인
    - Untracked files
      - 새로 만든 파일, 아직 관리 대상(tracked)이 아닌 파일
    - Changes not staged for commit
      - tracked 상태이지만, 수정된 파일이 staged 상태가 아님. `git add`를 실행하면 staged 상태가 됨
    - Changes to be committed
      - staged 상태, `git commit`을 실행하면 repository에 기록
    - Nothing to commit, working tree clean
      - 모든 파일이 커밋된 상태
- git log
  - 현재 저장소에 기록된 커밋 히스토리 조회

| 명령어                          | 내용                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| git init                        | 로컬 저장소 생성                                             |
| git add <파일명> 또는 git add . | 특정 파일/폴더의 변경사항 또는 모든 변경사항 추가            |
| git commit -m '<커밋메세지>'    | 커밋 (버전 기록)                                             |
| git status                      | 상태 확인                                                    |
| git log                         | 버전 확인 (자세히)                                           |
| git log --oneline               | 버전 확인 (간단히)                                           |
| git log --oneline --all         | 버전 확인 + 전체 조회 (해당 브랜치에서 실행되지 않은 커밋 포함) |
| git log --oneline --all --graph | 버전 확인 + 전체 조회 + 그래프형태                           |
| git --version                   | 깃 버전 확인                                                 |



### ✨원격 저장소

- 네트워크를 활용한 저장소
  - GitHub
  - GitLab
  - Bitbucket
- 기본 명령어

| 명령어                            | 내용                                |
| --------------------------------- | ----------------------------------- |
| git clone <url>                   | 원격저장소 복제                     |
| git remote -v                     | 원격저장소 정보 확인                |
| git remote add <원격저장소> <url> | 원격저장소 추가 (일반적으로 origin) |
| git remote rm <원격저장소>        | 원격저장소 삭제                     |
| git push <원격저장소> <브랜치>    | 원격저장소에 push                   |
| git pull <원격저장소> <브랜치>    | 원격저장소로부터 pull               |



### ✨Git Branch

![branch](https://user-images.githubusercontent.com/97656286/172760113-038cbf87-738d-4bb8-a3ad-22605621d6b5.PNG)

- 나뭇가지처럼 여러 갈래로 작업공간을 나누어 독립적으로 작업할 수 있도록 도와주는 Git의 도구

- 하나의 작업은 하나의 브랜치로 나누어 진행 → 체계적 개발 가능
- 독립적 공간에서 작업이 이루어져 원본(master 브랜치)에 대해 안전
- 문제가 생길 경우 별도의 브랜치에서 오류를 해결하기 위한 작업 실행 → master 브랜치에 영향을 주지 않기때문에 고객들의 사용(master)에도 문제 없음, 이후 브랜치에서 작업한 내용을 master에 반영 가능



### ✨Branch command

#### git branch

- 브랜치 조회, 생성, 삭제 등 브랜치와 관련된 Git 명령어

```bash
# 로컬 브랜치 목록 확인
$ git branch

# 원격 저장소의 브랜치 목록 확인
$ git branch -r

# 모든 브랜치 목록 확인
$ git branch -a

# 새로운 브랜치 생성
$ git branch <브랜치 이름>

# 특정 브랜치 삭제
$ git branch -d <브랜치 이름> # 병합된 브랜치만 삭제 가능
$ git branch -D <브랜치 이름> # 강제 삭제 (병합되지 않은 브랜치도 삭제 가능)
```

#### git switch

- 현재 브랜치에서 다른 브랜치로 HEAD를 이동시키는 명령어
  - HEAD: 현재 브랜치를 가리키는 포인터
  - 현재 브랜치의 가장 최근 커밋을 가리킴

```bash
# 브랜치 이동
$ git switch <다른 브랜치 이름>

# 새로운 브랜치 생성과 동시에 이동
$ git switch -c <브랜치 이름>
```

- git switch 주의사항

  - git switch 하기 전, 워킹 디렉토리 파일이 모두 버전 관리가 되고 있는지 확인
- Git의 브랜치는 Git이 관리하는 파일 트리에 한해서 독립적인 작업 공간을 가짐
  - Staging Area (`git add`)에 있지 않은 파일은 관리 대상이 아니기 때문에 브랜치가 바뀌어도 유지됨

- git 2.23부터 기존의 `git checkout <브랜치 이름>`을 대체하기 위해 도입

  - checkout → switch + restore

  ```bash
  # 기존 명령어
  # 브랜치 이동
  $ git checkout <브랜치 이름>
  
  # 브랜치 생성과 동시에 이동
  $ git checkout -b <브랜치 이름>
  ```



### ✨Branch Merge

#### git merge

- 분기된 브랜치들을 하나로 합치는 명령어
- merge 하기 전, 다른 브랜치를 합치려고 하는 메인 브랜치로 이동(switch)

```bash
# 브랜치 병합
$ git merge <합칠 브랜치 이름>

# 현재 branch1과 branch2가 있고, HEAD가 가리키는 곳이 branch1일 때
$ git branch
* branch1
  branch2

# branch2를 branch1에 병합
$ git merge branch2

# branch1을 branch2에 병합
$ git switch branch2
$ git merge branch1
```



### ✨Merge의 세 종류

#### 1. Fast-Forward

- 브랜치를 병합할 때 마치 빨리감기처럼 브랜치가 가리키는 커밋을 앞으로 이동시키는 것

1. 현재 master는 C2 커밋을, hotfix는 C4 커밋을 가리킴

![Fast-Forward1](https://user-images.githubusercontent.com/97656286/172760150-4aa9b73b-592c-4861-9e5c-c7e87d6f0b1b.PNG)

2. master에 hotfix를 병합

   ```bash
   $ git switch master
   $ git merge hotfix
   ```

3. hotfix가 가리키는 C4는 C2에 기반한 커밋이므로, master가 C4에 이동
   이렇게 따로 merge 과정 없이 브랜치의 포인터가 이동하는 것을 Fast-Forward라고 함

![Fast-Forward2](https://user-images.githubusercontent.com/97656286/172760218-ab1c926d-55f4-43f9-8fd2-cd8aa3b798df.PNG)

4. 병합이 완료된 hotfix는 더 이상 필요 없으므로 삭제

   ```bash
   $ git branch -d hotfix
   ```



#### 2. 3-Way Merge (Merge commit)

- 각 브랜치의 커밋 두 개와 공통 조상 하나를 사용하여 병합
- 두 브랜치에서 `다른 파일` 혹은 `같은 파일의 다른 부분`을 수정했을 때 가능

1. 현재 master는 C4 커밋을, iss53은 C5 커밋을 가리킴
   master와 iss53의 공통 조상은 C2 커밋

![3-Way Merge1](https://user-images.githubusercontent.com/97656286/172760254-c80a7cb6-c94b-4f9c-bac5-d11fba528739.PNG)

2. master에 iss53을 병합

   ```bash
   $ git switch master
   $ git merge iss53
   ```

3. master와 iss53은 갈래가 나누어져 있기 때문에 Fast-Forward로 합쳐질 수 없음
   따라서 공통 조상인 C2와 각자가 가리키는 커밋인 C4, C5를 비교하여 `3-way merge`를 진행

![3-Way Merge2](https://user-images.githubusercontent.com/97656286/172760303-ab86fb8e-fd6c-41cd-97bb-8a02af36af12.PNG)

4. 이때 생긴 C6는 master와 iss53이 병합되면서 발생한 Merge Commit

5. 병합이 완료된 iss53은 더 이상 필요 없으므로 삭제

   ```bash
   $ git branch -d iss53
   ```



#### 3. Merge Conflict

- 병합하는 두 브랜치에서 `같은 파일의 같은 부분`을 수정한 경우, Git이 어느 브랜치의 내용으로 작성해야 하는지 판단하지 못해 발생하는 충돌(Conflict) 현상
- 사용자가 직접 내용을 선택해서 Conflict를 해결

1. 현재 master는 C4 커밋을, iss53은 C5 커밋을 가리킴
   master와 iss53의 공통 조상은 C2 커밋

![Merge Conflict1](https://user-images.githubusercontent.com/97656286/172760342-dd0eddc2-8c87-4887-b3c7-6ed211a1590f.PNG)

2. master와 iss53이 같은 파일의 같은 부분을 수정하고 병합하면 충돌 발생

   ```bash
   $ git switch master
   $ git merge iss53
   Auto-merging test.md
   CONFLICT (content): Merge conflict in test.md
   Automatic merge failed; fix conflicts and then commit the result.
   ```

3. 충돌이 일어난 파일을 확인하기 위해 `git status`를 입력

   ```bash
   $ git status
   On branch master
   You have unmerged paths.
     (fix conflicts and run "git commit")
     (use "git merge --abort" to abort the merge)
   
   Unmerged paths:
     (use "git add <file>..." to mark resolution)
   
       both modified:      test.md
   
   no changes added to commit (use "git add" and/or "git commit -a")
   ```

4. `test.md`을 열어보면 아래와 같이 충돌 내역을 볼 수 있음

   ```markdown
   <<<<<<< HEAD (Current Change)
   이것은 master에서 작성한 코드입니다.
   =======
   이것은 iss53에서 작성한 코드입니다.
   >>>>>>> iss53 (Incoming Change)
   ```

5. `=======` 를 기준으로 위는 master의 내용, 아래는 iss53의 내용

   이 중 하나를 선택할 수도 있고, 둘 다 선택할 수도 있고, 아예 새롭게 작성할 수도 있음

   ```markdown
   충돌을 해결해보자!

6. 이후 `git add`와 `git commit`을 통해 병합한 내용 커밋 가능

   이 단계에서 별도의 커밋 메세지 작성 X

   ```bash
   $ git add .
   $ git commit
   ```

7. Vim 편집기가 켜지며 커밋 내역 수정 가능

   가장 위에 적힌 `Merge branch 'iss53'`가 커밋 메세지

   (수정을 마치거나 수정할 것이 더이상 없을 경우 `esc` 를 누른후`:wq`를 입력하여 저장 & 종료)

   ```bash
   Merge branch 'iss53'
   
   Conflicts:
       test.md
   #
   # It looks like you may be committing a merge.
   # If this is not correct, please remove the file
   #	.git/MERGE_HEAD
   # and try again.
   
   
   # Please enter the commit message for your changes. Lines starting
   # with '#' will be ignored, and an empty message aborts the commit.
   # On branch master
   # All conflicts fixed but you are still merging.
   #

8. 병합이 완료된 iss53은 더 이상 필요 없으므로 삭제

   ```bash
   $ git branch -d iss53
   ```

