---
id: 2883
title: 'Как зеркалировать трафик на коммутаторе Huawei S5700?'
date: '2024-05-22T16:32:09+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2883'
permalink: /2024/05/22/kak-zerkalirovat-trafik-na-kommutatore-huawei-s5700/
views:
    - '204'
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
    - 'Записи по Huawei'
tags:
    - huawei
    - сети
format: false
---

Чтобы зеркалировать трафик надо указать куда зеркалировать, откуда и какой трафик (входящий и/или исходящий).

1\. Переходим в режим конфигурирования:

```
[code lang="plain"]system-view[/code]
```

  
2\. Выбираем порт наблюдения. Например 11

```
[code lang="plain"]observe-port 1 interface GigabitEthernet0/0/11[/code]
```

  
3\. Указываем порт откуда трафик зеркалировать. Например 10:

```
[code lang="plain"]interface GigabitEthernet 0/0/10
port-mirroring to observe-port 1 both
quit[/code]
```

Если требуется только входящий трафик зеркалироваться, то

```
[code lang="plain"]port-mirroring to observe-port 1 inbound[/code]
```

  
Только исходящий

```
[code lang="plain"]port-mirroring to observe-port 1 outbound[/code]
```

  
4\. Посмотреть порт наблюдения:

```
[code lang="plain"]display observe-port[/code]
```

  
5\. Посмотреть порт зеркалирования:

```
[code lang="plain"]display port-mirroring[/code]
```