---
id: 684
title: 'Не запрашивает пароль root MariaDB'
date: '2020-03-20T15:22:50+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=684'
permalink: /2020/03/20/ne-zaprashivaet-parol-root-mariadb/
views:
    - '313'
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
    - linux
    - mariadb
    - mysql
format: false
---

После установки MariaDB, на входе в СУБД не запрашивается пароль для пользователя root. Все просто. Надо задать пароль для root :) 1 вариант:

> `mysqladmin -u root password newpass`

2 вариант: > `# mysql -u rootMariaDB [(none)]> use mysql;Database changedMariaDB [mysql]> update user set password=PASSWORD("my-new-cool-password") where User='root';MariaDB [mysql]> flush privileges;MariaDB [mysql]> update user set plugin='' where User='root';MariaDB [mysql]> quit;Bye# systemctl restart mariadb`

-- Источники: - [ ответ на stackoverflow](https://ru.stackoverflow.com/questions/964570/maria-db-входит-под-root-без-пароля-а-подключиться-через-localhost-не-получаетс)- [ ответ на linux.org.ru](https://www.linux.org.ru/forum/admin/13554233)