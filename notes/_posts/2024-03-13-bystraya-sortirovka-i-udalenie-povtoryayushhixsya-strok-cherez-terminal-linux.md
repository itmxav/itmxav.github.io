---
id: 2809
title: 'Быстрая сортировка и удаление повторяющихся строк через терминал Linux'
date: '2024-03-13T12:11:55+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2809'
permalink: /2024/03/13/bystraya-sortirovka-i-udalenie-povtoryayushhixsya-strok-cherez-terminal-linux/
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
    - '89'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Linux'
tags:
    - bash
    - linux
format: false
---

Короткая заметка, чтобы можно было быстро найти.  
Иногда надо быстро отсортировать строки через терминал в Linux и убрать повторения.  
Здесь хорошо может помочь конвейерные способы

\[code lang="plain"\]cat file.txt | sort | uniq\[/code\]

или

\[code lang="plain"\]sort file.txt | uniq\[/code\]

Или sort через параметр -u

\[code lang="plain"\]sort -u file.txt\[/code\]