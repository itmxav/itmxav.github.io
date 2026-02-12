---
id: 863
title: 'Как найти рабочие хосты в подсети через Linux?'
date: '2021-08-03T18:56:37+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=863'
permalink: /2021/08/03/kak-najti-rabochie-xosty-v-podseti-cherez-linux/
views:
    - '218'
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

Например, нам надо найти все работающие хосты (если файерволом не закрыты) в диапазоне 10.126.0.1-20:

> `echo 10.126.0.{1..20} | xargs -n1 -P0 ping -c1 | grep "bytes from" | grep 10.126.0 | awk {'print $4'} | sort | uniq | sed 's/.\{1\}$//'`

Детальный разбор приведенной команды с параметрами через explainshell.com на английском: [Детальный разбор приведенной команды](https://explainshell.com/explain?cmd=echo+10.126.0.%7B1..20%7D+%7C+xargs+-n1+-P0+ping+-c1+%7C+grep+%22bytes+from%22+%7C+grep+10.126.0+%7C+awk+%7B%27print+%244%27%7D+%7C+sort+%7C+uniq+%7C+sed+%27s%2F.%5C%7B1%5C%7D%24%2F%2F%27)