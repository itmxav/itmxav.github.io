---
id: 2863
title: 'Быстрый поиск файлов в Linux, содержащих определенный текст'
date: '2024-04-12T15:53:04+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2863'
permalink: /2024/04/12/bystryj-poisk-fajlov-v-linux-soderzhashhix-opredelennyj-tekst/
views:
    - '26'
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
wp_statistics_words_count:
    - '39'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Linux'
tags:
    - linux
format: false
---

Короткая заметка, чтобы можно было быстро найти.  
Когда надо быстро найти файлы с определенным текстом, то можно перейти в нужную папку и использовать grep:

```
[code lang="plain"]grep -iRl "нужный_текст" ./[/code]
```

Главное не потерять точку перед /, а то поиск будет производиться от корня.