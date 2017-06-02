---
title: User Management
layout: post
category: linux
tags: [linux, udemy, admin, user]
---

### Accounts
- username ( login ID)
- UID (user ID) - unique number
- Default Group
- Comments
- Shell
- Home Directory Location

### 사용자 계정 정보
- `/etc/password`

```bash
# username:password:UID:GID:comments:home_dir:shell
   root:x:0:0:root:/root:/bin/bash
```

### username convention
- 관습처럼 linux username은 8자 보다 작다. (시스템은 32자의 username까지 지원) -> 8자보다 큰 username의 경우 축약해서 보여짐
- Case Sensitive
- 소문자만 쓴다.
- 특수문자를 쓰지 않는다.

### 패스워드
- `/etc/shadow` 에 저장

### UIDs
- root 계정은 항상 UID 0
- UID는 unique number
- system 계정은 UIDs < 1000
    - `/etc/login.defs`에 설정

### GID (Group ID)
- /etc/passwd 에 표시되는 GID는 계정의 기본 그룹
- 새로운 파일은 사용자의 기본 그룹에 속하게 된다.
- `newgrp` 명령어로 사용자는 그룹을 바꿀 수 있다.

### Cooment Field
- 보통 사용자의 전체 이름
- 시스템 계정인 경우 사용 용도 표시
- 전화번호와 같은 부가 정보를 포함할 수 있다.
- GECOS 필드라고 불린다.

### Home Directory
- 홈 디렉토리가 존재하지 않으면 `/`에 위치하게 된다.

### Shell
- 사용자가 로그인하면 shell이 실행된다.
- `/etc/shells`에 사용가능한 shell의 목록
- shell은 반드시 shell일 필요가 없다.
- 계정의 사용을 방지하기 위해 `/usr/sbin/nologin` 이나 `/bin/false`를 shell로 사용
- command line 명령어일 수 있다.

### 사용자 관리
- 사용자 추가

```bash
useradd [options] username

-c "COMMENT"               Comments for the account       계정의 comment
-m                                    Create the home directory       홈 디렉토리 만들기
-s/shell/path                    The path to the user's shell      사용자의 shell 경로
-r                                      Create a system account          시스템 계정
-d                                     Specify the home directory      홈디렉토리 폴더 지정
-g GROUP                         Specify the default group        그룹 지정
-G GROUP1, GROUPN      Additional groups
```

- password 변경

```bash
passwd username
```

- 사용자 삭제

```bash
# -r 을 지정해야 사용자 홈 디렉토리가 삭제
userdel [-r] username
```

- 사용자 변경

```bash
usermod [ options ] username

-c "COMMENT"               Comments for the account       계정의 comment
-g GROUP                         Specify the default group         그룹 지정
-G GROUP1, GROUPN      Additional groups
-s/shell/path                    The path to the user's shell      사용자의 shell 경로
```

### `/etc/skel`
- 사용자를 만들떄 -m 옵션을 지정하여 home directory를 만들면 `/etc/skel`이 home directory에 복사된다.
- `/etc/skel`은 보통 shell 설정파일 (.profile, .bashrc, etc)

### 사용자 그룹
- `/etc/group`

```bash
# group_name:password:GID:account1, accountN
root:x:0:
```

- 사용자 그룹 보기

```bash
group root
```

- 사용자 그룹 추가

```bash
groupadd [options] group_name
```

- 사용자 그룹 삭제

```bash
groupdel group_name
```

- 사용자 그룹 변경
```bash
groupmod [options] group_name

-g GID                Change the group ID to GID
-n GROUP          Rename the group to GROUP
```