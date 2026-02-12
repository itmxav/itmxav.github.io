---
id: 106
title: 'Как снять ограничение 2 мб в Apache2?'
date: '2017-09-07T19:00:47+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=106'
permalink: /2017/09/07/kak-snyat-ogranichenie-2-mb-v-apache2/
views:
    - '1538'
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
    - 'Записи FastHowTo'
    - 'Записи по Linux'
tags:
    - apache2
    - fasthowto
    - web
format: false
---

**1 способ - php.ini:**Редактируем php.ini > `#vi /etc/php5/apache2/php.ini`

Корректируем на то, что нам нужно: > `upload_max_filesize = 100M — максимальный размер загружаемого файла,post_max_size = 100M — максимальный размер сообщения методом POST.`

**2 способ - .htaccess:**Создаем или редактируем, если уже есть, в корне сайта .htaccess > `#vi .htaccess`

Добавляем параметры: > `php_value upload_max_filesize 100Mphp_value post_max_size 100M`

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="300" src="https://www.youtube.com/embed/jXcbUaEC2YA" width="400"></iframe>