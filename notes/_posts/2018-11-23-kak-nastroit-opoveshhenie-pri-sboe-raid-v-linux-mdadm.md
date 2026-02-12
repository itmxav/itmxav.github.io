---
id: 363
title: 'Как настроить оповещение при сбое RAID в Linux (mdadm)?'
date: '2018-11-23T14:30:44+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=363'
permalink: /2018/11/23/kak-nastroit-opoveshhenie-pri-sboe-raid-v-linux-mdadm/
views:
    - '372'
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
    - linux
    - raid
format: false
---

Исходим из того, что письма с сервера могут уходить. Для настройки оповещения при сбое RAID (mdadm) необходимо: Отредактировать конфигурационный файл mdadm

> `# editor etc/mdadm/mdadm.conf`

Находим параметр MAILADDR и прописываем нашу почту: > `# instruct the monitoring daemon where to send mail alertsMAILADDR example@example.org`

Пересчитываем конфигурационные файлы > `# /etc/init.d/mdadm reload `