---
id: 88
title: 'TFTP-сервер на Windows 7 и включение службы Клиент TFTP'
date: '2017-09-06T17:37:49+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=88'
permalink: /2017/09/06/kak-podnyat-tftp-server-na-windows-7/
views:
    - '2486'
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
    - '158'
image: /wp-content/uploads/2017/09/computer-156949_640.png
categories:
    - 'Записи по Windows'
tags:
    - tftp
    - windows
format: false
---

Как поднять tftp-сервер на Windows 7 и как включить службу Клиент TFTP

> ***TFTP это?**TFTP (англ. Trivial File Transfer Protocol — простой протокол передачи файлов) используется главным образом для первоначальной загрузки без дисковых рабочих станций. TFTP, в отличие от FTP, не содержит возможностей аутентификации (хотя возможна фильтрация по IP-адресу) и основан на транспортном протоколе UDP.***Применение**Основное назначение TFTP — обеспечение простоты реализации клиента. В связи с этим он используется для загрузки бездисковых рабочих станций, загрузки обновлений и конфигураций в «умные» сетевые устройства, записи статистики с мини-АТС (CDR) и аппаратных маршрутизаторов/файрволов. [Источник](https://ru.wikipedia.org/wiki/TFTP)

**Как поднять TFTP-сервер**Качаем тот вариант, что нам нужен [здесь](http://tftpd32.jounin.net/tftpd32_download.html)В качестве примера был выбран tftpd32 standard edition (zip). Распаковываем/устанавливаем и запускаем с настройками: <center>![tftp](/wp-content/uploads/2017/09/tftp.png)</center>Смотрим чтобы антивирусы/брандмауэры не мешали и пробуем закачать или скачать, например, файлы конфига. ip-адрес компьютера = ip-адрес tftp-сервера. Примеры команды по передаче файлов tftp 192.168.1.2 GET file.txt tftp 192.168.1.2 PUT file.txt **Как включить клиента TFTP**Включение службы TFTP. Переходим в Панель управления: <center>![tftp1](/wp-content/uploads/2017/09/tftp1.png)</center>Переходим в Программы <center>![tftp2](/wp-content/uploads/2017/09/tftp2.png)</center>Переходим в Включение или отключение компонентов Windows <center>![tftp3](/wp-content/uploads/2017/09/tftp3.png)</center>Ставим галочку Клиент TFTP, нажимаем ОК и ждем пока все установится и запустится.