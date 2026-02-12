---
id: 679
title: 'Автозагрузка в Debian 9 и rc.local'
date: '2020-03-20T15:09:04+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=679'
permalink: /2020/03/20/avtozagruzka-v-debian-9-i-rc-local/
views:
    - '653'
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
    - '100'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Debian, Ubuntu etc.'
tags:
    - debian
    - linux
format: false
---

В Debian 9 по умолчанию нет файла rc.local. Чтобы вернуть автозапуск через rc.local нужно создать юнит в systemd: Создаем сам rc.local и добавляем в содержимое следующее:

> `# vim /etc/rc.local`

> `#!/bin/sh -e## rc.local## This script is executed at the end of each multiuser runlevel.# Make sure that the script will "exit 0" on success or any other# value on error.## In order to enable or disable this script just change the execution# bits.## By default this script does nothing.````exit 0`

Добавляем права на запуск rc.local: > `# chmod +x /etc/rc.local`

Создаем юнит для systemd: > `# vim /etc/systemd/system/rc-local.service`

Прописываем в rc-local.service: > `[Unit]Description=/etc/rc.local CompatibilityConditionPathExists=/etc/rc.local``[Service]Type=forkingExecStart=/etc/rc.local startTimeoutSec=0StandardOutput=ttyRemainAfterExit=yesSysVStartPriority=99``````[Install]WantedBy=multi-user.target`

Добавляем и запускаем: > `# systemctl enable rc-local# systemctl start rc-local`