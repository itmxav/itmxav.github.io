---
id: 3411
title: 'Ошибка Gitlab: remote: Your SSH key has expired'
date: '2025-09-19T16:30:46+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3411'
permalink: /2025/09/19/oshibka-gitlab-remote-your-ssh-key-has-expired/
views:
    - '45'
wp_statistics_words_count:
    - '116'
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
    - git
    - linux
format: false
---

Иногда бывает ошибка "Gitlab: remote: Your SSH key has expired". В первую очередь надо проверить срок ключа на Gitlab. По умолчанию год выставляется, хотя как такового срока нет у ключа. Если там срок истек, то необходимо заново добавить его:  
1\. Нажимаем на аватарку, переходим в настройки и далее в SSH ключи.  
2\. Видим, что срок истек и ключ отмечен соответствующим знаком.   
3\. Копируем ключ. Удаляем и добавить тот же ключи с более длительным сроком.  
4\. Проверяем работу.

Если же по срокам всё нормально, то проверяйте не заблокирована ли учетная запись, используете ли правильный приватный ключ, меняли ли ключи недавно, не используете ли временный ключ, не удалили ли случайно ключ на Gitlab или локально приватный, не взломан ли комп или сервер.