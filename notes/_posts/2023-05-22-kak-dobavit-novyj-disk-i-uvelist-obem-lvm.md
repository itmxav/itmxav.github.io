---
id: 2231
title: 'Как добавить новый диск и увеличить объем LVM?'
date: '2023-05-22T16:05:24+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=2231'
permalink: /2023/05/22/kak-dobavit-novyj-disk-i-uvelist-obem-lvm/
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
    - '151'
wp_statistics_words_count:
    - '114'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Linux'
tags:
    - linux
    - lvm
format: false
---

1\. Смотрим какие диски добавлены в LVM (физические тома):  
\[code lang="plain"\]pvs\[/code\]Детальней:   
\[code lang="plain"\]pvdisplay\[/code\]

Посмотреть информацию о группе томов:  
\[code lang="plain"\]vgs\[/code\]Детальней:  
\[code lang="plain"\]vgdisplay\[/code\]

Посмотреть информацию о логическом томе:  
\[code lang="plain"\]lvs\[/code\]Детальней:  
\[code lang="plain"\]lvdisplay\[/code\]

В данном случае группа томов называется /dev/mapper/gbackup-lbackup

2\. Находим свой диск  
\[code lang="plain"\]lsblk /dev/sd\*\[/code\] или через lvmdiskscan - сканирует все видимые устройства для LVM.  
В нашем случае диск sdd.

3\. Создаем физический том:  
\[code lang="plain"\]pvcreate /dev/sdd\[/code\]

Ответ - "Physical volume "/dev/sdd" successfully created"

Для проверки посмотрим вывод \[code lang="plain"\]lvmdiskscan –l\[/code\]

4\. Добавляем физический том в нужную группу:  
\[code lang="plain"\]vgextend gbackup /dev/sdd\[/code\]

Ответ - "Volume group "gbackup" successfully extended"

Смотрим, что получилось:  
\[code lang="plain"\]lvdisplay /dev/mapper/gbackup-lbackup\[/code\]

5\. Отмечаем на сколько хотим увеличить объем LVM:  
\[code lang="plain"\]lvextend -L +9800G /dev/mapper/gbackup-lbackup\[/code\]или всё  
\[code lang="plain"\]lvextend --extents +100%FREE /dev/mapper/gbackup-lbackup\[/code\]

6\. Обновляем все это дело:  
\[code lang="plain"\]resize2fs -p /dev/mapper/gbackup-lbackup\[/code\]

7\. Смотрим,что место увеличилось:   
\[code lang="plain"\]df -h\[/code\]