---
id: 3316
title: 'Как конвертировать публичный ключ SSH в формат RFC4716?'
date: '2025-04-02T12:51:18+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3316'
permalink: /2025/04/02/kak-konvertirovat-publichnyj-klyuch-ssh-v-format-rfc4716/
views:
    - '18'
wp_statistics_words_count:
    - '22'
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
    - ssh
format: false
---

Иногда бывает нужно перевести публичный ключ SSH в формат RFC4716 (например, для ProFTPD). Сделать это можно следующим образом:

> ssh-keygen -ef ~/.ssh/id\_rsa.pub &gt; ~/path/to/file/id\_rsa.pub