# 📌Reset & Revert

공통점

- 과거로 되돌림

차이점

- 과거로 되돌리겠다는 내용도 기록되는가 → 커밋 이력에 남는가

-------------------------



### ✨git reset

![reset](https://user-images.githubusercontent.com/97656286/172846390-22807660-7c36-4d66-91de-e5326dd44ba5.PNG)

- 이전 커밋으로 돌아가고, 돌아간 커밋 이후의 내역은 사라짐



#### 명령어

```bash
$ git reset [옵션] <커밋 ID>
```

- 특정 커밋 상태로 되돌아감
- 특정 커밋으로 되돌아갔을 때, 해당 커밋 이후로 쌓았던 커밋들은 전부 사라짐
- 커밋 ID는 `git log` 또는 `git log --oneline`을 했을 때 나오는 해시값



#### 옵션

- 옵션은 세 종류가 있으며, 생략시 `--mixed`가 기본 값

1. `--soft`
   - 돌아가려는 커밋으로 되돌아가고
   - 이후의 커밋된 파일들을 `Staging Area`로 돌려놓음 (commit 하기 전 상태)
   - 다시 커밋할 수 있는 상태가 됨
2. `--mixed`
   - 돌아가려는 커밋으로 되돌아가고
   - 이후의 커밋된 파일들을 `Working Directory`로 돌려놓음 (add 하기 전 상태)
   - Unstage 상태가 됨
   - 옵션 생략시 기본 값
3. `--hard`
   - 돌아가려는 커밋으로 되돌아가고
   - 이후의 커밋된 파일들(tracked 파일들)은 모두 `Working Directory`에서 삭제
   - 단, Untracked 파일은 그대로 Untracked 상태로 유지됨 (soft와 mixed도 Untracked 파일 유지)



#### git reflog

- 이미 삭제한 커밋으로 다시 돌아가고 싶을 때 사용
- `git reflog` 명령어는 HEAD가 이전에 가리켰던 모든 커밋을 보여줌
- 따라서 `--hard` 옵션을 통해 지워진 커밋도 `reflog`로 조회하여 돌아갈 수 있음

```bash
$ git reflog
1bc5c4e (HEAD -> master) HEAD@{0}: reset: moving to 1bc5c4e
3d60ece HEAD@{1}: commit: third
c282e61 HEAD@{2}: commit: second
1bc5c4e (HEAD -> master) HEAD@{3}: commit (initial): first
```

```bash
$ git reset --hard <복구하고자 하는 커밋 ID>
```





### ✨git revert

![revert](https://user-images.githubusercontent.com/97656286/172846976-252321c1-6d3e-4247-b04b-7c65eea99193.PNG)

- 이전 커밋을 취소했다는 새로운 커밋을 생성, 이전 커밋은 그대로 유지

- `git reset`은 쉽게 과거로 돌아갈 수 있지만 커밋 내역이 삭제됨

  → 다른 사람과 협업할 때 커밋 내역의 차이로 인해 충돌이 발생할 수 있음



#### 명령어

```bash
$ git revert <커밋 ID>
```

- 특정 사건을 없었던 일로 만드는 행위
- 이전 커밋을 취소한다는 새로운 커밋 생성
- `git reset`은 커밋 내역을 삭제, `git revert`는 새로 커밋을 생성



#### 사용 예시

- 현재 커밋 로그

  ```bash
  $ git log --oneline
  3d60ece (HEAD -> master) third
  c282e61 second
  1bc5c4e first
  ```

- second 커밋을 revert → 두 번째 커밋`을` 없었던 일로

  ```bash
  $ git revert c282e61
  ```

- Vim 편집기가 실행되면 저장 후 종료 (`:wq`)

- second 커밋에 있었던 b.md가 삭제됨 (third 커밋인 c.md는 사라지지 않음)

  - second와 third 커밋 모두 없었던 일로 하고 싶다면

    `git revert c282e61 3d60ece`

  ```bash
  Revert "second"
  
  This reverts commit c282e617ca067ba3f6e654d8c409e3eb73ead57c.
  
  # Please enter the commit message for your changes. Lines starting
  # with '#' will be ignored, and an empty message aborts the commit.
  #
  # On branch master
  # Changes to be committed:
  #       deleted:    b.md
  #
  ```

- 커밋 로그 확인 → 새로운 커밋 생성, 이전 커밋 히스토리 유지

  ```bash
  $ git log --oneline
  eb955c5 (HEAD -> master) Revert "second"
  3d60ece third
  c282e61 second
  1bc5c4e first



#### 그 외 사용법

```bash
# 공백을 통해 여러 커밋을 한꺼번에 되돌리기 가능 → 하나하나 커밋 메시지 작성(Vim)
# 다섯 번째, 네 번째, 세 번째 커밋 되돌리기
$ git revert 9dbd340 09b6063 3d60ece

# 범위 지정을 통해 여러 커밋을 한꺼번에 되돌리기 가능
# <세 번째 커밋>..<다섯 번째 커밋> → 순서 반대 불가, 네 번째와 다섯 번째 커밋이 삭제됨
# 하나하나 커밋 메시지 작성(Vim)
$ git revert 3d60ece..9dbd340

# 커밋 메시지 작성을 위한 편집기를 열지 않음 (자동으로 커밋 완료)
$ git revert --no-edit 9dbd340

# 자동으로 커밋하지 않고, Staging Area에만 올림 (이후, git commit으로 수동 커밋)
# 이 옵션은 여러 커밋을 revert 할 때 하나의 커밋으로 묶는게 가능
$ git revert --no-commit 9dbd340 09b6063
```





### ✨Reset & Revert 비교

- `git reset --hard c282e61`
  - c282e61라는 커밋`으로` 돌아감
  - 이후 커밋 모두 삭제
  - 옵션이 `--hard`일 경우 이후 커밋된 파일까지 모두 삭제
- `git revert c282e61`
  - c282e61라는 특정 커밋`을` 되돌림
  - 커밋 히스토리 그대로 유지, 커밋을 취소했다는 새로운 커밋 생성
  - revert 커밋 외의 커밋에 해당하는 파일들은 그대로 유지