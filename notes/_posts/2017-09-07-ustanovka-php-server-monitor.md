---
id: 108
title: 'Установка PHP Server Monitor'
date: '2017-09-07T19:06:01+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=108'
permalink: /2017/09/07/ustanovka-php-server-monitor/
views:
    - '261'
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
image: /wp-content/uploads/2017/09/1000px-Server-monitoring.svg_.png
categories:
    - 'Записи про мониторинг'
tags:
    - web
    - мониторинг
format: false
---

Исходим из того, что уже стоит LAMP. Переходим в default папку,качаем PHPServerMonitor, распаковываем, меняем владельца и группу:

> `$cd /var/www/html$wget https://sourceforge.net/projects/phpservermon/files/phpservermon/phpservermon-3.2.0.zip$unzip PHP Server Monitor$sudo chown www-data:www-data cd /var/www/html/phpservermon`

Создаем базу и пользователя для монитора: > `$mysql -uroot -pmysql> create database phpmonitordb;mysql> grant all on phpmonitordb.* to 'userphp'@'localhost' identified by '12345678';mysql> flush privileges;`

Переходим по http://ip-address-server/install.php и вбиваем все данные. После загоняем полученный ответ в config.php > `$sudo touch /var/www/html/phpservermon/config.php$sudo chown www-data:www-data cd /var/www/html/phpservermon/config.php$sudo nano/var/www/html/phpservermon/config.php define('PSM_DB_HOST', 'localhost');define('PSM_DB_PORT', '3306');define('PSM_DB_NAME', 'phpmonitordb');define('PSM_DB_USER', 'userphp');define('PSM_DB_PASS', '12345678');define('PSM_DB_PREFIX', 'psm_');define('PSM_BASE_URL', 'http://ip-address-server');`

Нажимаем дальше на странице и создаем новый аккаунт. Все.