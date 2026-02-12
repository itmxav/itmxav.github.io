---
id: 3545
title: 'Базовая настройка коммутатора QTech QSW-3750-52T-AC-R'
date: '2026-01-19T23:53:01+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3545'
permalink: /2026/01/19/bazovaya-nastrojka-kommutatora-qtech-qsw-3750-52t-ac-r/
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
    - '51'
wp_statistics_words_count:
    - '210'
image: /wp-content/uploads/2026/01/baseqtech3.jpg
categories:
    - 'Записи по QTECH'
tags:
    - qtech
    - сети
format: false
---

Импортозамещение продолжает двигаться. В руки попал очередной QTECH. В этот раз [QSW-3750-52T-AC-R](https://www.qtech.ru/catalog/switches/access/qsw_3750_rev_r/qsw_3750_52t_ac_r/).

Поддержка нужных сертификатов тоже на сайте можно посмотреть.

Настраиваем, в данном случае, всё через консоль и только базовые настройки. Без защиты от петель, кучи VLAN, trunk-портов, уровней доступа пользователей и т.п.

Подключаемся по 9600-8-N-1:

```
[code lang="plain"] enable
SW# config[/code]
```

Посмотреть рабочий конфиг

```
[code lang="plain"]SW# show running-config [/code]
```

Отключаем лишнее

```
[code lang="plain"]SW(config)# no ip http server
SW(config)# no ip http secure-server
SW(config)# interface Vlan1
SW(Config-if-Vlan1)#no ip address 192.168.0.1 255.255.255.0
SW(Config-if-Vlan1)#shutdown
SW(Config-if-Vlan1)#exit[/code]
```

Настройка hostname

```
[code lang="plain"]SW(config)# hostname ИМЯ[/code]
```

Добавляем нового пользователя, а старого удаляем. И защифруем пароль в конфиге

```
[code lang="plain"]SW(config)# username имя_пользователя privilege 15 password пароль
SW(config)# service password-encryption[/code]
```

Включаем ssh

```
[code lang="plain"]SW(config)# ssh enable[/code]
```

Настраиваем vlan 2

```
[code lang="plain"]SW(config)# vlan 2
SW(Config-Vlan2)# name Users
SW(Config-if-Vlan2)# interface Vlan2
SW(Config-if-Vlan2)#description Users
SW(Config-if-Vlan2)# ip address ip-адрес маска
SW(Config-if-Vlan2)# Interface Ethernet1/0/1-52
SW(Config-If-Port-Range)# switchport mode access
SW(Config-If-Port-Range)# switchport access vlan 2
SW(Config-If-Port-Range)#exit[/code]
```

Добавляем маршрут по умолчанию

```
[code lang="plain"]SW(config)# ip route 0.0.0.0/0 IP_ШЛЮЗА[/code]
```

Включаем lldp

```
[code lang="plain"]SW(config)# lldp enable[/code]
```

Настраиваем ntp

```
[code lang="plain"]SW(config)# ntp enable
SW(config)# ntp server ip-адрес[/code]
```

Настраиваем отправку логов

```
[code lang="plain"]SW(config)# logging 192.168.0.2
SW(config)# logging executed-commands enable[/code]
```

Пример стандартного acl

```
[code lang="plain"]SW(config)# access-list 10 permit 192.168.0.0 0.0.0.255
SW(config)# access-list 10 permit host-source 192.168.1.1
SW(config)# access-list 10 deny any-source[/code]
```

Применить стандартного acl для доступа к коммутатору (проверьте acl, а то доступ потеряете)

```
[code lang="plain"]SW(config)# authentication line vty login local
SW(config)# authentication ip access-class 10 in[/code]
```

Настраиваем snmpv2 только для чтения

```
[code lang="plain"]SW(config)# snmp-server enable
SW(config)# snmp-server community ro имя_коммунити
SW(config)# snmp-server securityip ip-адрес-сервера-мониторинга[/code]
```

Ловушки

```
[code lang="plain"]SW(config)# snmp-server host ip-адрес-сервера-мониторинга v1 usertrap
SW(config)# snmp-server enable traps[/code]
```

Cохраняем

```
[code lang="plain"]SW# write[/code]
```