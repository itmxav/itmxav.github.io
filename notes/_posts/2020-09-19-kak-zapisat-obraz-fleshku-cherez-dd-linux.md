---
id: 764
title: 'Как записать образ ОС на флешку через dd? Linux'
date: '2020-09-19T23:45:06+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=764'
permalink: /2020/09/19/kak-zapisat-obraz-fleshku-cherez-dd-linux/
views:
    - '619'
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
format: false
---

> `$ sudo dd if=/home/chocobo/Загрузки/linuxmint-18-cinnamon-32bit.iso of=/dev/sdb bs=4M`

if - путь к образу of - куда записать (физический устройство) bs - размер блока Интересный ход. Качаем с Инета и сразу записываем (нужно установить curl) > `$ curl -L http://mirror.yandex.ru/linuxmint/stable/18/linuxmint-18-mate-64bit.iso | sudo dd of=/dev/sdb bs=4M`

-- Источник - [Запись образа командой dd](https://www.linuxmint.com.ru/viewtopic.php?t=2943)