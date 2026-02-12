---
id: 905
title: 'Как очистить swap (своп) Linux?'
date: '2021-11-26T02:54:37+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=905'
permalink: /2021/11/26/kak-ochistit-swap-svop-linux/
views:
    - '226'
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

Чтобы очистить данные из swap нужно выполнить и дождаться окончание выполнения команды:

> `swapoff -a`

Включить: > `swapon -a`

Посмтреть использование swap можно так : > `free -m`