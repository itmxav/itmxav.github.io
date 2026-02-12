---
id: 2967
title: 'Как включить IP Forwarding в Linux?'
date: '2024-08-09T17:06:28+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2967'
permalink: /2024/08/09/kak-vklyuchit-ip-forwarding-v-linux/
views:
    - '79'
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
    - 'Записи по Linux'
tags:
    - linux
    - сети
format: false
---

Чтобы включить пересылку пакетов между интерфейсами на Linux надо для начала проверить состояние форвардинга:  
\[code lang="plain"\]sysctl net.ipv4.ip\_forward\[/code\]  
Если **net.ipv4.ip\_forward = 0**, то выключен. Если **1** - включен.

Времененно включить IP Forwarding можно командой   
\[code lang="plain"\]# sysctl -w net.ipv4.ip\_forward=1\[/code\]  
Отключить   
\[code lang="plain"\]# sysctl -w net.ipv4.ip\_forward=0\[/code\]

Чтобы постоянно был включен IP Forwarding надо прописать в файле **/etc/sysctl.conf**   
\[code lang="plain"\]net.ipv4.ip\_forward = 1\[/code\]  
Постоянно отключен   
\[code lang="plain"\]net.ipv4.ip\_forward = 0\[/code\]  
Далее применяем конфигурацию  
\[code lang="plain"\]# sysctl -p\[/code\]