---
id: 191
title: 'E: Sub-process /usr/bin/dpkg returned an error code'
date: '2018-07-12T14:06:32+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=191'
permalink: /2018/07/12/e-sub-process-usrbindpkg-returned-an-error-code/
views:
    - '228'
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
wp_statistics_words_count:
    - '103'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Debian, Ubuntu etc.'
tags:
    - linux
format: false
---

При обновлении пакетов Ubuntu появляется ошибка «E: Sub-process /usr/bin/dpkg returned an error code», при этом система не может закончить установку какого-либо пакета. Исправляем ошибку: Заходим в каталог /var/lib/dpkg/info и находим в ней все файлы с именем обрабатываемого пакета (из-за которого выдается ошибка) и переименовываем их все (например, в info.paket.bak)… Далее, удаляем нужный пакет. `#cd /var/lib/dpkg/info#mv info.paket.* info.paket.bak.*#rm paket.*`Запускаем команду исправления: `$sudo apt-get install -f && sudo dpkg --configure -a`Затем устанавливаем пакет по новой (если конечно он еще нужен). Проверяем, создались ли новые файлы в папке /var/lib/dpkg/info, а если нет — то переименовываем наши файлы обратно. PS: если не получилось, пробуем еще так: `sudo DEBCONF_DEBUG=developer apt-get install -f`-- Источник - pingvinoff .net/2011/12/25/reshenie-oshibki-e-sub-process-usrbindpkg-returned-an-error-code-na-debian/