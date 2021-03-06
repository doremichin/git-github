# Git & GitHub

<br/>

### 1. vi 입력모드시 커맨드

| 작업 | vi 명령어 | 내용 |
|-----|------|----|
| 입력 시작 | i | 명령어 입력 모드에서 텍스트 입력 모드로 전환 |
| 입력 종료 | esc버튼 | 텍스트 입력 모드에서 명령어 입력 모드로 전환 |
| 저장 없이 종료 | :q | |
| 저장하고 종료 | :wq | 입력한 것이 있을 때 사용 |
| 위로 스크롤 | k | git log 내역 같은 곳에서 사용 |
| 아래로 스크롤 | j | git log 내역 같은 곳에서 사용 | 

<br/>

### 2. git 명령어


**변경사항 확인 / git status**
```shell
git status
```

**내역 보기 / git log**
```shell
git log
```

**파일 담기 / stage에 담기 / git add** 
```shell
git add .  #모든 파일을 스테이지로 올림
git add tigers.yaml # tigers.yaml 파일 하나를 담는다  
```

**커밋하기 / git commit**
```shell
git commit

git commit -m "메세지를 적어서 커밋" # 메세지와 같이 커밋

git commit -am "수정된 사항을 자동으로 stage에 올리고 커밋"
# add + commit 이라고 보면 됨
# 파일을 수정 했을 땐 사용 가능하지만 생성 했을 땐 git add 로 추가해줘야함

#커밋 메세지 변경
git commit --amend
git commit --amend -m 'add new friends'
```
**과거의 커밋의 수정, 삭제 ,병합, 분할**
```shell
git rebase -i (대상 바로 이전 커밋의 해시)
# ex) git rebase -i a89f5226f413aa79a5781656be8abc9870f34629
# 각각의 커밋 앞에 pick이 붙어 있는 창이 나옴
# 커밋 앞에 pick에 여러 명령어를 입력해서 다양한 수정이 가능
```
| 명령어 | 설명 |
| ---- | ----|
| p , pick | 커밋 그대로 두기(기본값) | 
| r , reword | 커밋 메세지 변경 |
| e , edit | 수정을 위해 정지 |
| d , drop | 커밋 삭제 | 
| s , squash | 이전 커밋에 합치기 |


**과거로 돌아가기 / git reset, git revert**
```shell
git reset --hard # 뒤에 해시가 없으면 마지막 커밋을 가리킨다.

git revert (되돌릴 해시)
# :wq 로 커밋 메세지 저장
# 커밋끼리 에러가 발생하면 해결한 후 git revert --continue 로 마무리

# reset으로 사라진 커밋 복구하는 방법
git reflog # 커밋마다의 기록 내역이 나옴
# 이를 사용해 해시 값을 복사해서
git reset --hard (해시 값) # 리셋한 커밋 이전으로 돌아갈 수 있음
```

**치워두기 / git stash**
```shell
# 현재 변경 사항을 잠시 치워두기
git stash # git stash save 와 같음

# 원하는 시점, 브랜치에서 다시 적용
git stash pop

# 원하는 파일만 stash 하기 
git stash -p  # y, n을 입력해서 파일을 선택

# 메세지와 함께 치워두기
git stash -m 'readme 수정'

# 스태시 목록 보기
git stash list

# 목록에서 스태시 넘버를 확인 후 원하는 스태시 적용하기
git stash apply stash@{0}
```

| 명령어 | 설명 | 비고 |
|----|----|----|
| git stash | 현 작업들 치워두기 | git stash save와 같음 |
| git stash apply | 치워둔 마지막 항목(번호 없을 시) 적용 | 끝에 번호로 항목 지정 가능 |
| git stash drop | 치워둔 마지막 항목(번호 없을 시) 삭제 | 끝에 번호로 항목 지정 가능 |
| git stash pop | 치워둔 마지막 항목(번호 없을 시) 적용 및 삭제 | apply + drop 기능 |
| git stash branch (브랜치명) | 새 브랜치를 생성해서 pop | 충돌 사항이 있는 상황 등에 유용 |
| git stash clear | 치워둔 모든 항목들 비우기 | |
<br/>

**커밋되지 않은 변경사항 되돌리기 / git restore**
```shell
# stage에 올라가지 않은 파일들을 원래 상태로 복구
git restore (파일명)

# stage에 올라간 파일을 다시 워킹 디렉토리로 돌려놓기
git restore --staged (파일명)

# 파일을 특정 커밋의 상태로 되돌리기
git restore --source=(커밋 해시) (파일명)
```

