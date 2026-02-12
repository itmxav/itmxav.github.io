---
id: 443
title: 'Ожидающий (спящий) режим через консоль на Ubuntu 18.04'
date: '2018-12-02T11:32:37+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=443'
permalink: /2018/12/02/ozhidayushhij-spyashhij-rezhim-cherez-konsol-na-ubuntu-18-04/
views:
    - '1006'
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
    - '57'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Debian, Ubuntu etc.'
tags:
    - linux
format: false
---

Для перевода компьютера в спящий режим через терминал надо выполнить команду:

> `$ systemctl suspend`

Так есть и другие варианты перевода компьютера в спящий режим: 1. Закрытие крышки ноутбука (возможно надо будет поставить `gnome-tweaks - sudo apt-get install gnome-tweaks`) 2. Просто зажать кнопку выключения. Кнопка должна будет измениться. А после этого нажать на нее еще раз и компьютер уйдет в спящий режим. ![ss](/wp-content/uploads/2018/12/ss.jpg)