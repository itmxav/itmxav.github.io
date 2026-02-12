---
id: 3386
title: 'Как узнать IP, зная MAC адрес на порту CISCO?'
date: '2025-08-29T12:08:20+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3386'
permalink: /2025/08/29/kak-uznat-ip-znaya-mac-adres-na-portu-cisco/
views:
    - '29'
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
    - сети
format: false
---

Иногда бывают ситуации когда надо определить IP, зная MAC и порт Cisco. Сделать это можно так

Смотрим какие MAC есть на интересующем порту

```
[code lang="plain"]# sh mac-address table int GiX/X/X[/code]<br></br>или
```

```
[code lang="plain"]# sh mac address-table int GiX/X/X[/code]
```

Определяем IP по MAC-таблице

```
[code lang="plain"]# sh ip arp xxxx.xxxx.xxxx[/code]
```