---
id: 2789
title: 'Ошибка %ADJ-3-RESOLVE_REQ на Cisco 3560-X'
date: '2024-03-12T22:46:15+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2789'
permalink: /2024/03/12/oshibka-%adj-3-resolve_req-na-cisco-3560-x/
views:
    - '292'
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
    - сети
format: false
---

На одной из Cisco 3560-X в логи сыпались постоянно ошибки:

\[code lang="plain"\]%ADJ-3-RESOLVE\_REQ: Adj resolve request: Failed to resolve xx.xx.xx.xx VlanXX\[/code\]

Т.к. на Cisco нет какой-то сложной конфигурации, то помогло:

\[code lang="plain"\]no ip cef optimize neighbor resolution\[/code\]

Некоторые писали, что это может быть баг на конкретной железке. Некоторые писали, что может вырасти нагрузка на ЦП, по умолчанию включен параметр. В моем случае нагрузка не изменилась и ошибки ушли.