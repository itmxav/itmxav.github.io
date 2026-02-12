---
id: 3233
title: 'Как проверить конфигурацию ProFTPD?'
date: '2024-12-25T13:12:43+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3233'
permalink: /2024/12/25/kak-proverit-konfiguraciyu-proftpd/
views:
    - '57'
wp_statistics_words_count:
    - '18'
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
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Linux'
tags:
    - linux
    - proftpd
format: false
---

Краткая заметка. Чтобы проверить конфигурационный файл ProFTPD на ошибки можно запустить команду:

```
[code lang="plain"]proftpd -td5[/code]
```

или

```
[code lang="plain"]$ sudo proftpd -t[/code]
```