# 📌Git Workflow

Github flow

--------------------------------------------



### ✨Feature Branch Workflow

- Shared repository model (저장소의 소유권이 있는 경우)



#### Workflow

1. 각 사용자는 원격 저장소의 소유권을 가진 상태

   ```markdown
   1번 유저, 2번 유저, 3번 유저 Collaborators에 추가
   ```

2. clone을 통해 저장소를 로컬에 복제

   ```bash
   git clone <원격저장소 주소>
   ```

3. 기능 추가를 위해 각자 브랜치 생성 및 기능 구현 

   - master에서 구현 X, master는 병합할 때만 사용

   ```markdown
   1번 유저: feature/login
   2번 유저: feature/signup
   3번 유저: feature/profile
   ```

   ```bash
   # 1번 유저의 경우
   $ git switch -c feature/login  # 브랜치 생성, 이동
   $ touch login.md  # 기능 구현
   $ git add .
   $ git commit -m "login completed"
   ```

4. 기능 구현 후 `git push <원격저장소 이름> <브랜치 이름>`

   ```bash
   # 원격저장소 이름이 origin일 경우
   # 1번 유저
   $ git push origin feature/login
   
   # 2번 유저
   $ git push origin feature/signup
   
   # 3번 유저
   $ git push origin feature/profile
   ```

5. Pull Request

   - `Compare & pull request` 버튼
   - 요청을 하면 Pull requests 목록에 대기

6. 병합 & 병합 완료된 브랜치 삭제

   - 커밋과 변경된 부분 확인 후 `merge` 버튼 또는 잘못된 부분이 있다면 `close` 버튼

   - `merge` 버튼 클릭 후 `Delete branch` 버튼

     → 원격 저장소의 master branch 버전은 이동, 각 유저의 로컬 master branch 버전은 이동 X

     → repository의 소유권을 가진 유저가 merge 후 반드시 모든 유저에게 알려야 함

7. 각 유저는 master 브랜치로 이동, 병합된 master의 내용을 pull

   ```bash
   $ git switch master
   $ git pull origin master
   ```

8. 각 유저는 원격 저장소에서 병합 완료된 로컬 브랜치 삭제

   ```bash
   $ git branch -d feature/login
   ```





### ✨Forking Workflow

- Fork & Pull model (저장소의 소유권이 없는 경우)
- 오픈소스



#### Workflow

1. 소유권이 없는 원격저장소를 fork를 통해 내 원격저장소로 복제

2. 복제한 것을 clone (이때 원격저장소 이름은 origin으로 설정됨)

   ```bash
   $ git clone <복제한 원격저장소 주소>
   ```

3. 추후 로컬 저장소를 원본 원격 저장소와 동기화하기 위해 원본에 대해서도 URL 연결

   - upstream: 일반적으로 지정하는 원본 원격저장소 이름

   ```bash
   $ git remote add upstream <원본 원격저장소 URL>
   ```

4. 기능 추가를 위해 브랜치 생성 및 기능 구현

   ```bash
   $ git switch -c feature/login
   $ touch login.md
   $ git add .
   $ git commit -m "fixed login.md"
   ```

5. 기능 구현 후 복제한 원격저장소(origin)에 브랜치 반영

   - 원본 원격저장소(upstream)에는 소유권이 없기 때문에 push 불가능

   ```bash
   $ git push origin feature/login
   ```

6. 복제한 원격저장소(origin)에서 원본 원격저장소(upstream)로 pull request

   → 원본 원격저장소의 Pull requests 목록에 대기

7. 원본 원격저장소(upstream)에서 병합완료 

   → 병합 완료된 복제 원격저장소(origin)의 브랜치 삭제

   → 로컬에서 master 브랜치로 switch, 원본 원격저장소(upstream)를 pull

   ```bash
   $ git switch master
   $ git pull upstream master
   ```

8. 원격저장소에서 병합 완료된 로컬 브랜치 삭제

   ```bash
   $ git branch -d feature/login
   ```

   