**다른 브랜치의 특정한 커밋 하나를 가져오기 / git cherry-pick**
```shell
# 현재 브랜치에 다른 브랜치 커밋을 가져온다.
git cherry-pick (커밋 해시 값)
```
<br/>

### 3. branch

**브랜치 생성, 확인, 이동 / git branch , git switch**
```shell
# myeoni-branch 라는 브랜치 생성
git branch myeoni-branch

# 브랜치 목록 확인
git branch

# myeoni-branch 브랜치로 이동
git switch myeoni-branch

# checkout 명령어가 git2.23버전부터 switch, restore로 분리 됨
```

```shell
# 브랜치 생성과 동시에 이동
git switch -c new-branch

# 브랜치 삭제하기
git branch -d new-branch
# -d  대신 -D 를 사용하면 강제 삭제 가능

# 브랜치 이름 바꾸기
git branch -m (기존 브랜치명) (새 브랜치명)
```
브랜치 합치기

**merge / git merge**
```shell
# myeoni-branch를 main 브랜치로 merge 하는 상황
# git switch main  // 먼저 main 브랜치로 이동
git merge myeoni-branch 
# :wq로 커밋메세지 저장 후 마무리

# merge 충돌 발생시
# 당장 해결이 어려울 경우
git merge --abort  # merge 중단

# 충돌 부분을 해결한 후
git add .
git commit # 으로 병합
```
* merge는 reset으로 되돌리기 가능 
* merge도 하나의 커밋

**rebase / git rebase**
```shell
# myeoni-branch 를 main 브랜치로 rebase 하는 상홍
# git switch myeoni-branch // 먼저 myeoni-branch 로 이동
# merge와 반대
git rebase main

# 이제 main 브랜치가 myeoni-branch 보다 뒤쳐져 있음
# git switch main // main 브랜치로 이동 하고
git merge myeoni-branch # merge 가능


# rebase 충돌 발생시
# 당장 해결이 어려울 경우
git rebase --abort

# 해결 가능한 경우
# 충돌 부분을 수정한 뒤
git add .
git rebase --continue #rebase 계속하기
```
<br/>

### 4. github

**원격 저장소에서 프로젝트 다운 받기**
```shell
git clone (원격 저장소 주소) 
```

**원격 저장소 연결**
```shell
# origin  부분은 다른 이름으로 수정 가능
git remote add origin (원격 저장소 주소)
```

**push , pull**
```shell
# 현재 브랜치에서 어떤 원격의 어떤 브랜치로 기본 설정할 것인지 정한다.
git push -u origin main

# 로컬에서 원격으로 커밋을 밀어 올린다.
git push

# 원격의 커밋을 당겨온다.
git pull
```

**로컬과 원격의 저장소 내용이 다를 때**
```shell
git pull --no-rebase # merge 방식
# 원격 브랜치와 로컬 브랜치를 분기 태운 다음 머지 시키는 방식

git pull --rebase  # rebase 방식
# 원격 브랜치을 rebase 한 다음 로컬 브랜치를 이어 붙임  
```

**로컬 브랜치와 원격 브랜치의 push, pull**
```shell
# 로컬과 원격의 브랜치 모두 확인
git branch --all

# local-branch 를 만들고 스위치홤
git switch -c local-branch
# 원격의 브랜치 명시 및 기본 설정
git push -u origin local-local

# 깃헙에 remote-branch 생성
# git fetch 로 원격의 변경사항 확인 후
git switch -t origin/remote-branch  
# origin 저장소의 remote-branch를 로컬로 가져옴
```

**브랜치 삭제**
```shell
# 로컬 브랜치 삭제
git branch -d (로컬 브랜치명)

# 원격 브랜치 삭제
git push (원격이름) --delete (원격의 브랜치명)
git push origin --delete remote-branch
```

### 5. 태그

**로컬**
```shell
# 마지막 커밋에 태그 달기
git tag (태그 이름) # ex) git tag v2.0.0

# 현존하는 태그 확인
git tag

# 원하는 태그 내용 확인
git show v2.0.0

# 원하는 커밋에 태그 달기
git tag (태그 이름) (커밋 해시) -m (메세지)

# 원하는 패턴으로 필터링
git tag -l (조건) # ex) git tag -l 'v1.*'

# 원하는 버전으로 체크아웃
git checkout v2.0.0
```
**원격**
```shell
# 특정 태그 원격에 올리기
git push (원격명) (태그명)

# 특정 태그 원격에서 삭제
git push --delete (원격명) (태그명)

# 로컬의 모든 태그 원격에 올리기
git push --tags
```
