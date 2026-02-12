---
id: 119
title: 'Подключение нового диска в Linux'
date: '2017-12-17T14:58:07+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=119'
permalink: /2017/12/17/podklyuchenie-novogo-diska-v-linux/
views:
    - '167'
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
    - 'Debian, Ubuntu etc.'
tags:
    - linux
format: false
---

Продключение происходило в Ubuntu. Проверяем состояние дисков:

> `fdisk -l`

***Пример вывода:**Disk /dev/sda: 1000.2 GB, 1000204886016 bytes Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes*Далее размечаем диск: > `fdisk /dev/sdb`

***Команды fdisk:**m — Помощь p — Показать разделы жесткого диска n — Создать новый раздел d — Удалить раздел q — Выйти без сохранения w — Записать изменения и выйти*Форматируем наш диск с учетом FS ext4: > `mkfs.ext4 /dev/sdb1`

А после создаем папку, ставим права и закидываем в fstab: > `mkdir /mnt/diskchmod 755 /mnt/diskmount -t ext4 /dev/sdb1 /mnt/diskecho '/dev/sdb1 /mnt/disk ext4 defaults 0 0' >> /etc/fstab`