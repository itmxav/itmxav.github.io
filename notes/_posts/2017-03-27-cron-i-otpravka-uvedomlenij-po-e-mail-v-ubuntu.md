---
id: 50
title: 'Cron и отправка уведомлений по E-MAIL в Ubuntu.'
date: '2017-03-27T20:16:01+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=50'
permalink: /2017/03/27/cron-i-otpravka-uvedomlenij-po-e-mail-v-ubuntu/
views:
    - '1628'
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
image: /wp-content/uploads/2017/03/cron.png
categories:
    - 'Debian, Ubuntu etc.'
tags:
    - cron
    - linux
    - postfix
format: false
---

*cron – программа-демон, предназначенная для выполнения заданий в определенное время, или через определенные промежутки времени. Для редактирования заданий используется утилита crontab.*[Источник](http://help.ubuntu.ru/wiki/cron)**Управление через crontab:***!!Для редактирование надо использовать crontab -e*Создания файла расписания: > `crontab имя_файла`

Содержимое файла расписания: > `crontab -l`

Удаления текщего файла расписания > `crontab -r`

Редактирование текущего файла расписания > `crontab -e`

Редактирования файла расписания пользователя root: > `sudo crontab -e`

Ключ позволяющий осуществлять действия от другого пользователя. > `sudo crontab -u nameuser`

**Настройка файла расписания:**Выбор среды: > `SHELL=/bin/bash`

Кому отправить сообщение, если это необходимо, пользователю или по почте: > `MAILTO=nameuser(или nameuser@example.loc.org)`

Для отправки почты надо использовать MTA (Mail Transfer Agent). *Это виртуальный пакет, то есть на самом деле программы с таким названием не существует. Роль mail-transport-agent может выполнять exim, sendmail, postfix, ssmtp или ещё какая-то почтовая программа.* [Источник](http://help.ubuntu.ru/wiki/mta)Часто используется postfix. Установка: > `sudo apt-get install postfix`

при установке выбор был сделан "Интернет-сайт". Пример записи задания в список расписаний: > `* * * * * ls`

где \* \* \* \* \* это: > `минута час день_месяца месяц день_недели`

a ls команда, которая будет выполнятся в данном случае каждую минуту. Получается такой файл расписания без комментов: > `SHELL=/bin/bashMAILTO=nameuser@example.loc.org* * * * * ls`

-- В сети есть online-калькулятор cron - [Калькулятор Cron](http://www.sysmasters.net/kalkulyator-cron/)