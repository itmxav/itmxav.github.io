---
id: 627
title: 'Задать статический постоянный маршрут Debian 9'
date: '2019-05-23T14:48:43+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=627'
permalink: /2019/05/23/zadat-staticheskij-postoyannyj-marshrut-debian-9/
views:
    - '702'
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
    - 'Debian, Ubuntu etc.'
tags:
    - linux
    - сети
format: false
---

В /etc/network/interfaces вместо (учитывая свою сеть):

> `post-up route add -net 192.1.1.0 netmask 255.255.254.0 gw 192.1.1.10pre-down route del -net 192.1.1.0.0 netmask 255.255.254.0 gw 192.1.1.10`

Надо прописать > `post-up /sbin/ip r add 192.1.1.0/23 via 192.1.1.10pre-down /sbin/ip r del 192.1.1.0/23 via 192.1.1.10`