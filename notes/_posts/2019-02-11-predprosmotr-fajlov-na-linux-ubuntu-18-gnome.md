---
id: 528
title: 'Предпросмотр файлов на Linux Ubuntu 18 Gnome'
date: '2019-02-11T23:06:14+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=528'
permalink: /2019/02/11/predprosmotr-fajlov-na-linux-ubuntu-18-gnome/
views:
    - '484'
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
    - '44'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Debian, Ubuntu etc.'
tags:
    - gnome
format: false
---

Иногда, лень открывать файлы, но посмотреть что в файле находится надо. Есть интересное решение - Gnome Sushi. Устанавливаем `unoconv` (для просмотра ods, odf и т.п.):

> `$ sudo apt-get install unoconv`

Собственно, Gnome Sushi: > `$ sudo apt-get install gnome-sushi`

Перезагружаем nautilus: > `$ nautilus -q`

Пример предпросмотра (выбрать файл и нажать на "пробел"): ![sushi](/wp-content/uploads/2019/02/sushi.png)