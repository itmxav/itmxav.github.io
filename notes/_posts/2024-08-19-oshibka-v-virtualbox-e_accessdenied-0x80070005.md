---
id: 2981
title: 'Ошибка в VirtualBox E_ACCESSDENIED (0x80070005)'
date: '2024-08-19T16:54:05+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2981'
permalink: /2024/08/19/oshibka-v-virtualbox-e_accessdenied-0x80070005/
views:
    - '204'
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
    - 'Записи по Linux'
tags:
    - virtualbox
format: false
---

После перезагрузки ОС на Linux Ubuntu перестали запускаться виртуальные машины на VirtualBox.

В логах появляется ошибка

\[code lang="plain"\]ERROR \[COM\]: aRC=E\_ACCESSDENIED (0x80070005) aIID={...} aComponent={DisplayWrap} aText={The console is not powered up (setVideoModeHint)}, preserve=false aResultDetail=0\[/code\]

Пытался решить разными способами эту проблему. Кто-то писал в интернете, что надо переустановить ​Extension Pack, кто-то отмечал, что надо в настройках ВМ USB 1 поставить. После разных попыток и анализа того, что происходит помогла только переустановка VB на последнюю версию.

1\. Папку с ВМ переименовать. Например добавить .bak в хвост, чтобы случайно не удалить её вместе с удалением VB.  
2\. Удаляется VB и VB-dkms через remove на Ubuntu, не через purge  
\[code lang="plain"\]sudo apt remove virtualbox sudo apt remove virtualbox-dkms\[/code\]  
3\. Далее скачивается последняя версия VB и Extension Pack [на оф.сайте](https://www.virtualbox.org/wiki/Downloads).  
4\. Устанавливается VB

```
[code lang="plain"]sudo dpkg -i virtualbox-7.0_7.0.20-163906~Ubuntu~amd64.deb[/code]
```

  
5\. Устанавливаем Extension Pack. Просто 2 раза кликнуть по файлу ЛКМ.  
6\. Возвращаем имя папки с виртуальными машинами и пробуем запустить всё.