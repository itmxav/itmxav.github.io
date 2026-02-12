---
id: 3507
title: 'Как перенести виртуальную машину из VirtualBox в Proxmox?'
date: '2025-11-19T12:35:06+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3507'
permalink: /2025/11/19/kak-perenesti-virtualnuyu-mashinu-iz-virtualbox-v-proxmox/
views:
    - '57'
wp_statistics_words_count:
    - '195'
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
    - proxmox
    - virtualbox
format: false
---

Бывают ситуации когда надо перенести виртуальную машину из VirtualBox в Proxmox. Сделать это можно, например, следующим способом:

1\. В virtualbox экспортируем ВМ в открытый формат виртуализации 2.0.

При экспортировании лучше убрать галки с сетевого адаптера и usb-контроллера, если они есть. Экспортируется в файл с расширением ova.

2\. Перекидываем файл ova любым удобным способом в Proxmox (nfs, scp, smb и т.п.)

3\. Распаковываем (лучше в отдельной папке это всё делать):

```
[code lang="plain"]tar -xvf VM.ova[/code]
```

Появятся файлы с расширениями mf, ovf, vmdk.

4\. Создаем ВМ без диска в Proxmox. Например, это будет ВМ с номером 106.

5\. Конвертируем vmdk в qcow2 (можно напрямую попытаться залить, но лучше сконвертировать)

```
[code lang="plain"]qemu-img convert -f vmdk -O qcow2 VM.vmdk vm106-disk.qcow2[/code]
```

напрямую залить:

```
[code lang="plain"]qm importdisk 106 VM.vmdk local-lvm --format vmdk[/code]
```

6\. Импортируем диск в нужное хранилище (например, local-lvm) с указанием номера машины:

```
[code lang="plain"]qm importdisk 106 /полный/путь/vm106-disk.qcow2 local-lvm[/code]
```

7\. В настройках ВМ должен появиться неиспользованный диск.

Выбираем его и нажимаем редактировать, указываем тип контроллера (например, scsi) и нажимаем добавить.

8\. В параметрах ВМ, в порядке загрузки надо отметить устройство, с которого ВМ должна грузиться. Можно через терминал сделать:

```
[code lang="plain"]qm set 106 --boot c --bootdisk scsi0[/code]
```

9\. Запускаем ВМ.

10\. Часто сетевая конфигурация остается прежняя, поэтому смотрим название интерфейса в ВМ и правим всё с нужными IP-адресами, сетевыми интерфейсами.