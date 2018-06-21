---
title: postman
p: /ubuntu/postman
date: 2018-06-16 12:47:31
tags:
categories:
- ubuntu
---

安装postman遇到报错：
./Postman: error while loading shared libraries: libgconf-2.so.4: cannot open shared object file: No such file or directory

安装libgconf即可：
$sudo apt install libgconf2-4
