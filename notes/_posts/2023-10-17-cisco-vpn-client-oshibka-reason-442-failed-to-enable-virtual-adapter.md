---
id: 2346
title: 'Cisco VPN Client. Ошибка Reason 442: Failed to enable Virtual Adapter'
date: '2023-10-17T12:07:36+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=2346'
permalink: /2023/10/17/cisco-vpn-client-oshibka-reason-442-failed-to-enable-virtual-adapter/
views:
    - '85'
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

Ошибка происходит потому что клиент не находит адаптер сети. Можно исправить так:  
1\. Запускаем редактор реестра

\[code lang="plain"\]regedit.exe\[/code\]

2\. Идем в

\[code lang="plain"\]HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\CVirtA\[/code\]

3\. Находим значение

\[code lang="plain"\]DisplayName\[/code\]

с содержимым типа

\[code lang="plain"\]@oem172.inf,%CVirtA\_Desc%;Cisco Systems VPN Adapter for 64-bit Windows \[/code\]

4\. Нажимает изменить. Для 64 битных систем заменяем всё на

\[code lang="plain"\]Cisco Systems VPN Adapter for 64-bit Windows\[/code\]

Для 32-х

\[code lang="plain"\]Cisco Systems VPN Adapter\[/code\]

5\. Сохраняем изменения и пробуем запустить VPN-клиент.