---
id: 917
title: 'Сброс пароля на Cisco Catalyst 3850R / Cisco Catalyst 3850R Password Recovery'
date: '2022-02-21T17:27:29+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=917'
permalink: /2022/02/21/sbros-parolya-na-cisco-catalyst-3850r-cisco-catalyst-3850r-password-recovery/
views:
    - '309'
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
    - '72'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Cisco'
tags:
    - cisco
    - сети
format: false
---

1\. Подключаем консольный кабель.

2\. Выключаем по питанию.

3\. Нажимает кнопку Mode и держим

4\. Включаем. Ждем 12 секунд и отпускаем кнопку Mode.

5\. Ждем поле для ввода команд

> `Switch:`

6\. Задаем параметр "загрузиться игнориря конфиг":

> `Switch: SWITCH_IGNORE_STARTUP_CFG=1`

7\. Загружемся:

> `Switch: boot`

8\. Далее переходим в привелегерованный режим и загружаем наш конфиг:

> `Switch# copy start runn`

9\. Удаляем старый пароль и, если нужно, то делаем другие настройки:

> `Switch(conf)#no enable secret`

10\. Устанавливаем новый пароль и сохраняем конфигурацию:

> `Switch(conf)#enable secret PASSWORD`
> 
> Switch# copy runn start

или

> `Switch# wr mem`

\--

Источник - https://blog.router-switch.com/2014/01/cisco-catalyst-3850-password-recovery/