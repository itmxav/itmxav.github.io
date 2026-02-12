---
id: 790
title: 'Как добавить подключение  L2TP/IPSec в Linux Ubuntu ?'
date: '2021-01-20T22:00:34+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=790'
permalink: /2021/01/20/kak-dobavit-podklyuchenie-l2tpipsec-v-linux-ubuntu/
views:
    - '126'
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

Чтобы добавить L2TP/IPSec подключение необходимо добавить репозиторий и установить:

> `sudo add-apt-repository ppa:nm-l2tp/network-manager-l2tpsudo apt updatesudo apt install network-manager-l2tp network-manager-l2tp-gnome`