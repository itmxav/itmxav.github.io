---
id: 325
title: 'MySQL: ERROR 1396 (HY000): Operation DROP USER failed for &#8216;username&#8217;'
date: '2018-09-20T17:25:13+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=325'
permalink: /2018/09/20/mysql-error-1396-hy000-operation-drop-user-failed-for-username/
views:
    - '309'
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
    - '233'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'MySQL, MariaDB etc.'
tags:
    - mysql
format: false
---

При удалении пользователя MySQL сообщает об ошибке:

> `mysql> drop user usertest;ERROR 1396 (HY000): Operation DROP USER failed for 'usertest'@'%'`

Хотя пользователь вроде есть: > `mysql> SELECT User FROM mysql.user;+-------------+| User |+-------------+| usertest|`

Проверяем права пользователя: > `mysql> show grants for 'usertest'@'%';ERROR 1141 (42000): There is no such grant defined for user 'usertest' on host '%'`

При выборке надо добавлять поле Host: > `mysql> select User, Host from mysql.user where user like 'usertest';+--------+-----------+| User | Host |+--------+-----------+| usertest| localhost |+--------+-----------+1 row in set (0.00 sec)`

Повторяем запрос: > `mysql> show grants for 'usertest'@'localhost';+-----------------------------------------------------------------+| Grants for usertest@localhost |+-----------------------------------------------------------------+| GRANT USAGE ON *.* TO 'usertest'@'localhost' IDENTIFIED BY PASSWORD '*5EF6800D2864A93C2BAC3C4DF69A43687CA7DC90' || GRANT ALL PRIVILEGES ON `usertest_db1`.* TO 'usertest'@'localhost' |+-----------------------------------------------------------------+2 rows in set (0.00 sec)`

И теперь удаляем: > `mysql> drop user 'usertest'@'localhost';Query OK, 0 rows affected (0.00 sec)`

Если имя было указано верно, но данный способ не помог, то проверьте активность сессий пользователя: > `mysql> select * from information_schema.processlist where user='usertest';+------+---------+-----------------+---------+---------+------+-------+------+| ID | USER | HOST | DB | COMMAND | TIME | STATE | INFO |+------+---------+-----------------+---------+---------+------+-------+------+| 6602 | usertest| localhost:38181 | usertest| Sleep | 237 | | NULL || 1 | usertest| localhost:35533 | usertest| Sleep | 120 | | NULL |+------+---------+-----------------+---------+---------+------+-------+------+2 rows in set (0.00 sec)`

Остановите процесс, если такой есть: > `mysql> kill номер процесса;Query OK, 0 rows affected (0.01 sec)`

После того, как остановили процесс – отзовите права пользователя на базу: > `mysql> revoke all privileges on usertestdb.* from 'usertest'@'localhost';Query OK, 0 rows affected (0.00 sec)`

И после этого попробуйте удалить пользователя: > `mysql> drop user 'usertest'@'localhost';Query OK, 0 rows affected (0.00 sec)`

-- Источник - https://rtfm.co.ua/mysql-error-1396-hy000-operation-drop-user-failed-for-username/