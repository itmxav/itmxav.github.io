---
id: 887
title: 'Как задать время на коммутаторе Huawei?'
date: '2021-08-17T21:03:54+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=887'
permalink: /2021/08/17/kak-zadat-vremya-na-kommutatore-huawei/
views:
    - '982'
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
    - 'Записи по Huawei'
tags:
    - huawei
    - сети
format: false
---

Часто требуется настройка времени на сетевом оборудовании. Например, чтобы настроить время на оборудовании Huawei (6810, 5700 и т.д.) надо: Перейти в перивелегированый режим

> `sys`

Если вручную надо установить, то > `clock datetime hh:mm:ss YYYY-MM-DD`

Добавляем временную зону > `clock timezone MSK add hh:mm:ss`

или > `clock timezone MSK minus hh:mm:ss`

Если забирать в простом варианте с NTP-сервера, то > `ntp-service unicast-server XXX.XXX.XXX.XXX`