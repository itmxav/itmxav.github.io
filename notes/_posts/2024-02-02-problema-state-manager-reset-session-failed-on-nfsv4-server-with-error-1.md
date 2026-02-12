---
id: 2613
title: 'Проблема &#171;state manager: reset session failed on NFSv4 server with error 1&#187;'
date: '2024-02-02T17:03:18+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2613'
permalink: /2024/02/02/problema-state-manager-reset-session-failed-on-nfsv4-server-with-error-1/
views:
    - '107'
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
    - nfs
format: false
---

Иногда при работе с NFS в Proxmox может быть ошибка:

> NFS: state manager: reset session failed on NFSv4 server 192.168.2.2 with error 1

Можно её исправить так:  
1\. Отключим хранилище в "Датацентр" -&gt; "Хранилище" -&gt; Выключаем NFS через редактирование  
2\. На узлах смотрим папку монитирования

\[code lang="plain"\]# mount\[/code\]

3\. Отмонтирем её вручную. Например, интересует папка ISONFS

\[code lang="plain"\]# umount /mnt/pve/ISONFS\[/code\]

4\. Подключаем хранилище (см. п.1)