---
id: 31
title: 'UFW. Ubuntu. Открытие или закрытие портов для хоста или подсети.'
date: '2017-02-26T13:30:46+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=31'
permalink: /2017/02/26/ufw-ubuntu-otkrytie-ili-zakrytie-portov-dlya-xosta-ili-podseti/
views:
    - '262'
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
image: /wp-content/uploads/2017/02/firewal.png
categories:
    - 'Debian, Ubuntu etc.'
tags:
    - firewall
    - linux
format: false
---

"Ядро линукс включает подсистему Netfilter (сетевой фильтр), который используется для манипулирования или решения судьбы сетевого трафика передаваемого в или через ваш сервер. Все современные решения линукс по сетевой защите используют эту систему пакетной фильтрации....Система пакетной фильтрации на уровне ядра была бы малоиспользуема администраторами без пользовательского интерфейса для ее управления. Для этого предназначен iptables...iptables - это все, что вам нужно для управления вашей сетевой защитой, если вы хорошо с ним знакомы, однако множество внешних интерфейсов доступны для упрощения этой задачи...ufw - простой Firewall.Он разработан для легкой настройки iptables и предоставляет дружественный способ создания сетевой защиты для IPv4 и IPv6...." <a>источник</a>Включить/отключить ufw:

> `sudo ufw enable/disable`

Открыть/закрыть порт 22 всем: > `sudo ufw allow/deny 22`

Удалить правило: > `sudo ufw delete deny 22`

Разрешить доступ к 22 порту с определенного хоста: > `sudo ufw allow proto tcp from 10.0.0.1 to any port 22`

Разрешить доступ к 22 порту с определенной подсети: > `sudo ufw allow proto tcp from 10.0.1.0/24 to any port 22`

Посмотреть статус защиты: > `sudo ufw status`

Полное отображение информации: > `sudo ufw status verbose`

Включить/отключить журналирование: > `sudo ufw logging on/off`