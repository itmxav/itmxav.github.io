---
id: 3527
title: 'Как забэкапить виртуальную машину через XenCenter 6.5?'
date: '2025-12-12T13:10:39+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3527'
permalink: /2025/12/12/kak-zabekapit-virtualnuyu-mashinu-cherez-xencenter-6-5/
views:
    - '39'
wp_statistics_words_count:
    - '86'
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
    - xen
format: false
---

В глубине глубин нашлась система виртуализации Xen с древней версией 6.5. Надо было забэкапить пару машин. Бэкапим по NFS. Для этого:  
1\. Добавляем в XenCenter "New Storage" -&gt; NFS VHD -&gt; вписываем название -&gt; путь к папке на сервере NFS.  
2\. Выключаем ВМ, чтобы была консистентность.  
2\. Переходим в консоль и смотрим куда NFS смонтировалось:

```
[code lang="plain"]mount[/code]
```

3\. И бэкапим

```
[code lang="plain"]xe vm-export vm="название_вм_с_учетом_регистра" filename="/var/run/sr-mount/Здесь_UUID/backup_VM.xva"[/code]
```

и дожидаемся

```
[code lang="plain"]Export succeeded[/code]
```

На более новых версиях Xen, вроде, через UUID надо бэкапить.  
Узнать UUID NFS-SR

```
[code lang="plain"]xe sr-list name-label="NFS-Backup" params=uuid --minimal[/code]
```

и, возможный, пример

```
[code lang="plain"]xe vm-export vm="название_вм_с_учетом_регистра" filename="nfs://UUID_NFS_SR/backup_VM.xva"[/code]
```