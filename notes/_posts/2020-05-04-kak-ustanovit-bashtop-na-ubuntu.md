---
id: 731
title: 'Как установить Bashtop на Ubuntu?'
date: '2020-05-04T00:47:51+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=731'
permalink: /2020/05/04/kak-ustanovit-bashtop-na-ubuntu/
views:
    - '259'
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
image: /wp-content/uploads/2020/05/bashtop.png
categories:
    - 'Записи про мониторинг'
tags:
    - linux
    - мониторинг
format: false
---

Монитор bashtop может показывать в терминале использование таких ресурсов как процессор, память, диски, трафик на сетевых интерфейсах,а также список процессов. Возможна сортировка данных и установка интервала обновления данных, а также можно вести лог ошибок. Чтобы установить Bashtop на Ubuntu нужно: -добавить репозиторий; -провести update; -установить bashtop.

> ` sudo add-apt-repository ppa:bashtop-monitor/bashtopsudo apt updatesudo apt install bashtop`

Более подробно можно ознакомиться с [Bashtop на GitHub](https://github.com/aristocratos/bashtop).