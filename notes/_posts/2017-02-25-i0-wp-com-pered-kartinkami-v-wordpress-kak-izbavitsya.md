---
id: 23
title: 'i0.wp.com перед картинками в WordPress. Как избавиться?'
date: '2017-02-25T23:05:56+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=23'
permalink: /2017/02/25/i0-wp-com-pered-kartinkami-v-wordpress-kak-izbavitsya/
views:
    - '1722'
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
    - '87'
image: /wp-content/uploads/2017/02/Logo_Wordpress-e1488053049246.png
categories:
    - 'Записи по CMS'
tags:
    - wordpress
    - сайт
format: false
---

Недавно наткнулся на, что картинки на сайте под управление WordPress отображаются через другие сайта. Т.е. При просмотри ссылки картинки можно увидеть следующее: http://i0.wp.com/it.mxav.ru/wp-content/uploads/2016/11/rt.png вместо: /wp-content/uploads/2016/11/rt.png Такое происходит из-за включенного модуля Photon в плагине Jetpack. В "Ынтернетах" пишут, что это для обхода какого-то firewall'а и снижения нагрузки на сервер (картинки грузятся с другого сервера). На мой взгляд лучше локальная загрузка картинки на сайте, чем через другие сайты отображать эту же локальную картинку. Хотя нагрузка чуть больше станет на сервер. Чтобы картинка стала грузиться с вашего сайта надо перейти в Jetpack-Настройки-Appearance и выключить Photon.