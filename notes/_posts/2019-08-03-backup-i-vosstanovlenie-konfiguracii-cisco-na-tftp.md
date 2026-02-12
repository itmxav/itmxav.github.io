---
id: 640
title: 'Backup и восстановление конфигурации Cisco. TFTP-сервер'
date: '2019-08-03T16:57:02+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=640'
permalink: /2019/08/03/backup-i-vosstanovlenie-konfiguracii-cisco-na-tftp/
views:
    - '8286'
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
image: /wp-content/uploads/2017/09/computer-156949_640.png
categories:
    - 'Записи по Cisco'
tags:
    - cisco
    - tftp
format: false
---

**Резервное копирование на tftp-сервер**В привилегированном режиме (если текущий конфиг - running-config, загрузочный startup-config): > `Router#copy running-config tftpAddress or name of remote host []? 192.168.0.2Destination filename [Router-confg]?!!11600 bytes copied in 0.132 secs (83921 bytes/sec)`

**Восстановление с tftp-сервера**В привилегированном режиме(если текущий конфиг - running-config, загрузочный startup-config): > `Router#copy tftp: running-configAddress or name of remote host []? 192.168.0.2Source filename []? backup_cfg_ciscoDestination filename [running-config]?Accessing tftp://192.168.0.2/backup_cfg_cisco...Loading backup_cfg_cisco from 192.168.0.2 (via FastEthernet0/0): ![OK - 1030 bytes]`1020 bytes copied in 8.61 secs (102 bytes/sec)

Если в качестве назначения указывается running-config то чтобы его задействовать после перезагрузки его надо сохранить в стартовую конфигурацию.