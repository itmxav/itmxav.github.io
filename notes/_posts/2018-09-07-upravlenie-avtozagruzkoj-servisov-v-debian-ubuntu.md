---
id: 282
title: 'Управление автозагрузкой сервисов в Debian (Ubuntu)'
date: '2018-09-07T15:10:46+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=282'
permalink: /2018/09/07/upravlenie-avtozagruzkoj-servisov-v-debian-ubuntu/
views:
    - '1458'
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

**Управление загрузкой сервисов с системой инициализации upstart**Отобразить статус всех сервисов: > **`service --status-all`**

Добавить в автозапуск > **`update-rc.d имя_сервиса defaults`**

Удалить из автозапуска > **`update-rc.d -f имя_сервиса remove`**

**Управление загрузкой сервисов через систему инициализации systemd**Отобразить статус всех сервисов: > **`systemctl list-units --type service --all`**

Проверить включен ли сервис > **`systemctl is–enabled имя_сервиса`**

Добавить в автозапуск > **`systemctl enable имя_сервиса`**

Удалить из автозапуска > **`systemctl disable имя_сервиса`**

-- Источник - [blog.ispsystem.info](http://blog.ispsystem.info/2016/10/debian-ubuntu.html)