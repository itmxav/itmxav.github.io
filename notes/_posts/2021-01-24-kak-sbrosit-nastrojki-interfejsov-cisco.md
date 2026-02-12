---
id: 798
title: 'Как сбросить настройки интерфейсов Cisco?'
date: '2021-01-24T23:01:15+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=798'
permalink: /2021/01/24/kak-sbrosit-nastrojki-interfejsov-cisco/
views:
    - '335'
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
    - 'Записи по Cisco'
tags:
    - cisco
format: false
---

Для того чтобы сбросить интерфейсы на Cisco в default надо выполнить команду в режиме (config):

> `default interface range GigabitEthernet1/0/1-48`

Названия интерфейсов могут быть другие.