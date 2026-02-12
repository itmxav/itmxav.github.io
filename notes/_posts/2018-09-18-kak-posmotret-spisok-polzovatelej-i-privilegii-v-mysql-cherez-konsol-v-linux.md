---
id: 318
title: 'Как посмотреть список пользователей и привилегии в MySQL через консоль в Linux?'
date: '2018-09-18T14:36:30+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=318'
permalink: /2018/09/18/kak-posmotret-spisok-polzovatelej-i-privilegii-v-mysql-cherez-konsol-v-linux/
views:
    - '1035'
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
    - 'MySQL, MariaDB etc.'
tags:
    - mysql
format: false
---

Для того чтобы отобразить всех пользователей и затем, просмотрев их, узнать привилегии необходимого в MySQL через консоль, необходимо: Зайти под учетной записью root в MySQL. После, выбираем используемую базу данных MySQL:

> `mysql>use mysql;`

Делаем выбор имен всех пользователей, которые у нас существуют: > `mysql>select user from user;`

На экран будет выведен список всех пользователей MySQL. Для просмотра привилегий пользователя в MySQL вводим команду: > `mysql>SHOW GRANTS FOR nameuser@localhost;`

Где nameuser - нужное имя пользователя и просматриваем привилегии данного пользователя. -- Источник - [it-student.com.ua](http://it-student.com.ua/databases/tips/pokazatj-poljzovatelei-i-privilegii-mysql.html)