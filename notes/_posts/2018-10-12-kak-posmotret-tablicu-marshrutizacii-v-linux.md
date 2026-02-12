---
id: 351
title: 'Как посмотреть таблицу маршрутизации в Linux'
date: '2018-10-12T17:32:22+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=351'
permalink: /2018/10/12/kak-posmotret-tablicu-marshrutizacii-v-linux/
views:
    - '437'
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
    - сети
format: false
---

Посмотреть таблицу маршрутизации можно использовав команду:

> `$ route`

Более подробно: > `$ routel`

Вариант удобного просмотра: > `$ ip route`

Доп. пояснения вывода ip route: *default* - в данной строке означает вариант по умолчанию. Здесь должен быть ip адрес цели или маска подсети; *via 192.168.1.1* - указывает через какой шлюз мы можем добраться до этой цели, у нас это 192.168.1.1; *dev enp2s0* - сетевой интерфейс, с помощью которого будет доступен этот шлюз; *proto static* - означает, что маршрут был установлен администратором, значение kernel значит что он был установлен ядром; *metric* - это приоритет маршрута, чем меньше значение - тем выше приоритет. -- Источник - [losst.ru](https://losst.ru/marshrutizatsiya-v-linux)