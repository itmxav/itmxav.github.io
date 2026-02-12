---
id: 121
title: 'Установка git-lfs на Linux'
date: '2017-12-17T15:06:44+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=121'
permalink: /2017/12/17/ustanovka-git-lfs-na-linux/
views:
    - '429'
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
    - git
format: false
---

Пример установки git-lfs на Ubuntu. (Для других дистрибутивов смотрите [ здесь](https://packagecloud.io/github/git-lfs)) Качаем скрипт по добавлению репозитория и выполняем его:

> $ curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash

Устанавливаем git-lfs из репозитория: > $ sudo apt-get install git-lfs=2.3.4