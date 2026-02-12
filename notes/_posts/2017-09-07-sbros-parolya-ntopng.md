---
id: 104
title: 'Сброс пароля NtopNG'
date: '2017-09-07T18:58:59+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=104'
permalink: /2017/09/07/sbros-parolya-ntopng/
views:
    - '278'
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
    - 'Записи про мониторинг'
tags:
    - мониторинг
format: false
---

Генерируем новый пароль:

> `$echo -n "12345" | md5sum827ccb0eea8a706c4c34a16891f84e7b -`

Ставим новый пароль > `$sudo redis-cli SET ntopng.user.admin.password 827ccb0eea8a706c4c34a16891f84e7b`