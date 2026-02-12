---
id: 2868
title: 'Как проверить fstab в Linux?'
date: '2024-05-06T17:08:48+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2868'
permalink: /2024/05/06/kak-proverit-fstab-v-linux/
views:
    - '227'
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
    - linux
format: false
---

Иногда требуется проверить файл /etc/fstab.  
Перед внесением изменений лучше забэкапить fstab.  
\[code lang="plain"\]cp -p /etc/fstab /etc/fstab.bak\[/code\]  
Можно рассмотреть вариант с ключом -a. Т.е. смонтируются все всё, что указано в fstab.  
\[code lang="plain"\]mount -a\[/code\]  
Как вариант, можно использоваться mount с фейковым подключением, т.е. проверка без внесения изменений. Главное не использовать ключ -f во FreeBDS. Там значение ключа другое - force.  
\[code lang="plain"\]mount -fav\[/code\]  
Либо через findmnt можно сделать проверку.