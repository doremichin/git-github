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
```
