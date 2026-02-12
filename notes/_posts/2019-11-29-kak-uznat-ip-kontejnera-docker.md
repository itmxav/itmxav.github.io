---
id: 663
title: 'Как узнать ip контейнера docker?'
date: '2019-11-29T13:56:34+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=663'
permalink: /2019/11/29/kak-uznat-ip-kontejnera-docker/
views:
    - '1642'
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
image: /wp-content/uploads/2023/02/Надпись-1.jpg
categories:
    - 'Записи по DevOps'
tags:
    - docker
format: false
---

Для начала ищем ID контейнера (CONTAINER ID):

> `docker ps`

А после ищем ip через grep: > `docker inspect CONTAINER_ID | grep "IPAddress"`

Видео: <iframe allowfullscreen="allowfullscreen" frameborder="0" height="220" src="https://www.youtube.com/embed/NnERAzH86W4" title="" width="330"></iframe>UPD ([комментарий Александра](/2019/11/29/kak-uznat-ip-kontejnera-docker/#comment-139)). Поиск адреса с учетом иерархии расположения запрашиваемого поля IPAddress: <div class="comment-body">> *Не совсем корректный пример т.к. поле IPAddress может присутсоватьа более 1 раза т.е. в нескольких местах выводимой информации. Например:**…**«NetworkSettings-&gt;»IPAddress»**и там же только ниже**«NetworkSettings»-&gt;»Networks»-&gt;НАЗВАНИЕ\_ПОДСЕТИ-&gt;»IPAddress»**….**более корректно использовать команду с учетом иерархии расположения запрашиваемого поля IPAddress:**docker container inspect -f «{{ .NetworkSettings.Networks.НАЗВАНИЕ\_ПОДСЕТИ.IPAddress }}» контейнер*

Например, IP-адрес контейнера myredis с учетом названия подсети bridge можно получить следующим образом: > `<em>docker container inspect -f '{{ .NetworkSettings.Networks.bridge.IPAddress }}' myredis</em>`

</div>