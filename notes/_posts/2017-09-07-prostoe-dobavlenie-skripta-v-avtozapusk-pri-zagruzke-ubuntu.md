---
id: 101
title: 'Простое добавление скрипта в автозапуск при загрузке Ubuntu'
date: '2017-09-07T11:39:05+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=101'
permalink: /2017/09/07/prostoe-dobavlenie-skripta-v-avtozapusk-pri-zagruzke-ubuntu/
views:
    - '194'
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
    - bash
    - linux
format: false
---

Создаем свой скрипт test.sh:

> `touch test.sh`

> `#!/bin/sh.........`

Ставим права на исполнение: > `sudo chmod ugo+x /home/test/test.sh`

Редактируем файл rc.local: > `sudo nano /etc/rc.local`

До exit 0 прописываем наш скрипт: > `#!/bin/sh -e/home/test/test.shexit 0`