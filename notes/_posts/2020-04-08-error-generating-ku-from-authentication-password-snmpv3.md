---
id: 725
title: 'Ошибка Error generating Ku from authentication pass phrase. SNMPv3'
date: '2020-04-08T16:59:06+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=725'
permalink: /2020/04/08/error-generating-ku-from-authentication-password-snmpv3/
views:
    - '904'
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
wp_statistics_words_count:
    - '41'
image: /wp-content/uploads/2017/09/1000px-Server-monitoring.svg_.png
categories:
    - 'Записи про мониторинг'
tags:
    - snmpv3
    - сети
format: false
---

При конфигурировании работы через SNMPv3 (например, на Cisco) может возникнуть ошибка:

> **Error generating Ku from authentication pass phrase. Give Valid Authentication password.**

Это может быть связано с тем, что пароль, который используется для работы по SNMPv3, короткий. Попробуйте пароль длинной в 12 символов.