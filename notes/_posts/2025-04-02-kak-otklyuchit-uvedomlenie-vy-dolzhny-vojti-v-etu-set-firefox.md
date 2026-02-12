---
id: 3318
title: 'Как отключить уведомление &#171;Вы должны войти в эту сеть перед тем как сможете получить доступ в Интернет&#187; (отключение поддержки Captive portal) в Mozilla Firefox?'
date: '2025-04-02T13:00:07+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3318'
permalink: /2025/04/02/kak-otklyuchit-uvedomlenie-vy-dolzhny-vojti-v-etu-set-firefox/
views:
    - '43'
wp_statistics_words_count:
    - '41'
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
image: /wp-content/uploads/2021/08/question-1015308_640-e1627931854783.jpg
categories:
    - 'Разные записи'
tags:
    - Разное
format: false
---

Это сообщения является частью механизма Captive portal. Если оно мешает, то его можно отключить следующим способом:

1\. В адресной строке браузера надо прописать *about:config* и нажать *"Принять риск"*.  
2\. Находим параметр *network.captive-portal-service.enabled* и меняем его значение на *false*.

После этого сообщение не будет появляться.