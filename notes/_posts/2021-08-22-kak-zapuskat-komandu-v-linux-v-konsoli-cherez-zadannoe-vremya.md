---
id: 894
title: 'Как запускать команду в Linux в консоли через заданное время?'
date: '2021-08-22T18:17:17+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=894'
permalink: /2021/08/22/kak-zapuskat-komandu-v-linux-v-konsoli-cherez-zadannoe-vremya/
views:
    - '239'
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
    - команды
format: false
---

Чтобы запускать команду в Linux в консоли через заданное время надо задействовать команду watch. Синтаксис:

> `watch [options] command`

Например, запускать df каждые 10 секунд: > `watch -n 10 df -h`

Остановить ctrl+c. -- Дополнительный источник - [Как запускать команду Linux каждые X секунд навсегда](https://itisgood.ru/2018/06/08/kak-zapuskat-komandu-linux-kazhdye-x-sekund-navsegda/)