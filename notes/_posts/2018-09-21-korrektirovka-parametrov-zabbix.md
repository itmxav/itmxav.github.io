---
id: 329
title: 'Корректировка параметров Zabbix'
date: '2018-09-21T14:21:08+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=329'
permalink: /2018/09/21/korrektirovka-parametrov-zabbix/
views:
    - '3598'
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
wp_statistics_words_count:
    - '141'
image: /wp-content/uploads/2017/09/1000px-Server-monitoring.svg_.png
categories:
    - 'Записи про мониторинг'
tags:
    - zabbix
format: false
---

При увеличении отслеживаемых узлов, состояний различных элементов могут возникать различные проблемы. Необходимо откорректировать параметры. Возможно у вас будут другие значения. Параметры находятся в файле:

> `/etc/zabbix/zabbix_server.conf`

После изменения параметров необходимо перезагрузиться: > `service zabbix-server restart `

Ниже приведены параметры, корректировка которых может помочь устранить проблему: **Настройка кеша**> `CacheSize=256M`

**Zabbix discoverer processes more than 75% busy**> `StartDiscoverers=5`

**Zabbix icmp pinger processes more than 75% busy**Данное сообщение, говорит — что процесс(ы) выполняющие ping по хостам, перегружены. > `StartPingers=5`

**Zabbix poller processes more than 75% busy**poller — это процесс который опрашивает агентов. Данный параметр стоит увеличивать в 2- случаях: - Большая сеть - Есть много недоступных ресурсов и они мониторятся. Имеется вероятность того, что перестанет хватать коннекшенов для БД. Надо будет увеличивать лимит подключений. > `StartPollers=5`

**Zabbix unreachable poller processes more than 75% busy**> `StartPollersUnreachable=1`

**Zabbix housekeeper processes more than 75% busy**> `HousekeepingFrequency=1MaxHousekeeperDelete=100`

**Zabbix busy configuration syncer processes, in %**> `HistoryCacheSize=`

**Zabbix busy history syncer processes, in %**> `HistoryCacheSize=CacheSize=`

**Zabbix busy http poller processes, in %**> StartHTTPPollers=

**Zabbix busy java poller processes, in %**> `StartJavaPollers=`

-- Источник - [linux-notes.org](https://linux-notes.org/optimizatsiya-nastroek-zabbix/)