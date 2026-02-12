---
id: 2608
title: 'Как установить шрифты в Linux?'
date: '2024-02-02T13:03:57+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2608'
permalink: /2024/02/02/kak-ustanovit-shrifty-v-linux/
views:
    - '42'
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
format: false
---

1\. Создаем папку ~/.fonts:

\[code lang="plain"\]$ mkdir ~/.fonts\[/code\]

2\. Копируем нужный шрифт:

\[code lang="plain"\]$ cp OpenSans.ttf ~/.fonts\[/code\]

3\. Обновляем кэш шрифтов и перезапускаем программы для работы со шрифтами.

\[code lang="plain"\]$ fc-cache -f -v\[/code\]

или просто перезагружаем компьютер.