---
id: 847
title: 'Как посмотреть информацию о critical на Cisco ASR1001?'
date: '2021-07-08T13:11:46+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=847'
permalink: /2021/07/08/kak-posmotret-informaciyu-o-critical-na-cisco-asr1001/
views:
    - '765'
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

Горит лампочка critical на Cisco asr 1001/1000. Можно посмотреть информацию о состоянии через команду:

> `show facility-alarm status `

В выводе покажет порт и сообщение с возможной проблемой.