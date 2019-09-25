---
title: "Linux sed command"
date: 2019-09-25 23:02:00 -0400
categories: linux command
---

```bash
$ sed -i -e 's+\(^deb http://security.*\)+# \1+g' /etc/apt/sources.list
```

-i: script 실행결과를 File에 반영.  
-e: 이 Option 뒤에 나오는 문자열들을 편집 명령어로 해석. 명령 하나만 사용하려면 안써도 무방.  
'+'가 내가 알고 있는 '/'로 쓰이고 있다.  
\(\) 안의 내용은 뒤에서 \1로 불러올수 있다. \(a\)\(b\)에서 \1은 a가 되고 \2는 b가 된다.  

결국 /etc/apt/sources.list 파일 안에서 dev http://security.*로 시작하는 문자열을 찾아서 # dev http://security.*로 치환하는 명령이다.
