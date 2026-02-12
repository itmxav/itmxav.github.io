---
id: 367
title: 'Как установить драйвер для видеокарт Intel [linux ubuntu 18.04]?'
date: '2018-11-24T12:16:14+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=367'
permalink: /2018/11/24/kak-ustanovit-drajver-dlya-videokart-intel-linux-ubuntu-18-04/
views:
    - '281'
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
    - '23'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Debian, Ubuntu etc.'
tags:
    - linux
format: false
---

Для обновления до последней версии драйвера xserver-video-intel надо добавить готовый репозиторий:

> `sudo add-apt-repository ppa:oibaf/graphics-drivers`

Обновить список пакетов: > `sudo apt-get update`

Теперь, обновить систему: > `sudo apt-get dist-upgrade`

Перезагрузиться. -- Источник - [help.ubuntu.ru](https://help.ubuntu.ru/wiki/драйвер_видеокарт_intel)