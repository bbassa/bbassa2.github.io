---
title: Linux Boot
layout: post
category: linux
tags: [linux, udemy, admin, boot]
---
### BIOS
- Basic Input/Output System
- boot loader를 찾아서 실행하는게 주 목적
- POST (Power-On Self Test) 실행 

###  Boot Loaders
- LILO
   -  Linux Loader
- GRUB
   - Grand Unified Bootloader
   - LILO 를 Replace

### Initial RAM DIsk
- initrd
    - initial RAM Disk
    - 디스크로부터 임시 파일시스템을 읽어서 메모리에 로드
    - permanent OS file system을 로드하는데 필요한 모듈을 포함

### /boot Directory
- 리눅스가 부팅하는데 필요한 파일을 포함
- initrd
- kernel (vmlinux or vmlinuz) - 압축되면 z로 끝남
- boot loader configuration

### Kernel Ring Buffer
- Linux Kernel 의 메세지를 포함
- dmesg
- `/var/log/dmesg`

### Runlevels
- 0 - 시스템 shutdown
- 1, S, s - single-user mode, maintenance를 위해 사용
- 2 - multi-user mode with GUI(Debian / Ubuntu)
- 3 - multi-user text mode (RedHat / CentOS)
- 4 - undefined
- 5 - multi-user mode with GUI (RedHat / CentOS)
- 6 - reboot

### Init
- `/etc/inittab`
- 'id:3:initdefault:`
- systemd 로 바뀜

### Systemd
- runlevels 대신에 targets를 사용
- `ls -l /lib/systemd/system/runlevel5.target` 을 쳐보면 graphical.target으로 심볼릭 링크가 걸려있음
- `systemctl set-default graphical.target`

### runlevel 또는 target를 바꾸기
- telinit RUNLEVEL
`telinit 5`
- systemctl isolate TARGET
`systemctl isolate graphical.target`

### Rebooting
```bash
> telinit 6
> systemctl isolate reboot.target
> reboot
```

- `shutdown [options] time [message]`

```bash
> shutdown -r 15:30 "rebooting!"
> shutdown -r +5 "rebooting soon!"
> shutdown -r now
```

### Power-Off
```bash
> telinit 0
> systemctl isolate poweroff.target
> poweroff
```