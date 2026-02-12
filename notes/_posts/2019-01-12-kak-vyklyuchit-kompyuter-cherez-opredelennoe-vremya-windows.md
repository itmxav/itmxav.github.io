---
id: 521
title: 'Как выключить компьютер через определенное время через командную строку? [Windows]'
date: '2019-01-12T16:13:42+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=521'
permalink: /2019/01/12/kak-vyklyuchit-kompyuter-cherez-opredelennoe-vremya-windows/
views:
    - '176'
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
    - '55'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Windows'
tags:
    - windows
format: false
---

Для того чтобы выключить компьютер через определенное время через командную строку необходимо: - Открыть командную строку - Вбить:

> `shutdown –s –t 11100`

Где команда shutdown используется для завершения сеанса пользователя, перезагрузки компьютера, перевода его в спящий режим или выключения питания. Ключи: s - завершение работы компьютера, t - задание задержки в секундах перед завершением работы компьютера. -- Подробнее - [Команда shutdown](https://ab57.ru/cmdlist/shutdown.html)