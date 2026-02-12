---
id: 746
title: 'Как очистить кэш Squid?'
date: '2020-06-22T16:43:08+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=746'
permalink: /2020/06/22/kak-ochistit-kesh-squid/
views:
    - '727'
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
    - proxy
format: false
---

Ищем где находится кэш:

> `grep cache_dir /etc/squid/squid.conf`

Например, кэш находится в */var/spool/squid/*. Останавливаем, чистим, инициализируем и запускаем: > `service squid stoprm -r /var/spool/squid/*squid -zservice squid start`