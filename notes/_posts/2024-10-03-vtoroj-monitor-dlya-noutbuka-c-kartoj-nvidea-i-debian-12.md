---
id: 3038
title: 'Второй монитор для ноутбука c картой Nvidea и Debian 12'
date: '2024-10-03T13:53:34+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3038'
permalink: /2024/10/03/vtoroj-monitor-dlya-noutbuka-c-kartoj-nvidea-i-debian-12/
views:
    - '38'
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
    - 'Debian, Ubuntu etc.'
tags:
    - debian
format: false
---

Если есть ноутбук с видеокартой Nvidia и при подключении второго монитора экран этого монитора белый, то скорее всего не хватает драйверов как написано в [wiki](https://wiki.debian.org/NvidiaGraphicsDrivers#Debian_12_.22Bookworm.22). Вот [здесь](https://us.download.nvidia.com/XFree86/Linux-x86_64/535.183.01/README/supportedchips.html) можно посмотреть поддержку карт Nvidea.   
1\. Подключаем репозиторий в /etc/apt/sources.list

\[code lang="plain"\]deb http://deb.debian.org/debian/ bookworm main contrib non-free non-free-firmware\[/code\]

  
2\. И устанавливаем необходимое ПО

\[code lang="plain"\]apt update apt install nvidia-driver firmware-misc-nonfree\[/code\]

  
3\. Перезагружаем ноутбук.