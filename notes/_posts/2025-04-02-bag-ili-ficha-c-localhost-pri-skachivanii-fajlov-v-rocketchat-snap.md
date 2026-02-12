---
id: 3321
title: 'Баг или фича c localhost при скачивании файлов в RocketChat (snap)'
date: '2025-04-02T14:21:52+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3321'
permalink: /2025/04/02/bag-ili-ficha-c-localhost-pri-skachivanii-fajlov-v-rocketchat-snap/
views:
    - '32'
wp_statistics_words_count:
    - '188'
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
    - rocketchat
format: false
---

Наткнулся на странный баг или фичу в RocketChat после очередного обновления через snap. Плюс на входе nginx, который проксирует запросы. Можно было бы через docker всё поднять, но пока что через snap развернуто всё. После того как RocketChat перезапустился, то он просит, после входа в систему, изменить или подтвердить данные по адресу (домену). Нажимаю кнопку чтобы была привязка к домену, как и было. В итоге подключиться можно, но если попытать скачать файл, то вместо домена подсовывается localhost. Если скопировать ссылку, закинуть её в браузер и поменять localhost на нужный домен, то файл скачивается. После пары экспериментов нашел вывел алгоритм действия:  
0\. Создать отдельного пользователя с правами админа Workspace'a.  
1\. Через браузер заходим в RocketChat под пользователем с правами админа.   
2\. Нажимаем "update config" в появившемся окне.  
3\. В новом появившемся окне выбираем кнопку для изменения параметров и указываем нужный адрес (домен).  
4\. В новом окне кнопку "upgrade config" не трогаем и выходим из системы.

Есть ещё интересный момент. Если после входа в RocketChat под админом перекидывает на страницу с мастером настройки, то пару раз нажимаем Backspace и оказывается уже в самом RocketChat. Возможно, это приколы только в варианте со snap, но всё же.