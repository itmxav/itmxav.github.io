---
id: 323
title: 'Centos 7 не сохраняет правила iptables'
date: '2018-09-20T17:07:17+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=323'
permalink: /2018/09/20/centos-7-ne-soxranyaet-pravila-iptables/
views:
    - '502'
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
    - 'RedHat, CentOS etc.'
    - 'Записи по Linux'
tags:
    - firewall
    - linux
format: false
---

При перезагрузки сервера правила, которые были добавлены до перезагрузки, не сохраняются. Возможное решение: 1. Отключаем firewald для того чтобы работали только правила iptables:

> `systemctl disable firewalldsystemctl stop firewalld`

2. Просмотр текущих правил: > `iptables -nL`

3. Добавляем нужные нам правила и сохраняем их: > `service iptables save`