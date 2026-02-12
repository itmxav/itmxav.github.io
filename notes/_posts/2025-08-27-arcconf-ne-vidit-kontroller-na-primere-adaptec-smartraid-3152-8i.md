---
id: 3378
title: 'Arcconf не видит контроллер на примере Adaptec SmartRAID 3152-8i'
date: '2025-08-27T15:42:05+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3378'
permalink: /2025/08/27/arcconf-ne-vidit-kontroller-na-primere-adaptec-smartraid-3152-8i/
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
    - '24'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Linux'
tags:
    - linux
format: false
---

После очередного обновления ОС arcconf перестал видеть контроллер:

```
[code lang="plain"]

# arcconf LIST
Controllers found: 0

Command completed successfully.

[/code]
```

Хотя всё видно и загружено через

```
[code lang="plain"]

# cat /proc/scsi/scsi
# lsscsi -v
# dmesg | grep -i smartpqi

[/code]
```

С большой вероятностью надо более новую версию скачать с download.adaptec.com, закинуть в правильное место и сделать символьную ссылку на бинарник.  
1\. Создаем папку

```
[code lang="plain"]# mkdir -p /opt/arcconf[/code]
```

  
2\. Копируем бинарник и даем права

```
[code lang="plain"]# cp /путь/к/бинарнику/arcconf/linux_x64/arcconf /opt/arcconf/
# chmod +x /opt/arcconf/arcconf
# chmod -R 755 /opt/arcconf
# ln -sf /opt/arcconf/arcconf /usr/local/bin/arcconf[/code]
```

Проверить работу можно через

```
[code lang="plain"]# which arcconf
# arcconf getconfig 1[/code]
```