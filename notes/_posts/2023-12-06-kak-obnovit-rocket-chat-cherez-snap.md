---
id: 2449
title: 'Как обновить Rocket.chat через snap?'
date: '2023-12-06T16:51:32+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2449'
permalink: /2023/12/06/kak-obnovit-rocket-chat-cherez-snap/
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
    - '164'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по DevOps'
tags:
    - linux
    - rocketchat
format: false
---

1\. Останавливаем

\[code lang="plain"\]sudo service snap.rocketchat-server.rocketchat-server stop\[/code\]

или

\[code lang="plain"\]sudo systemctl stop snap.rocketchat-server.rocketchat-server\[/code\]

2\. Переключаем на нужную ветку  
Обновление должно быть последовательное по версиям 1.x-&gt;2.x-&gt;3.x-&gt;4.x-&gt;5.x-&gt;6.x  
Обязательно сделайте резервное копирование

\[code lang="plain"\]sudo snap switch rocketchat-server --channel=x.x/stable\[/code\]

3\. Обновляемся

\[code lang="plain"\]sudo snap refresh rocketchat-server\[/code\] или всё сразу \[code lang="plain"\]sudo snap refresh rocketchat-server --channel=x.x/stable\[/code\]

4\. Запускаем сервис

\[code lang="plain"\]sudo service snap.rocketchat-server.rocketchat-server start\[/code\]

или

\[code lang="plain"\]sudo systemctl restart snap.rocketchat-server.rocketchat-server\[/code\]