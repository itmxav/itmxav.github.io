---
id: 655
title: 'SNMP error: (noSuchName) There is no such variable name in this MIB. Zabbix'
date: '2019-10-21T19:01:29+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=655'
permalink: /2019/10/21/snmp-error-nosuchname-there-is-no-such-variable-name-in-this-mib-zabbix/
views:
    - '1167'
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
    - мониторинг
format: false
---

Ошибка в Zabbix:

> SNMP error: (noSuchName) There is no such variable name in this MIB. Zabbix

Zabbix надо указывать конкретный (конечный) OID откуда брать значения. Проверьте OID. Для проверки OID используйте snmpget (берет значения из конечного места), а не snmpwalk (заходит в ветки). Иногда не хватает .0 в OID.