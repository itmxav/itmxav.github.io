---
id: 169
title: 'Конфигурационный файл подключения к базе данных в некоторых CMS'
date: '2018-06-22T13:49:11+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=169'
permalink: /2018/06/22/konfiguracionnyj-fajl-podklyucheniya-k-baze-dannyx-v-nekotoryx-cms/
views:
    - '246'
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
image: /wp-content/uploads/2018/06/cms.png
categories:
    - 'Записи по CMS'
tags:
    - cms
format: false
---

В <ins datetime="2018-06-22T10:21:39+00:00">Joomla</ins> есть configuration.php, в:

> `var $host = 'сервер';var $user = 'имя_пользователя';var $db = 'имя_базы_данных';var $password = 'пароль';`

В <ins datetime="2018-06-22T10:21:39+00:00">Drupal</ins> в папке /site/default/ есть settings.php и там есть строчка $db\_url = 'mysql://username:password@mysqlhost/databasename'; Там: > `username - имя пользователя;password - пароль;mysqlhost - сервер базы данных;databasename - имя базы данных.`

В <ins datetime="2018-06-22T10:21:39+00:00">MODx</ins> в /manager/includes/config.inc.php: > `$database_server = 'сервер';$database_user = 'имя_пользователя';$database_password = 'пароль';$dbase = 'имя_базы_данных’;`

В <ins datetime="2018-06-22T10:21:39+00:00">Bitrix</ins> в /bitrix/php\_interface/dbconn.php: > `$DBHost = "сервер";$DBLogin = "имя_пользователя";$DBPassword = "пароль";$DBName = "имя_базы_данных";`

В <ins datetime="2018-06-22T10:21:39+00:00">WordPress</ins> есть wp-config.php, в котором: > `define('DB_NAME', 'имя_базы_данных');define('DB_USER', 'имя_пользователя');define('DB_HOST', 'сервер');define('DB_PASSWORD', 'пароль');`

В phpBB в docs/config.php: $dbhost = 'адрес\_сервера'; $dbname = 'имя\_базы\_данных'; $dbuser = 'имя\_пользователя'; $dbpasswd = 'пароль'; В <ins datetime="2018-06-22T10:21:39+00:00">DLE</ins> в папке /engine/data/ есть dbconfig.php, в котором: > `define ("DBHOST", "сервер");define ("DBNAME", "имя_базы_данных");define ("DBUSER", "имя_пользователя");define ("DBPASS", "пароль");`

В <ins datetime="2018-06-22T10:21:39+00:00">Shop-script</ins> подключение настраивается в файле /cfg/connect.inc.php > `define('DB_HOST', 'сервер');define('DB_USER', 'имя_пользователя');define('DB_PASS', 'пароль');define('DB_NAME', 'имя_базы_данных');`

В <ins datetime="2018-06-22T10:21:39+00:00">ShopCMS</ins> БД подключается в /core/config/connect.inc.php > `define('DB_HOST', 'сервер');define('DB_USER', 'имя_пользователя');define('DB_PASS', 'пароль');define('DB_NAME', 'имя_базы_данных');`

В <ins datetime="2018-06-22T10:21:39+00:00">WebAsyst</ins> есть файл /dblist/логин.xml в котором: > `SQLSERVER="сервер"DB_NAME="имя_базы_данных"DB_PASSWORD="пароль"DB_USER="имя_пользователя"`

и в файле кеша /temp/scdb/.settings.логин дублируются эти же параметры: > `"DB_USER" "имя_пользователя""DB_PASS" "пароль""DB_NAME" "имя_базы_данных""DB_HOST" "сервер"`

В <ins datetime="2018-06-22T10:21:39+00:00">PrestaShop</ins> подключение настраивается в /config/settings.inc.php > `define('_DB_NAME_', 'имя_базы_данных');define('_DB_SERVER_', 'сервер');define('_DB_USER_', 'имя_пользователя');define('_DB_PASSWD_', 'пароль');`

В <ins datetime="2018-06-22T10:21:39+00:00">Amiro.CMS</ins> нв docs/\_local/config.ini.php: > `DB_Host = "адрес_сервера"DB_Database = "имя_базы_данных"DB_User = "имя_пользователя"DB_Password = "пароль"`

В <ins datetime="2018-06-22T10:21:39+00:00">PHPShop</ins> в phpshop/inc/config.ini: > `host = "сервер";user_db = "имя_пользователя";pass_db = "пароль";dbase = "имя_базы_данных";`

В <ins datetime="2018-06-22T10:21:39+00:00">HostCMS</ins> в modules/core/config/database.php : > `'driver' => 'mysql','host' => 'localhost','username' => 'srv83user','password' => 'megapassword','database' => 'hostcms'`

В <ins datetime="2018-06-22T10:21:39+00:00">UMI</ins> в секции \[connections\] файла docs/config.ini: > `core.host = "адрес_сервера"core.login = "имя_пользователя"core.password = "пароль"core.dbname = "имя_базы_данных"`

В <ins datetime="2018-06-22T10:21:39+00:00">NetCat</ins> в docs/vars.inc.php: > `$MYSQL_HOST = "адрес_сервера";$MYSQL_USER = "имя_пользователя";$MYSQL_PASSWORD = "пароль";$MYSQL_DB_NAME = "имя_базы_данных";`