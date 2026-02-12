---
id: 859
title: 'Как отфильтровать ip адреса по максимальному количеству запросов в Linux из логов?'
date: '2021-08-03T18:44:47+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=859'
permalink: /2021/08/03/kak-otfiltrovat-ip-adresa-po-maksimalnomu-kolichestvu-zaprosov-v-linux-iz-logov/
views:
    - '269'
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
    - web
    - команды
format: false
---

Пример выборки:

> `tail -n 400000 access.log | grep '01/Aug/2020:13' | cut -d ' ' -f 1 | sort | uniq -c | sort -n | tail -n 30`

Детальный разбор приведенных команд с параметрами через explainshell.com на английском: [Детальный разбор приведенной команды](https://explainshell.com/explain?cmd=tail+-n+400000+access.log+%7C+grep+%2701%2FAug%2F2020%3A13%27+%7C+cut+-d+%27+%27+-f+1+%7C+sort+%7C+uniq+-c+%7C+sort+-n+%7C+tail+-n+30)