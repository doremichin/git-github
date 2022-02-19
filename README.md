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


변경사항 확인
```shell
git status
```

파일 담기 / stage에 담기
```shell
git add .  #모든 파일을 스테이지로 올림
git add tigers.yaml # tigers.yaml 파일 하나를 담는다  
```

커밋하기
```shell
git commit

git commit -m "메세지를 적어서 커밋" # 메세지와 같이 커밋

git commit -am "수정된 사항을 자동으로 stage에 올리고 커밋"
# add + commit 이라고 보면 됨
# 파일을 수정 했을 땐 사용 가능하지만 생성 했을 땐 git add 로 추가해줘야함
```

내역 보기
```shell
git log
```

과거로 돌아가기
```shell
git reset --hard # 뒤에 해시가 없으면 마지막 커밋을 가리킨다.

git revert (되돌릴 해시)
# :wq 로 커밋 메세지 저장
# 커밋끼리 에러가 발생하면 해결한 후 git revert --continue 로 마무리
```
### 3. branch

브랜치 생성, 확인, 이동
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

merge
```shell
# myeoni-branch를 main 브랜치로 merge 하는 상황
# git switch main  // 먼저 main 브랜치로 이동
git merge myeoni-branch 
# :wq로 커밋메세지 저장 후 마무리
```
* merge는 reset으로 되돌리기 가능 
* merge도 하나의 커밋

rebase
```shell
# myeoni-branch 를 main 브랜치로 rebase 하는 상홍
# git switch myeoni-branch // 먼저 myeoni-branch 로 이동
# merge와 반대
git rebase main

# 이제 main 브랜치가 myeoni-branch 보다 뒤쳐져 있음
# git switch main // main 브랜치로 이동 하고
git merge myeoni-branch # merge 가능

```
