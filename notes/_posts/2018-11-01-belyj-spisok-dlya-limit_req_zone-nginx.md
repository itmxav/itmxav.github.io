---
id: 355
title: 'Белый список для limit_req_zone [Nginx]'
date: '2018-11-01T15:33:04+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=355'
permalink: /2018/11/01/belyj-spisok-dlya-limit_req_zone-nginx/
views:
    - '240'
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
    - nginx
format: false
---

Решается через geo и map

> `geo $limited_net {default 1;10.3.0.0/16 0;}map $limited_net $addr_to_limit {0 "";1 $binary_remote_addr;}limit_req_zone $addr_to_limit zone=gulag:10m rate=2r/s;`

Суть в том, что что бы сделать непустое значение для нашей переменной. Напомню, что пустые значения (как в даном случае у нас определена подсеть 10.3.0.0/16) не учитываются -- Источник - [skeletor.org.ua](https://skeletor.org.ua/?p=3941)