---
id: 331
title: 'Быстрая (временная) установка ip-адреса и шлюза для Linux'
date: '2018-09-21T14:28:38+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=331'
permalink: /2018/09/21/bystraya-vremennaya-ustanovka-ip-adresa-i-shlyuza-dlya-linux/
views:
    - '299'
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
format: false
---

Иногда может потребоваться быстрая установка ip-адреса и шлюза по умолчанию в Linux. Например, при работе по сети с Live CD. Для этого мы зададим ip-адрес с маской и шлюз по умолчанию. Данные параметры будут работать до перезагрузки. eth0 - название сетевого интерфейса, оно может быть другое.

> `# ifconfig eth0 inet IP_АДРЕС netmask МАСКА# route add default gw АДРЕС_ШЛЮЗА eth0`