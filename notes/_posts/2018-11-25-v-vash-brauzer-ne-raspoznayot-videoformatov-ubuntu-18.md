---
id: 371
title: 'В настоящее время ваш браузер не распознаёт ни один из доступных видеоформатов Firefox'
date: '2018-11-25T23:40:11+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=371'
permalink: /2018/11/25/v-vash-brauzer-ne-raspoznayot-videoformatov-ubuntu-18/
views:
    - '187'
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
    - '31'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Debian, Ubuntu etc.'
tags:
    - linux
format: false
---

Наткнулся на такую ошибку: *В настоящее время ваш браузер не распознаёт ни один из доступных видеоформатов на Linux Ubuntu 18.04 в firefox.*Для решения данной проблемы необходимо установить кодеки:

> `$ sudo apt-get install ubuntu-restricted-extras`