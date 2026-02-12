---
id: 2756
title: 'Не запускается MongoDB на виртуальной машине Proxmox'
date: '2024-02-22T15:26:33+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2756'
permalink: /2024/02/22/ne-zapuskaetsya-mongodb-na-virtualnoj-mashine-s-proxmox/
views:
    - '215'
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
    - 'Записи по MongoDB'
tags:
    - mongodb
    - proxmox
format: false
---

Недавно наткнулся на с проблему с MongoDB. После установки сервис никак не хотел запускаться.  
Полез посмотреть в логи, а там:

\[code lang="plain"\]kernel: traps: mongod\[xxxxxx\] trap invalid opcode ip:xxxxxx\[/code\]

В других машинах всё нормально отрабатывает и запускается.  
Ествественно, начал информацию искать через поиск и вот [здесь нашлось решение](https://forum.proxmox.com/threads/mongo-db-5-0-not-install.95857/).   
Залез посмотреть какой CPU выбран для этой машины - x86-64-v2-aes.  
Поменял на x86-64-v3, перезапустился и всё завелось.   
Часто предлагают поставить host, но если на узлах Proxmox разные CPU, то могут быть проблемы с живой миграцией.   
Хоть узлы и одинаковые, но всё же отказался от этой идеи.  
На тему CPU моделей в Proxmox можно [почитать здесь](https://pve.proxmox.com/pve-docs/chapter-qm.html).