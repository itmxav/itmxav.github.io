---
id: 365
title: 'Сброс пароля администратора OwnCloud'
date: '2018-11-23T14:40:11+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=365'
permalink: /2018/11/23/sbros-parolya-administratora-owncloud/
views:
    - '661'
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
    - '65'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по DevOps'
tags:
    - owncloud
format: false
---

Для того чтобы сбросить пароль OwnCloud необходим доступ к консоли сервера, где стоит OwnCloud. Если настройка OwnCloud была по умолчанию, то выполняем:

> `$ sudo -u www-data php /var/www/owncloud/occ user:resetpassword admin`

Если имя пользователя другое и папка установки была другая, то, соответственно, надо указать их. После этого надо указать новый пароль: > `Enter a new password:Confirm the new password:`

Если все сделано правильно, то появится следующее сообщение: > `Successfully reset password for admin`

-- Источник - https://code-inside.com/sbros-parolya-administratora-owncloud/