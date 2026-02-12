---
id: 76
title: 'Backup конфига Huawei Quidway на tftp.'
date: '2017-09-05T21:48:55+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=76'
permalink: /2017/09/05/backup-konfiga-huawei-quidway-na-tftp/
views:
    - '4936'
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
image: /wp-content/uploads/2017/09/switch-35568_640.png
categories:
    - 'Записи по Huawei'
tags:
    - huawei
    - сети
format: false
---

Файл конфига (vrpcfg.cfg) может быть в архиве zip или просто лежать в корне: **Копировать конфиг**

> `copy vrpcfg.cfg vrpcfg1.cfg`

**Закачать на сервер**> `tftp 172.10.2.12 put vrpcfg1.zip`

**Скачать с сервера**> `tftp 172.10.2.12 get vrpcfg1.zip`

После того как скачали и перезаписали конфиг необходимо перезагрузить оборудование, т.к. оборудование работает еще со старой конфигурацией. Но при перезагрузке будет предложено сохранить текущие настройки в файл-конфиг - говорим N и перезагружаемся.