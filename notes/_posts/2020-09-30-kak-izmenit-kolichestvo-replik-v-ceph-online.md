---
id: 768
title: 'Как изменить количество реплик в pool ceph (online)?'
date: '2020-09-30T02:15:30+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=768'
permalink: /2020/09/30/kak-izmenit-kolichestvo-replik-v-ceph-online/
views:
    - '218'
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
    - 'Записи по DevOps'
tags:
    - ceph
format: false
---

Для того чтобы изменить количество реплик/копий в пуле ceph, например, на size=3, min\_size=2 в терминале:

> `ceph osd pool set Имя_пула size 3ceph osd pool set Имя_пула min_size 2`

-- Источник - [комменты на форуме proxmox](https://forum.proxmox.com/threads/change-num-replicas-on-ceph-rool-online.25904/)