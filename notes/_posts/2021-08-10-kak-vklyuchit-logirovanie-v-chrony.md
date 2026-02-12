---
id: 883
title: 'Как включить логирование в Chrony?'
date: '2021-08-10T02:46:45+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=883'
permalink: /2021/08/10/kak-vklyuchit-logirovanie-v-chrony/
views:
    - '1075'
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
    - время
format: false
---

Если Chrony не пишет лог, т.е. в /var/log/chrony пусто, то надо в chrony.conf раскомментировать строку:

> `#log measurements statistics tracking`

Параметры: - measurements Записывает необработанные измерения NTP и сопутствующую информацию в файл measurements.log. - statistics Записывать данные обработки регрессии в файл statistics.log. -tracking Записывает изменения в оценке диапазона системного отставания или опережения времени в файл tracking.log. -rtc Лог системных часов реального времени. -refclocks Записывает "сырые" и обработанные показания эталонных часов в файл refclocks.log. -tempcomp Записывает показания температурных датчиков и частоты компенсации в файл tempcomp.log. Файлы записываются в каталог, указанный как logdir. После надо перезапустить сервис chronyd > `systemctl restart chronyd.service`

-- Источник по параметрам - [Настройка реализации NTP chrony. ](https://bjdarticles.blogspot.com/2019/04/ntp-chrony.html)