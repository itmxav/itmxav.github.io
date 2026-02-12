---
id: 349
title: 'Как проверить установлен ли пакет Linux'
date: '2018-10-12T16:35:01+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=349'
permalink: /2018/10/12/kak-proverit-ustanovlen-li-paket-linux/
views:
    - '332'
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

**Проверка пакета opera через утилиту по управлению пакетами dpkg:**> `$ dpkg -s opera`

Если статусе installed - ok, то пакет установелен Версию пакета можно узнать: > `$ dpkg-query -l opera`

Просмотр всех установленных пакетов: > `$ dpkg --get-selections`

Фильтр с отображением местоположения: > `$ dpkg -L gcc-5`

**Через менеджер пакетов rpm:**> `$ rpm -q opera`

Все установленные пакеты: > `$ rpm -qa`

-- Источник - [losst.ru](https://losst.ru/kak-uznat-ustanovlen-li-paket-v-ubuntu)