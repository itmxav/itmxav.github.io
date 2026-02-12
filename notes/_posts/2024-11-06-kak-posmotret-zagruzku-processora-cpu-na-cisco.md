---
id: 3088
title: 'Как посмотреть загрузку процессора (CPU) на Cisco?'
date: '2024-11-06T11:16:34+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3088'
permalink: /2024/11/06/kak-posmotret-zagruzku-processora-cpu-na-cisco/
views:
    - '102'
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
    - 'Записи по Cisco'
tags:
    - cisco
format: false
---

Иногда бывает нужно посмотреть какие процессы грузят Cisco. Сделать это можно следующим образом:

```
[code lang="plain"]# sh processes cpu | exclude 0.00[/code]
```

Выводим весь список процессов и убираем тех, кто потребляет 0.