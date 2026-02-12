---
id: 3472
title: 'Как отправить UDP пакет с Linux?'
date: '2025-11-14T15:04:47+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3472'
permalink: /2025/11/14/kak-otpravit-udp-paket-s-linux/
views:
    - '109'
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
wp_statistics_words_count:
    - '33'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Linux'
tags:
    - linux
    - сети
format: false
---

Бывают ситуации когда надо отправить тестовые UDP-пакеты на какой-то адрес и конкретный порт. Сделать это можно следующим способом:

> echo -n "test" &gt;/dev/udp/IP\_ADDRESS/PORT

IP\_ADDRESS - адрес на который надо отправить пакет  
PORT - конкретный порт куда отправить