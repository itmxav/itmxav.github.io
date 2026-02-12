---
id: 271
title: 'Как установить и настроить rsnapshot на Ubuntu, CentOS?'
date: '2018-08-17T15:54:29+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=271'
permalink: /2018/08/17/kak-ustanovit-i-nastroit-rsnapshot-na-ubuntu-centos/
views:
    - '428'
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
    - 'RedHat, CentOS etc.'
    - 'Записи по Linux'
tags:
    - backup
    - linux
format: false
---

- Содержание:

- [Что такое rsnapshot?](#1 "Что такое Git?")
- [Установка](#2 "Установка")
- [Настройка](#3 "Установка")

#### *Что такое rsnapshot?*

rsnapshot – Базирующаяся на rsync утилита на Perl для создания резервных копий. Особенностью является ориентация на создание инкрементных полных снапшотов файловой системы через заданный интервал времени, для экономии места на диске. Файлы линкуются как hard link. #### *Установка*

Ubuntu: > `# apt-get install rsnapshot`

CentOS: > `# yum install rsnapshot`

#### *Настройка*

Создаем папку для снимков: > `# mkdir /var/data/snapshots`

Открывем конфигурационный файл текстовым редактором <span style="color: red;">**В конфигурационном файле недопустимы пробелы — только табы!**</span>> `# nano /etc/rsnapshot.conf`

Настроим следующие параметры: > `snapshot_root - директория, в которую закидываем инкрементно "снимки".interval xxx yy - ххх - название интервала(например hourly, daily), yy - количество снимков для каждого. Например:interval hourly 6interval daily 7`

Означает, что мы хотим хранить 6 ежечасных копий и 7 ежемесячных. Если уже доступно указанное количество копий, rsnapshot будет заменить старую более новой. <span style="color: red;">**Указание завершающих слешей "/" в названии папок обязательно!**</span>Добавляем папку /etc/ с локальной машины в папку localhost/ > `backup /etc/ local/`

После изменения настроек следует выполнить их проверку: > `# rsnapshot configtest`

Запуск в проверочном режиме (только вывод команд без их выполнения): > `# rsnapshot -t hourly`

Создание первого архива: > `# rsnapshot hourly`

Просмотр сколько места занимают резервные копии: > `# rsnapshot du`

Закидываем в планировщик задач: > `/etc/cron.d/rsnapshot0 */4 * * * root /usr/bin/rsnapshot hourly30 3 * * * root /usr/bin/rsnapshot daily0 3 * * 1 root /usr/bin/rsnapshot weekly30 2 1 * * root /usr/bin/rsnapshot monthly`

-- Источники: [wiki.enchtex.info](https://wiki.enchtex.info/tools/archiving/rsnapshot)[habr.com](https://habr.com/post/45912/)