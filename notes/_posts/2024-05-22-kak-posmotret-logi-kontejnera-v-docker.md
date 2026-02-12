---
id: 2881
title: 'Как посмотреть логи контейнера в Docker?'
date: '2024-05-22T16:29:55+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2881'
permalink: /2024/05/22/kak-posmotret-logi-kontejnera-v-docker/
views:
    - '43'
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
    - docker
format: false
---

Посмотреть просто логи конейнера на данный момент:  
\[code lang="plain"\]docker logs NameContainer\[/code\]

Отслеживать появляющиеся новые сообщения в логах:  
\[code lang="plain"\]docker logs -f NameContainer\[/code\]

Посмотреть логи за определенный период:  
\[code lang="plain"\]docker logs -f NameContainer --since 2024-04-30 --until 2024-05-01\[/code\]