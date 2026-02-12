---
id: 2965
title: 'Правила в iptables для Zabbix'
date: '2024-08-09T12:42:12+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2965'
permalink: /2024/08/09/pravila-v-iptables-dlya-zabbix/
views:
    - '221'
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
    - zabbix
format: false
---

Часто в процессе настройки сервера и/или агентов Zabbix требуется прописывать правила для файервола. Обычно используются порты 10050 на агенте и 10051 на сервер.  
Например, для сервера в iptables вот такое правило может быть:  
\[code lang="plain"\]iptables -A INPUT -s IP\_ADDRESS\_AGENT/32 -p tcp -m tcp --dport 10051 -j ACCEPT \[/code\]   
Eсли для всех надо сделать порт доступным  
\[code lang="plain"\]iptables -A INPUT -p tcp -m tcp --dport 10051 -j ACCEPT\[/code\]  
Если правило надо поместить на самый верх цепочки, то  
\[code lang="plain"\]iptables -I\[/code\]  
На агенте:  
\[code lang="plain"\]iptables -A INPUT -s IP\_ADDRESS\_SERVER/32 -p tcp -m tcp --dport 10050 -j ACCEPT\[/code\]  
Удаление правил:  
\[code lang="plain"\]iptables -D INPUT -s IP\_ADDRESS\_AGENT/32 -p tcp -m tcp --dport 10051 -j ACCEPT\[/code\]  
\[code lang="plain"\]iptables -D INPUT -s IP\_ADDRESS\_SERVER/32 -p tcp -m tcp --dport 10050 -j ACCEPT\[/code\]