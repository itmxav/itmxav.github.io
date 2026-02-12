---
id: 499
title: 'Как изменить корень сайта webroot без запроса нового SSL Let&#8217;s Encrypt?  [Certbot]'
date: '2018-12-13T14:07:06+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=499'
permalink: /2018/12/13/kak-izmenit-koren-sajta-webroot-bez-zaprosa-novogo-ssl-lets-encrypt-certbot/
views:
    - '300'
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
format: false
---

Для того чтобы изменить пути к файлам сайта (например, переименовали корневой каталог сайта) необходимо перейти в каталог renewal:

> `$ cd /etc/letsencrypt/renewal`

Отредактировать конфигурационный файл соответствующий вашему сайту: > `$ sudo editor нужный_файл`

В разделе webroot\_map ставин нужные пути к файлам сайта > `[[webroot_map]]домен1 = /абсолютный/путь/к/файлам/сайтаwww.домен1 = /абсолютный/путь/к/файлам/сайта `

Сохранить и выйти из редактора. Теперь при автоматическом пере запросе SSL ссылаться Certbot будет на новый webroot.