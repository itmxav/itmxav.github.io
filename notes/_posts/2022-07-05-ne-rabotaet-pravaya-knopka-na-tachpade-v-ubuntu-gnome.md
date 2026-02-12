---
id: 1350
title: 'Не работает правая кнопка на тачпаде в Ubuntu GNOME'
date: '2022-07-05T13:39:41+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=1350'
permalink: /2022/07/05/ne-rabotaet-pravaya-knopka-na-tachpade-v-ubuntu-gnome/
views:
    - '271'
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
    - linux
    - ubuntu
format: false
---

Если не работает правая кнопка на тачпаде в ubuntu 18+ GNOME, то можно прописать терминале:

Установить tweak-tool, если нет

> sudo apt-get install gnome-tweak-tool

Прописать и проверить работу кнопки

> gsettings set org.gnome.desktop.peripherals.touchpad click-method 'areas'

Для версий ниже:

> gsettings set org.gnome.desktop.peripherals.touchpad click-method 'fingers'

Если после перезагрузки ситуация возобновится, то можно закинуть эту команду в автозапуск.

\--

Источник - [форум Ubuntu](https://forum.ubuntu.ru/index.php?topic=303703.0)