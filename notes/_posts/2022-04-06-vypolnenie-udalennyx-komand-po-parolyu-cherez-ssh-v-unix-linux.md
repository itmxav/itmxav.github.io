---
id: 946
title: 'Выполнение удаленных команд по паролю через SSH в Unix/Linux'
date: '2022-04-06T17:54:49+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=946'
permalink: /2022/04/06/vypolnenie-udalennyx-komand-po-parolyu-cherez-ssh-v-unix-linux/
views:
    - '211'
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
    - 'Записи по Linux'
tags:
    - linux
    - ssh
format: false
---

Для того чтобы можно было заходить по паролю необходимо установить утилиту sshpass. После установки можно отправлять команды на удаленный хоcт:

> `sshpass -p 'password' ssh user@ip  << EOF<br></br>command1<br></br>command2<br></br>command3<br></br>EOF```