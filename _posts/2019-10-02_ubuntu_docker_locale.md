---
title: Ubuntu docker에서 Locale 설정
date: 2019-10-02 21:15:00 -0400
categories: ubuntu docker locale
---

Docker에서 제공하는 공식 Image는 일반 Linux 배포판과 달리 Process 실행에 필요한 최소한의 파일들만 준비되어 있어 
기본적으로 설정 가능한 Locale도 C(POSIX)(기본값), C.UTF-8 정도로 제한적이다.  

Locale 형식  
<language>_<territory>.<codeset>  
ex) en_US.UTF-8

Locale 확인 방법  
```bash
$ locale
LANG=
LANGUAGE=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=
```

간단하게 LC_ALL 환경 변수를 설정하면 모든 LC에 적용된다.  
LANGAGE 환경변수를 설정하면 App 실행 시 해당 언어로 Log 출력된다.  

Locale 추가 및 설정
```bash
$ sudo apt-get update
$ sudo apt-get install locales
$ cat /usr/share/i18n/SUPPORTED #생성 가능한 Locale 확인.
$ locale-gen en_US.UTF-8
$ locale -a #설정 가능한 Locale 확인.
$ export LANG=en_US.UTF-8
$ export LANGUAGE en_US:en
$ export LC_ALL en_US.UTF-8
```

Dockerfile
```bash
RUN atp-get install -y locales
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8
```
