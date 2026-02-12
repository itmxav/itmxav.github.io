---
id: 3323
title: 'Как перенести (backup and restore) Pritunl?'
date: '2025-04-02T14:48:23+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3323'
permalink: /2025/04/02/kak-perenesti-backup-and-restore-pritunl/
views:
    - '82'
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
    - '93'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по DevOps'
tags:
    - linux
    - mongodb
format: false
---

Здесь нет информации по настройке VPN для обхода блокировок 😊  
Иногда требуется сделать резервную копию Pritunl и быстро восстановить/поднять в новом месте. Лучше чтобы версия ПО была одинакова на всех серверах, чтобы уменьшить возникновение ошибок.

***Бэкап:***  
1\. Бэкапим нужную базу через mongodump

```
[code lang="plain"]mongodump --db=pritunl[/code]
```

2\. Архивируем

```
[code lang="plain"]tar cf pritunldb.tar dump[/code]
```

3\. Перекидываем на нужный сервер любым удобным способом

***Восстановление:***  
1\. Заходим в mongosh и смотрим базу, если она есть

```
[code lang="plain"]mongosh
show dbs[/code]
```

2\. Если есть, то удаляем

```
[code lang="plain"]use pritunl
db.dropDatabase()[/code]
```

3\. Распаковываем архив

```
[code lang="plain"]tar xf pritunldb.tar[/code]
```

4\. Восстанавливаем забэкапенную базу из папки

```
[code lang="plain"]mongorestore --db=pritunl pritunl[/code]
```

5\. Заходим в WEB-интерфейс, правим IP-адреса, если нужно, и проверяем работу.