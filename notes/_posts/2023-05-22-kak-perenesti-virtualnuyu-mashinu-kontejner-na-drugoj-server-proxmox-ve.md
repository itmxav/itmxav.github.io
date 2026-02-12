---
id: 2228
title: 'Как перенести виртуальную машину (контейнер) на другой сервер Proxmox VE?'
date: '2023-05-22T12:51:56+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=2228'
permalink: /2023/05/22/kak-perenesti-virtualnuyu-mashinu-kontejner-na-drugoj-server-proxmox-ve/
views:
    - '782'
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
format: false
---

0\. Отключаем всякие ISO - файлы в CD-ROM.

1\. Делаем резервную копию

\[code lang="plain"\]vzdump 111 --dumpdir /root --mode stop\[/code\]

111 - номер машины

/root - место куда сохраняется копия

\--mode stop - останавливаем чтобы была максимальная согласованность данных

Если нужно сжатие, то можно применять алгоритм Zstandard:

\[code lang="plain"\]vzdump 111 --dumpdir /root --mode stop --compress zstd\[/code\]

2\. Переносите любым удобным способом на сервер.

3\. Разворачиваем машину

\[code lang="plain"\]qmrestore /root/vzdump-qemu-111.vma 126 -storage cluster-files\[/code\]

/root/vzdump-qemu-111.vma - сама резервная копия

126 - свободный номер для машины на сервере

-storage cluster-files - хранилище, в которое машина будет разворачиваться

Если контейнер,то пример восстановления следующий:

\[code lang="plain"\]pct restore 112 /root/vzdump-lxc-133.vma -storage cluster-files\[/code\]

\--

Источник - [Технический блог специалистов ООО"Интерфейс" - Перенос виртуальных машин и контейнеров Proxmox VE на другой сервер](https://interface31.ru/tech_it/2021/12/perenos-virtualnyh-mashin-i-konteynerov-proxmox-ve-na-drugoy-server.html)