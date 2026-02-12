---
id: 128
title: 'Изменение пароля пользователя Mysql (консоль)'
date: '2018-01-07T15:14:37+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=128'
permalink: /2018/01/07/kak-izmenit-parol-polzovatelsya-mysql-konsol/
views:
    - '260'
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

Для того чтобы изменить пароль пользователя, под которым зашли,необходимо:

> $mysql -uПОЛЬЗОВАТЕЛЬ -p mysql&gt;SET PASSWORD = PASSWORD('пароль') mysql&gt;FLUSH PRIVILEGES;

Если нужно уменить пароль другого пользователя, то сначала заходим под рутом: > $mysql -uroot -p mysql&gt;SET PASSWORD FOR 'mysqluser'@'localhost' = PASSWORD('пароль'); mysql&gt;FLUSH PRIVILEGES;

Вместо localhost может быть или ip, или %. т.е. откуда пользователю можно будет подклоючаться к MySql. *Изменение через SQL-запрос:*> UPDATE mysql.user SET Password=PASSWORD('пароль') WHERE User='mysqluser' AND Host='localhost'; FLUSH PRIVILEGES;