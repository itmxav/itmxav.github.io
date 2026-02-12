---
id: 26
title: 'MySQL. Экспорт и импорт БД через терминал Linux.'
date: '2017-02-25T23:25:48+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=26'
permalink: /2017/02/25/mysql-eksport-i-import-bd-cherez-terminal-linux/
views:
    - '263'
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
    - '47'
image: /wp-content/uploads/2017/02/2000px-Database-mysql.svg_.png
categories:
    - 'MySQL, MariaDB etc.'
tags:
    - linux
    - mysql
format: false
---

**Экспорт БД**Экспорт одной БД: > `mysqldump -uNameUser -p NameDB > DB.sql`

Экспорт нескольких БД: > `mysqldump -uroot -p -B DB1 DB2 DB3 > DB1_3.sql`

Экспорт всех БД в один файл: > `mysqldump -uroot -p -A > DB_ALL.sql`

**Импорт БД**Перед тем как импортировать БД надо ее создать. Как создать написано [здесь](/2017/02/25/mysql-sozdanie-bd-polzovatelya-primenenie-privilegij-v-terminale-linux/). Импорт БД: > `mysql -uNameUser -p NameDB < DB.sql`