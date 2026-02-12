---
id: 672
title: 'Проблема с SNMPv3 и engineID'
date: '2020-03-20T14:54:09+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=672'
permalink: /2020/03/20/problema-snmpv3-i-engineid/
views:
    - '222'
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
    - 'Записи по сетям'
tags:
    - snmpv3
    - сети
format: false
---

Когда много оборудования одинаковой модели и версии ОС находится под мониторингом, то может возникнуть ситуация с некорректным сбором данных по SNMPv3. Необходимо посмотреть engineID на оборудовании. Если на двух хостах одинаковый engineID, то в ручную подкорректировать его. Но для начала необходимо удалить пользователей, связанных с SNMPv3,т.к. идет привязка к engineID. Т.е.: - удаляем пользователей для работы по SNMPv3; - меняем engineID; - создаем заново пользователей, чтобы привязать к новому engineID; - проверяем корректность работы через snmpget или систему мониторинга сети. -- Доп.информация: [Системы мониторинга, SNMPv3 и engineID ](https://vladimir-stupin.blogspot.com/2016/09/snmpv3-engineid.html)