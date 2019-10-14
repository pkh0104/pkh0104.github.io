---
title: "ubuntu terminal prompt stuck"
date: 2019-10-14 23:54:00 -0400
categories: ubuntu terminal stuck
---

ubuntu terminal에서 typing한 글자들도 보이지 않고 New line으로 넘어가지 않고 Prompt가 계속 이어질 때, 
```bash
$ reset #ncurses lib 필요
```
안먹으면  
```bash
$ stty sane
```
안먹으면  
```bash
$ tput rs1
```
그래서 아래와 같이 .bashrc에 설정해놓으면 편하다 한다.
```bash
alias   fixtty='reset; stty sane; tput rs1; clear; echo -e "\033c"'
```
