---
id: 2432
title: 'Как собрать образ из контейнера Docker для отправки в реестр?'
date: '2023-12-06T11:14:59+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2432'
permalink: /2023/12/06/kak-sobrat-obraz-iz-kontejnera-docker-dlya-otpravki-v-reestr/
views:
    - '32'
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

1\. Собираем

\[code lang="plain"\]docker commit -m "message" -a "Author" ID\_container Address\_Server/registry/nameContainer:tag\[/code\]

  
2\. Отправляем

\[code lang="plain"\]docker push Address\_Server/registry/nameContainer:tag\[/code\]