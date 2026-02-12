---
id: 2487
title: 'Как настроить SNMP v2c на Ruckus ZoneFlex R320?'
date: '2023-12-18T16:04:15+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2487'
permalink: /2023/12/18/kak-nastroit-snmp-v2c-na-ruckus-zoneflex-r320/
views:
    - '73'
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
    - 'Записи по сетям'
tags:
    - ruckus
    - сети
format: false
---

1\. Подключаемся по SSH.  
2\. Определяем версию SNMP и устанавливаем community

\[code lang="plain"\]set snmp version v2c set snmp community ro NAME\_COMMUNITY set snmp community rw NAME\_COMMUNITY\[/code\]

  
3\. Делаем доступ по ACL c определенный IP

\[code lang="plain"\]set snmp-acl enable set snmp-acl add IP\_ADDRESS1 set snmp-acl add IP\_ADDRESS2\[/code\]