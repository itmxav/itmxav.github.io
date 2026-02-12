---
id: 303
title: 'Обновление базы данных (tz database) часовых поясов в Linux'
date: '2018-09-12T15:21:28+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=303'
permalink: /2018/09/12/obnovlenie-bazy-dannyx-tz-database-chasovyx-poyasov-v-linux/
views:
    - '255'
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
    - 'Записи по Linux'
tags:
    - linux
    - время
format: false
---

Последние обновления базы данных часовых поясов публикуются на сайте международной организации IANA (The Internet Assigned Numbers Authority) в разделе Time Zone Database - Latest Version – Time Zone Data v. yyyy – файл именем tzdatayyyyx.tar.gz, где yyyy- год, x – версия файла. Эти обновления отражают актуальные границы часовых поясов и правила перехода на зимнее/летнее время. Скачать актуальную версию можно также с использованием FTP-доступа:

> `wget ftp://ftp.iana.org/tz/tzdata-latest.tar.gz`

Хранение этих данных не потребуется, поэтому, все последующие операции можно выполнить в каком-нибудь временном каталоге, который в дальнейшем, удалить. Создаем временный каталог, например, /tmp/tzdata и переходим в него : > `# mkdir /tmp/tzdata# cd /tmp/tzdata`

Скачиваем базу данных часовых поясов: > `# wget ftp://ftp.iana.org/tz/tzdata-latest.tar.gz`

Извлекаем содержимое архива: > `# tar zxvf tzdata-latest.tar.gz`

После распаковки, в каталоге будут находиться текстовые файлы с документацией и файлы настроек временных зон по регионам (africa, asia, europe, и т.п. ) Настройки системного времени в операционных системах Linux, определяются содержимым файла /etc/localtime. Данный файл не является текстовым и создается путем компиляции из исходного файла соответствующей временной зоны специальной утилитой zic, выполняемой с правами суперпользователя root . Утилита zic читает текстовый файл с описаниями зон и на выходе формирует бинарные файлы специального формата в каталоге /usr/share/zoneinfo/. Для замены, например, настроек для Европы, выполняется команда zic europe - где europe - имя файла из распакованного архива. Для азиатского региона - zic asia и т.п. В результате выполнения данной команды произойдет обновление файлов с данными временных настроек в каталоге /usr/share/zoneinfo/Europe/. Например, для Москвы, настройки содержатся в файле /usr/share/zoneinfo/Europe/Moscow и для их применения достаточно создать символьную ссылку для /etc/localtime: > `ln -sf /usr/share/zoneinfo/Europe/Moscow /etc/localtime`

Для проверки системного времени можно использовать команду date -- Источник - [white55.ru](https://white55.ru/tz.html)-- Дополнительная информация - [Синхронизация времени по Интернету в Linux](/2017/09/06/sinxronizaciya-vremeni-po-internetu-v-linux/)- [Как установить время и дату в Linux вручную (date)?](/2018/09/17/kak-ustanovit-vremya-i-datu-v-linux-vruchnuyu-date/)