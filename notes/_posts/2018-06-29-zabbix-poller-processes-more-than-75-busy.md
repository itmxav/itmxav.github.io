---
id: 181
title: 'Zabbix poller processes more than 75% busy'
date: '2018-06-29T16:15:59+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=181'
permalink: /2018/06/29/zabbix-poller-processes-more-than-75-busy/
views:
    - '324'
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
image: /wp-content/uploads/2017/09/1000px-Server-monitoring.svg_.png
categories:
    - 'Записи про мониторинг'
tags:
    - zabbix
format: false
---

При большом количестве узлов с snmp v3 может возникать данная ошибка. Возможное решение: Настройка-&gt;узлы-&gt;нужный узел-&gt;ставим галочку "Использовать массовые запросы" Данная опция позволяет задействовать обработку массовых запросов. Дополнительная информация: [Обработка\_массовых\_snmp\_запросов](https://www.zabbix.com/documentation/2.4/ru/manual/config/items/itemtypes/snmp#обработка_массовых_snmp_запросов)