---
id: 3510
title: 'Ubuntu: Требуется аутентификация для запуска демона gvfsd-admin'
date: '2025-11-19T14:06:46+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3510'
permalink: /2025/11/19/ubuntu-trebuetsya-autentifikaciya-dlya-zapuska-demona-gvfsd-admin/
views:
    - '46'
wp_statistics_words_count:
    - '46'
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
    - ubuntu
format: false
---

На ubuntu может неожиданно появиться окно с надписью

> Требуется подтверждение подлинности. Требуется аутентификация для запуска демона gvfsd-admin

И поле для ввода пароля.

Такое происходит, когда какая-то программа взаимодействует с gvfsd. В каждом случае надо разбираться отдельно.

Костыль:   
1\. Нажимем ALT+F2  
2\. Вводим "r" и нажимаем Enter.

Вот [здесь](https://www.reddit.com/r/Ubuntu/comments/t0fkf8/why_did_this_thing_pop_up/?tl=ru) есть пример причины возникновения.