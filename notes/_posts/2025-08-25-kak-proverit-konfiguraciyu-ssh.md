---
id: 3376
title: 'Как проверить конфигурацию SSH?'
date: '2025-08-25T18:00:41+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3376'
permalink: /2025/08/25/kak-proverit-konfiguraciyu-ssh/
views:
    - '26'
wp_statistics_words_count:
    - '17'
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
    - 'Записи по DevOps'
tags:
    - ssh
format: false
---

Иногда бывает нужно проверить конфиг SSH. Сделать это можно так:

> sshd -t

Если ошибок нет, то ничего не выдаст.