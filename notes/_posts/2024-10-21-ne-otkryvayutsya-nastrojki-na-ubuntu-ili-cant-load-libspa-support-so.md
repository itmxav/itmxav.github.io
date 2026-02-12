---
id: 3079
title: 'Не открываются настройки на Ubuntu или can&#8217;t load libspa-support.so'
date: '2024-10-21T11:24:14+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3079'
permalink: /2024/10/21/ne-otkryvayutsya-nastrojki-na-ubuntu-ili-cant-load-libspa-support-so/
views:
    - '68'
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
    - ubuntu
format: false
---

После одного из обновления на Ubuntu поймал ошибку, когда при нажитии на "настройки" эти настройки системы не открывались.

При вызове *gnome-control-center* вылетела ошибка

\[code lang="plain"\]can't load /usr/lib/x86\_64-linux-gnu/spa/support/libspa-support.so: /usr/lib/x86\_64-linux-gnu/spa/support/libspa-support.so: cannot open shared object file: No such file or directory Segmentation fault (core dumped)\[/code\]

Нечто похожее нашел [bugs.launchpad.net](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1862359)   
Помогла установка pipewire, в которой и был нужный файл.

\[code lang="plain"\]apt install pipewire\[/code\]