---
id: 792
title: 'Как подключиться по serial (COM) через Putty в Linux Ubuntu?'
date: '2021-01-21T16:52:13+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=792'
permalink: /2021/01/21/kak-putty-serial-com-port-v-linux-ubuntu/
views:
    - '1136'
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
    - '57'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Debian, Ubuntu etc.'
tags:
    - linux
    - сети
format: false
---

Устанавливаем putty:

> `sudo apt updatesudo apt install putty`

Если при подключении по COM-порту появляется ошибка: > Unable to open connection to /dev/ttyS0: Unable to open serial port

Это значит пользователю не хватает прав для запуска. Можно запустить так > `sudo putty /dev/ttyS0 -serial -sercfg 9600,8,n,1,N`

Или добавить пользователя в группу, а после запустить putty. -- Источник про ошибку - [Как запустить Putty по serial (COM) порту в Linux?](https://ru.stackoverflow.com/questions/961654/Как-запустить-putty-по-serial-com-порту-в-linux)