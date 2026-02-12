---
id: 3352
title: 'Проблемы обновления RocketChat c 6.13.0 на 7.5.0 через SNAP'
date: '2025-04-28T15:46:12+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3352'
permalink: /2025/04/28/problemy-obnovleniya-rocketchat-c-6-13-0-na-7-5-0-cherez-snap/
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
views:
    - '137'
wp_statistics_words_count:
    - '197'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по DevOps'
tags:
    - linux
    - rocketchat
format: false
---

При обновлении через snap с 6 на 7 версию ловил ошибки по работе с базой данных. Пример ошибки:

> /snap/rocketchat-server/1634/helpers/mongo.sh: line 50: ((: {"t":{"$date":"2025-04-28T11:26:41.300Z"},"s":"I", "c":"NETWORK", "id":5693100, "ctx":"js","msg":"Asio socket.set\_option failed with std::system\_error","attr":{"note":"connect (sync) TCP fast open","option":{"level":6,"name":30,"data":"01 00 00 00"},"error":{"what":"set\_option: Protocol not available","message":"Protocol not available","category":"asio.system","value":92}}}  
> 1 : syntax error: operand expected (error token is "{"t":{"$date":"2025-04-28T11:26:41.300Z"},"s":"I", "c":"NETWORK", "id":5693100, "ctx":"js","msg":"Asio socket.set\_option failed with std::system\_error","attr":{"note":"connect (sync) TCP fast open","option":{"level":6,"name":30,"data":"01 00 00 00"},"error":{"what":"set\_option: Protocol not available","message":"Protocol not available","category":"asio.system","value":92}}}

В интернетах ничего внятного не нашел, хотя люди сталкивались с подобным именно при переходе с 6 на 7. Может быть плохо искал решение, но всё же разрулил ситуацию с обновлением.

Перед обновлением лучше все [забэкапить данные](/2023/12/06/kak-sdelat-rezervnoe-kopirovanie-dannyx-rocketchat-server/) и на всякий случай всю папку RocketChat'а тоже скопировать.  
Обновить удалось следующим образом:  
1\. Останавливаем RocketChat

> snap stop rocketchat-server

2\. Бэкапим папку

> cp -r /var/snap/rocketchat-server/common /path/to/backup/rocketchat-backup

3\. Бэкапим данные

> snap run rocketchat-server.backupdb

4\. Переносим забэкапленные данные в другое своем место через cp.

Далее

5\. Удаляем RocketChat, но конфиги сохраняем, поэтому remove

> snap remove rocketchat-server

6\. Ставим последнюю версию

> snap install rocketchat-server --channel=latest/stable

7\. Далее копируем забэкапленные данные в папку для бэкапов RocketChat'a, иначе ошибка будет появляться.

> cp -r /path/to/backup/rocketchat-backup /var/snap/rocketchat-server/common

  
8\. Восстанавливаем данные

> snap run rocketchat-server.restoredb /var/snap/rocketchat-server/common/rocketchat\_backup.tgz

9\. В процессе предложит удалить старую базу. Соглашаемся и ждем завершения.  
10\. Запускаем RocketChat и ждем пока все нужные данные подтянутся, посматривая в журнал с логами.