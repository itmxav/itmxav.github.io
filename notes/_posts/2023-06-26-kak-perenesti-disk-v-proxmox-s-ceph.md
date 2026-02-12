---
id: 2247
title: 'Как перенести диск в Proxmox с Ceph?'
date: '2023-06-26T16:35:09+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=2247'
permalink: /2023/06/26/kak-perenesti-disk-v-proxmox-s-ceph/
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
views:
    - '214'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - Виртуализация
    - 'Записи по DevOps'
tags:
    - ceph
    - proxmox
format: false
---

Чтобы перенести диск из одной виртуальной машины в другую на одном физическом узле кластера (общее хранилище Ceph с bluestore) надо:

1\. Посмотреть нужный пул

\[code lang="plain"\]root@nodeA:~# ceph osd pool ls\[/code\]

В данном приемер это ceph-files  
2\. Найти нужный диск

\[code lang="plain"\]root@nodeA:~# rbd -p ceph-files ls\[/code\]

Переносим диск из 101 машины в 102, поэтому название диска vm-101-disk-0  
Если нужен второй диск, то vm-101-disk-1 и т.п.  
3\. Копируем диск (главное чтобы ресурсов хватало). Если большой объем надо передавать, то необходимо запустить как фоновый процесс. Можно через screen

\[code lang="plain"\]root@nodeA:~# rbd cp ceph-files/vm-101-disk-0 ceph-files/vm-102-disk-0\[/code\]

Ожидаем завершения

\[code lang="plain"\]Image copy: 100% complete...done.\[/code\]

4\. Смотрим результат

\[code lang="plain"\]root@nodeA:~# rbd -p ceph-files ls vm-101-disk-0 vm-102-disk-0\[/code\]

5\. Пересканируем конфиг для машины 102

\[code lang="plain"\]root@nodeA:~# qm rescan --vmid 102 rescan volumes... VM 102: add unreferenced volume 'ceph-files:vm-102-disk-0' as 'unused0' to config\[/code\]

Диск найден и помечен как неиспользуемый для машины 102.  
6\. Либо через web, либо через консоль прикрепляем неиспользуемый новый диск

\[code lang="plain"\]root@nodeA:~# qm set 102 --scsi1 ceph-files:vm-102-disk-0 update VM 102: -scsi1 ceph-files:vm-102-disk-0\[/code\]

7\. Если это загрузочный диск, то надо в параметрах загрузки ВМ указать scsi1.