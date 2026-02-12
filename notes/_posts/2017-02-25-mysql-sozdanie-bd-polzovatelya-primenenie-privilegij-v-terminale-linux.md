---
id: 19
title: 'MySQL. Создание БД, пользователя, применение привилегий в терминале Linux.'
date: '2017-02-25T22:42:18+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=19'
permalink: /2017/02/25/mysql-sozdanie-bd-polzovatelya-primenenie-privilegij-v-terminale-linux/
views:
    - '504'
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
image: /wp-content/uploads/2017/02/2000px-Database-mysql.svg_.png
categories:
    - 'MySQL, MariaDB etc.'
    - 'Записи FastHowTo'
tags:
    - fasthowto
    - linux
    - mysql
    - сайт
format: false
---

Вход:

> `mysql -uroot -p`

Создание базы данных 'testdb': > `mysql> CREATE DATABASE `testdb`;`

Создания пользователя 'user' c паролем 'password': > `mysql> CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';`

Выдача всех привилегий на базу данных`testdb` для созданного пользователя'user': > `mysql> GRANT ALL PRIVILEGES ON `testdb`.* TO 'user'@'localhost';`

Обновление привилегий: > `mysql> FLUSH PRIVILEGES;`

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="300" src="https://www.youtube.com/embed/n367LdLzIkw" width="400"></iframe>