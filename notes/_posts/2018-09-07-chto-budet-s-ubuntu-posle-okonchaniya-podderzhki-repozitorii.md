---
id: 278
title: 'Что будет с Ubuntu после окончания поддержки?'
date: '2018-09-07T13:29:27+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=278'
permalink: /2018/09/07/chto-budet-s-ubuntu-posle-okonchaniya-podderzhki-repozitorii/
views:
    - '289'
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
    - '103'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Debian, Ubuntu etc.'
tags:
    - linux
format: false
---

Старые версии Ubuntu не поддерживаются Canonical, это означает, что все официальные репозитории для них заморожены и не пополняются обновлениями, устраняющими проблемы с безопасностью. **Репозитории для неподдерживаемых версий:**После окончания поддержки дистрибутива он удаляется с серверов, на которых хранятся репозитории Ubuntu. Это приводит к тому, что при попытке обновить список доступных пакетов выдаётся предупреждение о недоступности всех основных репозиториев. Однако все пакеты из репозитория на момент окончания поддержки не удаляются в никуда, а переводятся на другой сервер, поэтому если вам зачем-либо понадобится репозиторий для неподдерживаемой версии Ubuntu, вы сможете его получить. Для этого заменить все ссылки в файле ***/etc/apt/sources.list***, отвечающие за официальные репозитории, на:

> **http://old-releases.ubuntu.com/ubuntu**

-- Источник - [help.ubuntu.ru](https://help.ubuntu.ru/wiki/old_ubuntu_versions)