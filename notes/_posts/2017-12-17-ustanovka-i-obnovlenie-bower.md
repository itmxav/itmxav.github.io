---
id: 117
title: 'Установка и обновление bower'
date: '2017-12-17T14:45:00+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=117'
permalink: /2017/12/17/ustanovka-i-obnovlenie-bower/
views:
    - '168'
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
    - bower
format: false
---

Установливаем с глобальным ключом g:

> `$ npm install -g bower`

Проверяем через поиск: > `$ which bower>> /usr/local/bin/bower`

Проверяем версию npm: > `$ npm -v`

Проверяем версию bower: > `$ bower -v`

*Если проблемы с "npm global path prefix", то перед установкой надо выполнить:*> `$ npm config set prefix /usr/local`

Для обновления bower можно установить: > `$ npm install -g bower-update`

А после можно и обновиться: > `$ bower-update`