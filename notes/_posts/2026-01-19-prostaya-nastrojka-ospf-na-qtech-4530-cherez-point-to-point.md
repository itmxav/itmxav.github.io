---
id: 3556
title: 'Простая настройка OSPF на QTECH 4530 через point-to-point'
date: '2026-01-19T23:52:32+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3556'
permalink: /2026/01/19/prostaya-nastrojka-ospf-na-qtech-4530-cherez-point-to-point/
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
    - '11'
wp_statistics_words_count:
    - '239'
image: /wp-content/uploads/2026/01/ospf2.jpg
categories:
    - 'Записи по QTECH'
tags:
    - сети
format: false
---

Далее простой пример OSPF на QTECH 4530 (без паролей, acl доп.функционала). Они поддерживают только OSPFv2. Все настройки идут через VLAN. На 1 коммутаторе ещё и маршрут по умолчанию. Зона Backbone. Тип point-to-point.  
Раз настраиваете динамическую маршрутизацию, то знаете как-то теорию, а также, что и в каком режиме надо делать, поэтому не буду уточнять про '&gt;','#', '(config)#' и т.д.   
На 1 коммутаторе делаем настройки vlan для OSPF p2p.

```
[code lang="plain"]vlan 10
 name p2p_to_sw2
interface Vlan10
 description p2p_to_sw2
 ip ospf network point-to-point
 ip address 192.168.1.101 255.255.255.252[/code]
```

Настраиваем loopback интерфейс (да, пример ip в обратном порядке)

```
[code lang="plain"]interface Loopback1
 ip address 192.168.2.3 255.255.255.255[/code]
```

Маршрут по умолчанию

```
[code lang="plain"]ip route 0.0.0.0/0 10.0.0.1[/code]
```

Настройка пользовательской сети

```
[code lang="plain"]vlan 20
 name Users
interface Vlan20
 description Users
 ip address 192.168.3.1 255.255.255.0
Interface Ethernet1/0/1
 description Users
 switchport access vlan 20[/code]
```

Включаем OSPF, анонсируем пользовательскую сеть, p2p, loopback и говорим про маршрут по умолчанию.

```
[code lang="plain"]router ospf 1
 ospf router-id 192.168.2.2
 network 192.168.3.0 0.0.0.255 area 0
 network 192.168.2.2 0.0.0.0 area 0
 network 192.168.1.100 0.0.0.3 area 0
 default-information originate[/code]
```

На 2 коммутаторе делаем настройки vlan для OSPF p2p

```
[code lang="plain"]vlan 11
 name p2p_to_sw1
interface Vlan11
 description p2p_to_sw1
 ip ospf network point-to-point
 ip address 192.168.1.102 255.255.255.252[/code]
```

Настраиваем loopback интерфейс

```
[code lang="plain"]interface Loopback1
 ip address 192.168.2.2 255.255.255.255[/code]
```

Включаем OSPF, анонсируем p2p и loopback

```
[code lang="plain"]router ospf 1
 ospf router-id 192.168.2.2
 network 192.168.2.2 0.0.0.0 area 0
 network 192.168.1.100 0.0.0.3 area 0[/code]
```

Пользовательскую сеть можно поднять как и в коммутаторе 1. Далее проверяем работу через ping и

```
[code lang="plain"]show ip ospf nei
show ip route[/code]
```

и тому подобные просмотры. Должны быть видны соседи и трафик должен проходить.