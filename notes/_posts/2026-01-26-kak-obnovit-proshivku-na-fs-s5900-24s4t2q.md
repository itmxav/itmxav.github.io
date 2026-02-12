---
id: 3585
title: 'Как обновить прошивку на FS S5900-24S4T2Q?'
date: '2026-01-26T17:26:26+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3585'
permalink: /2026/01/26/kak-obnovit-proshivku-na-fs-s5900-24s4t2q/
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
    - '37'
wp_statistics_words_count:
    - '119'
image: /wp-content/uploads/2026/01/fss5900new2.jpg
categories:
    - 'Работа с графикой'
tags:
    - fs
    - сети
format: false
---

Что-то какие баги на багах попадаются в коммутаторах в последнее время. Счетчики SNMP криво работали на S5900-24S4T2Q. Потребовалось обновить ПО.  
Добываем прошивку [здесь](https://www.fs.com/eu-en/products_support.html?isPica=false&categories_id=3079&third_categories_id=3256&products_model=S5900-24S4T2Q&style_id=9&files_id=d1356)

Закидываем самым распространенным способом: сначала на TFTP-сервер свой, а потом на оттуда на коммутатор.  
Посмотреть что есть на flash (конфиг естественно заранее сохранен на всякий случай)

```
[code lang="plain"]enable
# dir[/code]
```

Смотрим текущую версию

```
[code lang="plain"]# show version[/code]
```

Скачиваем с TFTP-сервера:

```
[code lang="plain"]# copy tftp: flash:[/code]
```

Попутно указали, что именно и откуда именно качаем.

Закинем на TFTP-сервер старую прошивку, мало ли:

```
[code lang="plain"]copy flash: tftp:[/code]
```

Попутно указали, что именно и откуда именно качаем.

Теперь переходим в конфиг, указываем новое ПО и потом старое на всякий случай

```
[code lang="plain"]# config
sw_config# boot system flash FSOS_S5900-24S4TSQ_2.2.0D_79390_04055_2020.bin
sw_config# boot system flash FSOS-S5900V2.2.0.bin[/code]
```

Сохраняем, а то изменения слетят и перезагружаемся

```
[code lang="plain"]# write
# reboot[/code]
```

Проверяем работу и версию ПО после перезагрузки.