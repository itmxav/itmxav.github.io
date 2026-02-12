---
id: 1441
title: 'Ошибка 1 scrub errors/Possible data damage: 1 pg inconsistent на Ceph'
date: '2022-09-13T12:28:09+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=1441'
permalink: /2022/09/13/oshibka-1-scrub-errors-possible-data-damage-1-pg-inconsistent-na-ceph/
views:
    - '520'
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
    - ceph
format: false
---

Иногда может возникать проблема "1 scrub errors/Possible data damage: 1 pg inconsistent" на ceph. В случае появлении такой проблемы, то надо будет присмотреть к дискам, с которыми она связана.

Чтобы решать эту проблему надо узнать id pg:

1. Смотрим состояние ceph: > `ceph health detail`
  
В выводе будет что-то такое:  
HEALTH\_ERR 1 scrub errors; Possible data damage: 1 pg inconsistent  
OSD\_SCRUB\_ERRORS 1 scrub errors  
PG\_DAMAGED Possible data damage: 1 pg inconsistent  
pg 2.123 is active+clean+scrubbing+deep+inconsistent, acting \[18,3,2\]  
  
7. pg id = 2.123
8. Пробуем восстановиться и ждем результаты восстановления: > `ceph pg repair 2.123`