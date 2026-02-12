---
id: 186
title: 'Отключить flow-control через ethtool на сетевой карте в Linux'
date: '2018-07-10T14:23:04+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=186'
permalink: /2018/07/10/otklyuchit-flow-control-cherez-ethtool-na-setevoj-karte-v-linux/
views:
    - '1200'
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
    - сети
format: false
---

> `#ethtool -A eth1 autoneg off rx off tx off`

-- Источник - [docs.carbonsoft.ru](http://docs.carbonsoft.ru/pages/viewpage.action?pageId=72155150)