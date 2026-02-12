---
id: 334
title: 'Не работает service iptables save в CentOS 7'
date: '2018-09-21T14:36:59+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=334'
permalink: /2018/09/21/ne-rabotaet-service-iptables-save-v-centos-7/
views:
    - '960'
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
    - 'RedHat, CentOS etc.'
    - 'Записи по Linux'
tags:
    - linux
format: false
---

Иногда при выполнении команды `service iptables save` может возникать такое сообщение: `The service command supports only basic LSB actions (start, stop, restart, try-restart, reload, force-reload, status). For other actions, please try to use systemctl.`Для решения этой проблемы надо установить iptables-services:

> `yum install iptables-services`

-- Источник - [ezyforanykey.blogspot.com](https://ezyforanykey.blogspot.com/2017/01/cenos-7-service-iptables-save.html)