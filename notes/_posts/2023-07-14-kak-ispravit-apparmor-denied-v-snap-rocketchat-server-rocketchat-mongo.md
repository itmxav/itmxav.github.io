---
id: 2269
title: 'Как исправить apparmor DENIED в snap.rocketchat-server.rocketchat-mongo?'
date: '2023-07-14T11:54:35+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=2269'
permalink: /2023/07/14/kak-ispravit-apparmor-denied-v-snap-rocketchat-server-rocketchat-mongo/
views:
    - '396'
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
    - 'Записи по DevOps'
tags:
    - linux
    - rocketchat
    - snap
format: false
---

Иногда при работе с rocketchat-server через snap могут быть блокировки типа:

\[code lang="plain"\]Jul 7 13:28:57 testserver kernel: \[9327038.753123\] audit: type=1400 audit(1688725736.995:37309385): apparmor="DENIED" operation="open" profile="snap.rocketchat-server.rocketchat-mongo" name="/proc/1961/net/netstat" pid=1992 comm="ftdc" requested\_mask="r" denied\_mask="r" fsuid=0 ouid=0 \[/code\] Чтобы исправить надо:

1\. Открываем   
\[code lang="plain"\]nano /var/lib/snapd/apparmor/profiles/snap.rocketchat-server.rocketchat-mongo\[/code\]

2\. Переходим в раздел `Miscellaneous accesses` и добавляем:  
\[code lang="plain"\]@{PROC}/@{pid}/net/netstat r,\[/code\]   
3\. Перечитываем профиль

\[code lang="plain"\]apparmor\_parser -r /var/lib/snapd/apparmor/profiles/snap.rocketchat-server.rocketchat-mongo\[/code\]