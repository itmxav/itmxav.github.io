---
id: 256
title: 'Как создать пользователя с правами только на чтение (read-only) в MySQL'
date: '2018-08-06T11:48:34+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=256'
permalink: /2018/08/06/polzovatelya-s-pravami-tolko-chtenie-read-only-v-mysql/
views:
    - '867'
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
    - '46'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'MySQL, MariaDB etc.'
tags:
    - mysql
format: false
---

Исходим из того, что у нас уже есть бд и пользователь. Если нет, то [здесь](/2017/02/25/mysql-sozdanie-bd-polzovatelya-primenenie-privilegij-v-terminale-linux/) написано как создать. Заходим в mysql:

> `# mysql -uroot -p`

Ставим необходимые привилегии пользователю *userwithRO* с паролем *userwithRO\_passw* к БД *testdb*: > `mysql> grant select on 'testdb'.* to 'userwithRO'@'localhost' identified by 'userwithRO_passw';`

Обновляем привилегии: > `mysql> flush privileges;`

Выходим: > `mysql> quit`