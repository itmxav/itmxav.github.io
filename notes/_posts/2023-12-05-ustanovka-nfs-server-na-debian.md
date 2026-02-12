---
id: 2422
title: 'Установка NFS-server на Debian'
date: '2023-12-05T20:46:05+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2422'
permalink: /2023/12/05/ustanovka-nfs-server-na-debian/
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
    - '154'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Debian, Ubuntu etc.'
tags:
    - debian
    - linux
    - nfs
format: false
---

1\. Обновляемся и ставим нужные пакеты

\[code lang="plain"\] apt update; apt upgrade; apt install nfs-kernel-server nfs-common portmap\[/code\]

  
2\. Запускаем сервис и добавляем его в автозагрузку

\[code lang="plain"\]systemctl start nfs-server; systemctl enable nfs-server\[/code\]

  
3\. Создаем папку, где всё будет лежать

\[code lang="plain"\]mkdir -p /var/nfsiso\[/code\]

  
4\. Редактируем файл exports

\[code lang="plain"\]nano /etc/exports /var/nfsiso 192.168.2.0/24(rw, async, no\_subtree\_check, no\_root\_squash)\[/code\]

  
*Вместо пробелов - tab.*  
*Если нужен доступ для всех, то вместо подсети указыается "\*"*  
*Лучше не использовать no\_root\_squash, чтобы нехорошие пользователи не могли загрузить нехорошее.*

  
5\. Перезагружаемся

\[code lang="plain"\]reboot\[/code\]

Видео:

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="220" src="https://www.youtube.com/embed/icWdUceVMAE" title="Установка NFS-server на Debian" width="330"></iframe>