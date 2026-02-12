---
id: 1403
title: 'Как конвертировать IMG в VDI с помощью VirtualBox на Linux?'
date: '2022-08-23T10:51:41+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=1403'
permalink: /2022/08/23/kak-konvertirovat-img-v-vdi-s-pomoshhyu-virtualbox-na-linux/
views:
    - '447'
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
    - Виртуализация
    - 'Записи по Linux'
tags:
    - linux
    - virtualbox
format: false
---

Для того чтобы преобразовать файл IMG в VDI нужно с помощью VirtualBox нужно:

1. Чтобы был установлен VirtualBox
2. Запустить VBoxManage convertdd:  
    > `$ VBoxManage convertdd input.img output.vdi`

Вывод будет похож на:

> `Converting from raw image file="input.img" to file="output.vdi"…<br></br>Creating dynamic image with size 160046252032 bytes (152632MB)…`

3. Дождаться завершения конвертиции.

Конвертирование может занять продолжительное время.