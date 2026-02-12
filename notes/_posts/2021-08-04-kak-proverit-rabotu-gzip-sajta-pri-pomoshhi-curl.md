---
id: 871
title: 'Как проверить работу gzip сайта при помощи curl?'
date: '2021-08-04T21:12:28+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=871'
permalink: /2021/08/04/kak-proverit-rabotu-gzip-sajta-pri-pomoshhi-curl/
views:
    - '258'
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
image: /wp-content/uploads/2021/08/надпись.jpg
categories:
    - 'Записи по Linux'
tags:
    - web
    - команды
format: false
---

Проверить работу gzip можно отправив запрос при помощи curl:

> `curl -H "Accept-Encoding: gzip" -I https://example.com`

В ответе должна быть информация о gzip: HTTP/1.1 200 OK Server: nginx Date: Sat, 02 May 2015 15:00:09 GMT Content-Type: text/html; charset=UTF-8 Content-Length: 20 Connection: keep-alive Cache-Control: max-age=2592000 Expires: Mon, 01 Jun 2015 15:00:08 GMT Vary: User-Agent,Accept-Encoding **Content-Encoding: gzip**Видео на Youtube: <iframe allowfullscreen="allowfullscreen" frameborder="0" height="220" src="https://www.youtube.com/embed/p8MR4GDFdHE" title="Как проверить работу gzip сайта при помощи curl?" width="330"></iframe>Видео на Rutube: <iframe allow="clipboard-write; autoplay" allowfullscreen="" frameborder="0" height="220" mozallowfullscreen="" src="https://rutube.ru/play/embed/49bcaab78f53f2f387a3bd11c395371a" webkitallowfullscreen="" width="330"></iframe>