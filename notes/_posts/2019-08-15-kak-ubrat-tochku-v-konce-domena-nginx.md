---
id: 644
title: 'Как убрать точку в конце домена? Nginx'
date: '2019-08-15T13:59:15+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=644'
permalink: /2019/08/15/kak-ubrat-tochku-v-konce-domena-nginx/
views:
    - '254'
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
    - nginx
format: false
---

Чем опасна точка в конце домена можно почитать [здесь](https://habr.com/ru/post/172999/). Для того чтобы настроить редирект в nginx надо в секции server в виртуальном хосте прописать:

> `if ($http_host ~ "\.$") {return 301 $scheme://$host$request_uri;}`

Например, при обращении на "http://домен./запрос" идет редирект на "http://домен/запрос"