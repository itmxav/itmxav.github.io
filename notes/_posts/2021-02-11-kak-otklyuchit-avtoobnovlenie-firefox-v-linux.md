---
id: 812
title: 'Как отключить автообновление Firefox в Linux?'
date: '2021-02-11T01:24:01+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=812'
permalink: /2021/02/11/kak-otklyuchit-avtoobnovlenie-firefox-v-linux/
views:
    - '1132'
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
    - firefox
    - linux
format: false
---

Чтобы отключить обновление Firefox в Linux: 1. В адресной строке прописать и открыть список параметров:

> `about:config`

2. Найти через поиск нужный параметр и изменить значение: > `app.update.auto — автоматическое обновление браузера (значение false)app.update.enabled — обновление браузера (значение false)`

UPD: Есть ещё один параметр: > `DisableAppUpdate - значение true`

[Источник информации](https://support.mozilla.org/ru/kb/upravlenie-obnovleniyami-firefox)