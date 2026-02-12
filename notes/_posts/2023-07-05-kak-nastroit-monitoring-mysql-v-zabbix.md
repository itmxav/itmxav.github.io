---
id: 2263
title: 'Как настроить мониторинг MySQL в Zabbix?'
date: '2023-07-05T14:35:45+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=2263'
permalink: /2023/07/05/kak-nastroit-monitoring-mysql-v-zabbix/
views:
    - '230'
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
    - 'Записи про мониторинг'
tags:
    - zabbix
    - мониторинг
format: false
---

*В примере используется Zabbix 5.0*

1\. Создаем пользователя с паролем разрешения:

\[code lang="bash"\]mysql -uroot -p &gt; CREATE USER 'zbx\_monitor'@'%' IDENTIFIED BY 'ndR44242RRgLed'; &gt; GRANT USAGE,REPLICATION CLIENT,PROCESS,SHOW DATABASES,SHOW VIEW ON \*.\* TO 'zbx\_monitor'@'%'; &gt; quit\[/code\] 2\. Необходимо добавиит новые параметры в агенте. Создаем конфигурационный файл /etc/zabbix/zabbix\_agentd.d/template\_db\_mysql.conf с содержанием:

\[code lang="plain"\]UserParameter=mysql.ping\[\*\], mysqladmin -h"$1" -P"$2" ping UserParameter=mysql.get\_status\_variables\[\*\], mysql -h"$1" -P"$2" -sNX -e "show global status" UserParameter=mysql.version\[\*\], mysqladmin -s -h"$1" -P"$2" version UserParameter=mysql.db.discovery\[\*\], mysql -h"$1" -P"$2" -sN -e "show databases" UserParameter=mysql.dbsize\[\*\], mysql -h"$1" -P"$2" -sN -e "SELECT COALESCE(SUM(DATA\_LENGTH + INDEX\_LENGTH),0) FROM INFORMATION\_SCHEMA.TABLES WHERE TABLE\_SCHEMA='$3'" UserParameter=mysql.replication.discovery\[\*\], mysql -h"$1" -P"$2" -sNX -e "show slave status" UserParameter=mysql.slave\_status\[\*\], mysql -h"$1" -P"$2" -sNX -e "show slave status" \[/code\] Чтобы избежать несостыковок по домашней папке, где должен находиться .my.cnf, указываем принудительно /var/lib/zabbix.

3\. Создадим папку, если её нет, и файл .my.cnf

\[code lang="bash"\]mkdir /var/lib/zabbix nano /var/lib/zabbix/.my.cnf\[/code\] Содержание .my.cnf:

\[code lang="plain"\]\[client\] user='zbx\_monitor' password='Passsw0rd'\[/code\] 4\. Назначим права:  
\[code lang="bash"\]chown -R zabbix. /var/lib/zabbix chmod 400 /var/lib/zabbix/.my.cnf\[/code\]

5\. Перезапустим Zabbix Agent:   
\[code lang="bash"\]sudo systemctl restart zabbix-agent\[/code\]

6\. В Zabbix переходим в настройки конкретного узла -&gt; Шаблоны. Для быстрого поиска вбиваем Mysql в строке "Присоединение новых шаблонов" и находим шаблон "Template DB MySQL by Zabbix agent". Выбираем и обновляем настройки.

В разделе Мониторинг -&gt; Последние данные можно посмотреть полученную информацию.