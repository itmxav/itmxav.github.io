---
id: 880
title: 'Как задать часовой пояс в Cisco Nexus?'
date: '2021-08-10T02:35:46+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=880'
permalink: /2021/08/10/kak-zadat-chasovoj-poyas-v-cisco-nexus/
views:
    - '337'
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
    - 'Записи по Cisco'
tags:
    - cisco
    - сети
format: false
---

Чтобы задать часовой пояс нужно прописать команду в следующем формате:

> `clock timezone zone-name offset-hours offset-minutes`

Например: > `clock timezone MSK 3 0`