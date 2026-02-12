---
id: 369
title: 'Как установить Ubuntu Tweak в Ubuntu 18.04 ?'
date: '2018-11-24T13:15:28+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=369'
permalink: /2018/11/24/kak-ustanovit-ubuntu-tweak-v-ubuntu-18-04/
views:
    - '251'
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
format: false
---

В Ubuntu 18.04 для установки Ubuntu Tweak необходимы пакеты libgksu, gksu, который были исключены из репозитория. Поэтому все "вручную" надо ставить через терминал:

> `$ cd /tmp; wget http://se.archive.ubuntu.com/ubuntu/pool/universe/libg/libgksu/libgksu2-0_2.0.13~pre1-9ubuntu2_amd64.deb http://se.archive.ubuntu.com/ubuntu/pool/universe/g/gksu/gksu_2.0.2-9ubuntu1_amd64.deb http://se.archive.ubuntu.com/ubuntu/pool/universe/g/gksu/gksu_2.0.2-9ubuntu1_amd64.deb https://launchpad.net/~trebelnik-stefina/+archive/ubuntu/ubuntu-tweak/+files/ubuntu-tweak_0.8.8-5~zesty_all.deb; sudo dpkg -i *.deb; sudo apt install -f -y`

-- Более подробно: Источник - [compizomania.blogspot.com](https://compizomania.blogspot.com/2018/05/ubuntu-tweak-ubuntu-1804-bionic.html)