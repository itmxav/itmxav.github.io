---
id: 2112
title: 'Как обратиться к сайту без DNS?'
date: '2023-02-03T12:37:18+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=2112'
permalink: /2023/02/03/kak-obratitsya-k-sajtu-bez-dns/
views:
    - '319'
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
image: /wp-content/uploads/2023/02/Надпись.png
categories:
    - 'Записи по DevOps'
tags:
    - dns
    - linux
    - windows
format: false
---

Если DNS заблокирован или по каким-то причинам нет возможности сопоставить домен и ip, но, и то, и то известно, то:

Для Unix-систем:  
1\. Открыть /etc/hosts.  
2\. Сделать запись:  
\[code lang="plain"\]"ip" "domain"\[/code\] 3. Сохранить и проверить.

Для Windows:  
1\. Открыть C:\\Windows\\System32\\drivers\\etc\\hosts  
2\. Сделать запись:  
\[code lang="plain"\]"ip" "domain"\[/code\] 3. Сохранить и проверить.

Видео на Youtube:

<iframe allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen="" frameborder="0" height="220" src="https://www.youtube.com/embed/HUKOTVCt_Hw" title="Как обратиться к сайту без DNS? Debian" width="330"></iframe>

Видео на Rutube:

<iframe allow="clipboard-write; autoplay" allowfullscreen="" frameborder="0" height="220" mozallowfullscreen="" src="https://rutube.ru/play/embed/5ca3c67744b37debfa0d04baadab675e" webkitallowfullscreen="" width="330"></iframe>