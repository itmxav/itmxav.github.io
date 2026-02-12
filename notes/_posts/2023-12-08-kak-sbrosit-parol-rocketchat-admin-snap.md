---
id: 2462
title: 'Как сбросить пароль RocketChat (admin) SNAP?'
date: '2023-12-08T12:33:09+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2462'
permalink: /2023/12/08/kak-sbrosit-parol-rocketchat-admin-snap/
views:
    - '196'
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
    - 'Записи по DevOps'
tags:
    - linux
    - rocketchat
format: false
---

Сброс пароля RocketChat:  
1\. Подключаемся к СУБД

\[code lang="plain"\]rocketchat-server.mongo\[/code\]

2\. Выбираем область

\[code lang="plain"\]use parties\[/code\]

3\. Создаем временную одноразовую ссылку для смены пароля

\[code lang="plain"\]db.getCollection('users').update({username:"ПОЛЬЗОВАТЕЛЬ"}, {$set: { "services":{"loginToken":{"token":"ТокенПридуманный"}}, "requirePasswordChange":true} })\[/code\]

или можно изменить пароль через bcrypt

\[code lang="plain"\]db.getCollection('users').update({username:"ПОЛЬЗОВАТЕЛЬ"}, { $set: {"services" : { "password" : {"bcrypt" : "хэш" } } } })\[/code\]

4\. Переходим по ссылке и меняем пароль

\[code lang="plain"\]https://домен/login-token/ТокенПридуманный\[/code\]