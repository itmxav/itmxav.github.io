---
id: 939
title: 'Ошибка A start job is running for Create Volatile Files and Directories на Linux'
date: '2022-03-22T17:15:41+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=939'
permalink: /2022/03/22/oshibka-a-start-job-is-running-for-create-volatile-files-and-directories-na-linux/
ytrssenabled_meta_value:
    - 'no'
ytremove_meta_value:
    - 'no'
ytad1meta:
    - enabled
ytad2meta:
    - enabled
ytad3meta:
    - enabled
ytad4meta:
    - enabled
ytad5meta:
    - enabled
template_meta:
    - 'no'
ytextendedhtmlmeta:
    - default
ytpostdatemeta:
    - default
views:
    - '1020'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Linux'
tags:
    - linux
format: false
---

1. При загрузке Grub, нажмите e. В строке linux /boot/vmlinuz... найти и заменить: > `"splash quit" на verbose rw init=/bin/bash`

2. После нажать Ctrl+X или F10 для загрузки. Надо дождаться командной строки под рутом. 3. Посмотреть /tmp: > `ls -la /`

4. Переименовать и создайте заново директорию /tmp: > `mv /tmp /old.tmp mkdir /tmpchmod 1777 /tmp`

5. Далее перезагрузиться. 