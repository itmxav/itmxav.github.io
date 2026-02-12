---
id: 2870
title: 'Как настроить Syslog на Cisco ASA 5500 серии?'
date: '2024-05-06T17:11:21+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2870'
permalink: /2024/05/06/kak-nastroit-syslog-na-cisco-5500-serii/
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
    - 'Записи по Cisco'
tags:
    - cisco
format: false
---

Для начала надо настроить время. Указываем зону и NTP-сервер:  
\[code lang="plain"\]clock timezone MSK/MSD 3 ntp server IP\_NTP\_server source inside\[/code\]

Далее настроиваем куда отправлять логи. Отправляем логи через inside-интерфейс и указываем, что отправляем их на порт 1234. По умолчанию 514 порт, но иногда лучше поменять порт. Например, Graylog почему-то не хотел логи с 514 порта обрабатывать, хотя логи других нормально обрабатывались.  
\[code lang="plain"\]logging enable logging trap informational logging asdm errors logging device-id string ASA55ver logging host inside IP\_syslog 17/1234\[/code\]