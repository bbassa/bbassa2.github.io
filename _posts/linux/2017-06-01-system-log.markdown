---
title: System Log
layout: post
category: linux
tags: [linux, udemy, admin, log]
---
### The Syslog Standard
- 로그 메시지 처리
- 로그가 중앙에서 통제
- 메세지를 카테고리로 분류하기위해 Facilities와 Severities를 사용

### Facilities
![image](/uploads/linux/linux_udemy_01.png)

### Severities
![image](/uploads/linux/linux_udemy_02.png)

### Syslog Servers
- syslog 메세지를 rule 베이스로 처리한다.
- syslogd
- rsyslog
- syslog-ng

### rsyslog
- `/etc/rsyslog.conf`
- `$IncludeConfig /etc/rsyslog.d/*.conf`

### Loggin Rules
- Selector Field
    - FACILITY.SEVERITY
- Action Field

### Caching vs Non-caching
- 설정파일의 룰이 `-` 으로 시작
- `mail.info   -/var/log/mail.info`
- 캐시를 사용하면 속도가 향상되나 로그 메세지가 사라질 위험이 존재
- 중요한 파일은 캐시를 사용하지 않는다.(예 severity : Emergency)

### logger
```{.sh}
logger [options] message

# Options:
#    -p FACILITY.SEVERITY
#    -t TAG
```

### logrotate
- 로그 파일 정책 설정
   - 보유기간
   - 개별 파일의 기간
- `/etc/logrotate.conf`
- `include /etc/logrotate.d`


### Facilities와 Severities 테이블 파일
[Linux_Facilities_Severity.xlsx](/uploads/linux/Linux_Facilities_Severity.xlsx)