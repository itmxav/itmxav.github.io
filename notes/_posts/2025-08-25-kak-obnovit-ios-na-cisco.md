---
id: 3369
title: 'Как обновить IOS на Cisco?'
date: '2025-08-25T17:20:41+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3369'
permalink: /2025/08/25/kak-obnovit-ios-na-cisco/
views:
    - '13'
wp_statistics_words_count:
    - '86'
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
    - 'Записи по Cisco'
tags:
    - cisco
    - сети
format: false
---

Иногда бывает, что необходимо обновить IOS Cisco вручную. Для этого:  
1\. Подключаем флешку с IOS. Если флешка не видится, но выдает ошибки, то лучше её отформатировать прямо на Cisco и потом закинуть на неё IOS:

```
[code lang="plain"]format usbflash0:[/code]
```

2\. Далее смотрим, что IOS есть и закидываем его на flash Cisco:

```
[code lang="plain"]dir usbflash0:
copy usbflash0:cXXXX-adventerprisek9-mz.124-12.bin flash:[/code]
```

3\. Далее в конфиге указывает что именно надо грузить, сохраняем и перезагружаемся

```
[code lang="plain"]conf t
boot system flash:cXXXX-adventerprisek9-mz.124-12.bin
!если есть выше другие загрузки, то удаляем или ставим ниже через команды no boot/boot
write memory
reload
[/code]
```

Если всё нормально, то IOS должен обновиться.