---
id: 2743
title: 'Ошибка Oxidized &#171;Timeout::Error with msg execution expired&#187; и Cisco Nexus'
date: '2024-02-19T12:10:52+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2743'
permalink: /2024/02/19/oshibka-oxidized-timeouterror-with-msg-execution-expired-i-cisco-nexus/
views:
    - '173'
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
    - cisco
    - oxidized
format: false
---

При сборе конфигурации Cisco Nexus через Oxidized может появиться ошибка "Timeout::Error with msg execution expired".

Чтобы её решить, в правилах для роли в Cisco Nexus необходимо добавить:

\[code lang="plain"\]permit command terminal length 0\[/code\]

Примерный список правил для роли может выглядеть вот так:

\[code lang="plain"\] NX(config-role)# rule 1 permit command show version NX(config-role)# rule 2 permit command show inventory NX(config-role)# rule 3 permit command show running-config NX(config-role)# rule 4 permit command terminal length 0 \[/code\]