---
id: 3564
title: 'Как настроить DHCP на QTECH 4530?'
date: '2026-01-19T16:46:58+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3564'
permalink: /2026/01/19/kak-nastroit-dhcp-na-qtech-4530/
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
views:
    - '8'
wp_statistics_words_count:
    - '89'
image: /wp-content/uploads/2026/01/dhcpQtechnew1.jpg
categories:
    - 'Записи по QTECH'
tags:
    - qtech
    - сети
format: false
---

Иногда бывает нужно поднять DHCP на коммутаторе QTECH 4530. Сделать это можно через включение DHCP и создание пула:  
1\. Включаем

```
[code lang="plain"]service dhcp[/code]
```

2\. Создаем пул: имя, время аренды, сеть, шлюз, dns

```
[code lang="plain"](config)# ip dhcp pool ИМЯ_ПУЛА
(config-dhcp)# network-address 192.168.1.0 255.255.255.0
(config-dhcp)# lease 0 23 0 
(config-dhcp)# default-router 192.168.1.1
(config-dhcp)# dns-server 10.0.0.2 10.0.0.3
(config-dhcp)# exit[/code]
```

Если надо исключить 1 адрес:

```
[code lang="plain"](config)# ip dhcp excluded-address 192.168.1.1[/code]
```

Если надо несколько адресов исключить, с 10 по 20, то

```
[code lang="plain"](config)# ip dhcp excluded-address 192.168.1.10 192.168.1.20[/code]
```

Если надо удалить

```
[code lang="plain"](config)# no ip dhcp excluded-address 192.168.1.1[/code]
```

no ip dhcp pool ИМЯ\_ПУЛА  
Посмотреть выданные адреса

```
[code lang="plain"]# show ip dhcp binding[/code]
```