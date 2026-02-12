---
id: 1944
title: 'Как обновить Proxmox с 7.2 на 7.3?'
date: '2022-12-15T23:52:29+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=1944'
permalink: /2022/12/15/kak-obnovit-proxmox-s-7-2-na-7-3/
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
    - '1301'
image: /wp-content/uploads/2022/12/надпись.jpg
categories:
    - Виртуализация
tags:
    - proxmox
format: false
---

Чтобы обновить Proxmox с 7.2 на 7.3 надо:

1\. Проверить /etc/apt/sources.list

\[code lang="plain"\] deb http://ftp.ru.debian.org/debian bullseye main contrib deb http://ftp.ru.debian.org/debian bullseye-updates main contrib # security updates deb http://security.debian.org bullseye-security main contrib \[/code\]

2\. Если нет подписки, то надо подключить:

\[code lang="plain"\]deb http://download.proxmox.com/debian bullseye pve-no-subscription\[/code\]

3\. И обновить через:

\[code lang="plain"\]# apt-get update # apt-get dist-upgrade # reboot\[/code\]

Проверить версию:

\[code lang="plain"\]pveversion -v\[/code\]

Видео на Youtube:

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="220" src="https://www.youtube.com/embed/qbFzDRk69yo" title="Как обновить Proxmox с 7.2 на 7.3?" width="330"></iframe>

Видео на Rutube:

<iframe allow="clipboard-write; autoplay" allowfullscreen="" frameborder="0" height="220" mozallowfullscreen="" src="https://rutube.ru/play/embed/90919df599d95a2b70f726ab95cedb79" webkitallowfullscreen="" width="330"></iframe>