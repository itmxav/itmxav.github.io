---
id: 3576
title: 'Как обновить ПО на отдельном коммутаторе QTECH?'
date: '2026-01-23T14:05:32+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3576'
permalink: /2026/01/23/kak-obnovit-po-na-otdelnom-kommutatore-qtech/
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
    - '19'
image: /wp-content/uploads/2026/01/POqtechnew1.jpg
categories:
    - 'Записи по QTECH'
tags:
    - qtech
    - сети
format: false
---

Нарвался на глюк ПО. На некоторых портах VLAN не менялся никак. Пришлось обновляться. Модель QSW-3750-52T-AC-R.  
Само ПО для этой модели [здесь](https://ftp.qtech.ru/Switch/Access/QSW-3750-R/Firmware/QSW-3750-52T-AC-R/).  
Если другая модель, то смотрите [здесь](https://www.qtech.ru/support/download/).  
L3-интерфейс поднят, поэтому повторятся не будут. Если что, то смотрите [базовую настройку](/2026/01/19/bazovaya-nastrojka-kommutatora-qtech-qsw-3750-52t-ac-r/).  
Для начала надо узнать текущую версию ПО (может уже последняя стоит):

```
[code lang="plain"]# show version[/code]
```

Файлы на flash можно вот так посмотреть

```
[code lang="plain"]# dir[/code]
```

Сначала на свой TFTP-сервер закинул образ и далее с этого сервера качал на коммутатор:

```
[code lang="plain"]# copy tftp://IP_TFTP/QSW-3750-X-AC-R_8.2.1.238_nos.img 8.2.1.238_nos.img[/code]
```

Можно и из других мест загрузить

```
[code lang="plain"]sftp://user:password@ip|host-name/remote-filename
ftp://user:password@ip|host-name/remote-filename
local-filename[/code]
```

Учитывайте, что более 2 образов не влезет на flash.  
Далее указываем, что грузить в первую очередь

```
[code lang="plain"]# boot img 8.2.1.238_nos.img primary [/code]
```

Указываем, что грузить, если первое ПО не запустилось. Например, старый образ загружать

```
[code lang="plain"]# boot img nos.img backup [/code]
```

Перезагружаемся

```
[code lang="plain"]# reload[/code]
```

Проверяем работу и версию ПО после перезагрузки.