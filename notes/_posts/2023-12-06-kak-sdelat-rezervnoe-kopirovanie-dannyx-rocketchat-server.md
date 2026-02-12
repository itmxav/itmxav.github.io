---
id: 2445
title: 'Как сделать резервное копирование данных rocketchat server?'
date: '2023-12-06T16:47:00+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2445'
permalink: /2023/12/06/kak-sdelat-rezervnoe-kopirovanie-dannyx-rocketchat-server/
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
    - '121'
wp_statistics_words_count:
    - '41'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по DevOps'
tags:
    - linux
    - rocketchat
format: false
---

1\. Останавливаем

```
[code lang="plain"]sudo service snap.rocketchat-server.rocketchat-server stop[/code]
```

или

```
[code lang="plain"]sudo systemctl stop snap.rocketchat-server.rocketchat-server[/code]
```

2\. Создание резервной копии данных

```
[code lang="plain"]sudo snap run rocketchat-server.backupdb[/code]
```

3\. Восстановление данных

```
[code lang="plain"]sudo snap run rocketchat-server.restoredb /var/snap/rocketchat-server/common/rocketchat_backup.tgz[/code]
```

4\. Запускаем сервис

```
[code lang="plain"]sudo service snap.rocketchat-server.rocketchat-server start[/code]
```

или

```
[code lang="plain"]sudo systemctl restart snap.rocketchat-server.rocketchat-server[/code]
```

P.s. [База данных может быть скопирована отдельно](/2023/12/06/kak-sdelat-rezervnoe-kopirovanie-dannyx-rocketchat-server/).