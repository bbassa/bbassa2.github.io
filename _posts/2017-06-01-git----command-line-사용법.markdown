---
title: git -- Command Line 사용법
layout: post
category: git
tags: [git, vcs, tools]
---
## 새로운 저장소 만들기
```{.sh}
# 폴더를 하나 만들고, 그 안에서 아래 명령을 실행 
git init
```
## 저장소 받아오기
```{.sh}
# 로컬 저장소를 복제
git clone /로컬/저장소/경로

# 원격 저장소를 복제
git clone 사용자명@호스트:/원격/저장소/경로
```

## add & commit
```{.sh}
# 변경된 파일을 인덱스(staging area)에 추가
git add <파일 이름>
git add *
git add .
# commit 하기 -m 다음에 commit 메세지를 달아준다.
git commit -m "이번 확정본에 대한 설명"
```
## 변경내용 push
```{.sh}
# 로컬 저장소 HEAD 안의 내용을 원격 서버에 반영
git push origin master
# 기존 원격저장소를 복제한게 아니라면 주소를 추가
git remote add origin <원격 서버 주소>
```

## branch
![image](/uploads/git/git_commandline_01.png)
```{.sh}
# branch 만들기
git checkout -b branch_a
# master로 돌아오기
git checkout master
# branch 삭제
git branch -d branch_a
# branch push 하기
git push origin branch_a
```

## merge
```{.sh}
# 원격 저장소 내용이 로컬 작업 디렉토리에 fetch and merge
git pull
# 다른 가지의 내용을 현재 가지에 병합하기
git merge <가지 이름>
# conflict 발생시 충돌을 해결후 다시 add해 줘야 함
git add <파일 이름>
# diff 보기
git diff <원래 가지> <비교 대상 가지>
```

## tag
```{.sh}
# 새 버전을 발표할 때마다 꼬리표를 달아 식별
git tag 1.0.0 10673fac 
# 식별자 얻어오기
git log
```

## 로컬 변경 내용 되돌리기
```{.sh}
git checkout -- <파일 이름>
```

## 로컬의 모든 내용과 확정본 포기후 최신 이력 가져오기
```{.sh}
git fetch origin
git reset --hard origin/master
```