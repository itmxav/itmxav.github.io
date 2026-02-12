---
id: 3523
title: 'Как ограничить работу SWAP на Proxmox?'
date: '2025-12-11T15:52:29+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3523'
permalink: /2025/12/11/kak-ogranichit-rabotu-swap-na-proxmox/
views:
    - '20'
wp_statistics_words_count:
    - '58'
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
    - Виртуализация
tags:
    - linux
    - proxmox
format: false
---

Иногда бывают ситуации когда надо изменить параметр, который отвечает когда задействуется SWAP. Например, на серверах виртуализации. Проверить текущее состояние можно так:

```
[code lang="plain"]sudo sysctl vm.swappiness[/code]
```

По дефолту стоит значение:

```
[code lang="plain"]vm.swappiness = 60[/code]
```

Т.е. когда ОЗУ заполнится на 40% начнется задействование SWAP. Изменить параметр, например, на 5 можно так:

```
[code lang="plain"]sudo sysctl -w vm.swappiness=5[/code]
```

Чтобы всё работало и после перезагрузки надо использовать ключ -w.