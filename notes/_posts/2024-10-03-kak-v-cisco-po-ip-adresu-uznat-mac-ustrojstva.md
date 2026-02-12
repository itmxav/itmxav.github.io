---
id: 3043
title: 'Как в Cisco по ip адресу узнать mac устройства'
date: '2024-10-03T14:05:54+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3043'
permalink: /2024/10/03/kak-v-cisco-po-ip-adresu-uznat-mac-ustrojstva/
views:
    - '123'
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
    - 'Записи по Cisco'
tags:
    - cisco
format: false
---

Иногда в Cisco бывает нужно быстро найти mac по IP. Сделать это достаточно просто смотрим arp таблицу и фильтруем по известному ip через include

> sh ip arp | i 10.111.222.111