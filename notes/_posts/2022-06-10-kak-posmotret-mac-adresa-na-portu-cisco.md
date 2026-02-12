---
id: 1328
title: 'Как посмотреть mac адреса на порту Cisco?'
date: '2022-06-10T17:45:55+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=1328'
permalink: /2022/06/10/kak-posmotret-mac-adresa-na-portu-cisco/
views:
    - '8377'
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
format: false
---

Иногда требуется посмотреть какие mac адреса привязаны к портам на cisco. Например, когда ip-телефон и ПК подключены к одному порту. Сделать это можно так:

> `show mac address-table interface <порт>`