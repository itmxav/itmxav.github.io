---
id: 2937
title: 'Как изменить сеть для контейнеров в Docker Desktop на Windows 11?'
date: '2024-07-22T20:50:34+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2937'
permalink: /2024/07/22/kak-izmenit-set-dlya-kontejnerov-v-docker-desktop-na-windows-11/
views:
    - '81'
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
    - '82'
image: /wp-content/uploads/2024/07/Надпись.jpg
categories:
    - 'Записи FastHowTo'
    - 'Записи по DevOps'
    - 'Записи по Windows'
tags:
    - docker
    - windows
format: false
---

Чтобы изменить сеть для контейнеров в Docker Desktop надо:  
1\. Запустить Docker Desktop и остановить все контейнеры, если они запущены.  
2\. Далее перейти в раздел настройки и выбрать пункт Docker Engine.  
3\. Добавить в конфигурации после **"experimental": false**  
\[code lang="plain"\], "default-address-pools":\[ {"base":"10.77.0.0/24","size":24} \]\[/code\]   
4\. Если добавлено всё корректно, то никаких ошибок не выскочит под формой.  
5\. Далее применяем "Apply &amp; restart" и ждем пока всё перезагрузится.  
6\. После загрузки запускаем контейнер для проверки и смотрим в параметрах контейнера, в Inspect, раздел Network. Там уже должна быть новая сеть.

Видео на Youtube:

<iframe allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen="" frameborder="0" height="220" referrerpolicy="strict-origin-when-cross-origin" src="https://www.youtube.com/embed/q-mWe0SOX9o" title="Как изменить сеть для контейнеров в Docker Desktop на Windows 11?  [FastHowTo]" width="330"></iframe>

Видео на Rutube:

<iframe allow="clipboard-write; autoplay" allowfullscreen="" frameborder="0" height="220" mozallowfullscreen="" src="https://rutube.ru/play/embed/dd5bc0bae66d73cec39ebc561cec772e" webkitallowfullscreen="" width="330"></iframe>