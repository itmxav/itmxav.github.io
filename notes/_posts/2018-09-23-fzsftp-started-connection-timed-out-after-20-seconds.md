---
id: 344
title: 'Ошибка Connection timed out after 20 seconds of inactivity. Filezilla'
date: '2018-09-23T23:45:35+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=344'
permalink: /2018/09/23/fzsftp-started-connection-timed-out-after-20-seconds/
views:
    - '526'
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
    - '97'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Linux'
tags:
    - filezilla
format: false
---

После обновления filezilla не удается подключиться к серверу по stfp. Логи: Статус: Соединяюсь с IP\_адрес:Номер\_порта... Ответ: fzSftp started, protocol\_version=8 Команда: open "username@IP\_адрес" Номер\_порта Ошибка: Соединение прервано после 20 секунд неактивности Ошибка: Невозможно подключиться к серверу Статус: Ожидание повтора... Статус: Соединяюсь с IP\_адрес:Номер\_порта... Или fzSftp started, protocol\_version=8 ; Connection timed out after 20 seconds of inactivity; Could not connect to server; Возможное решение - увеличения времени ожидания:

> `0)Проверьте, не блокирует ли firewall сетевое соединение. Если да, то разрешаем и проверяем возможность подключения1)Открывает filezilla2)Переходим во вкладку "Редактирование"3)Пункт "Настройка"4)Меняем значение "Время ожидание сек" с 20 на 30. Нажимаем ОК.5)Пробуем подключиться с серверу снова.`

Если проблема не решена, то попробуйте увеличить время ожидание до 40 сек.