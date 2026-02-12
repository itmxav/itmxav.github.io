---
id: 3418
title: 'Как удалить хранилище из Proxmox Backup Server?'
date: '2025-10-27T13:39:50+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3418'
permalink: /2025/10/27/kak-udalit-xranilishhe-iz-proxmox-backup-server/
views:
    - '95'
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
    - pbs
    - proxmox
format: false
---

Иногда бывает нужно удалить хранилище из PBS, но через GUI этого сделать нельзя. Поэтому переходим в терминал и удаляем:

1\. Удаляем хранилище из системы PBS:

```
[code lang="plain"]proxmox-backup-manager datastore remove &amp;lt;название_хранилища&amp;gt;[/code]
```

2\. Удаляем точку монтирования:  
Если папка:

```
[code lang="plain"]rm -r /путь/до/папки/[/code]
```

Если надо именно отмонтированить:

```
[code lang="plain"]umount точка_монтирования/[/code]
```