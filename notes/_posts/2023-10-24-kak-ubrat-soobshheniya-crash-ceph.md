---
id: 2389
title: 'Как убрать сообщения crash Ceph?'
date: '2023-10-24T13:08:00+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=2389'
permalink: /2023/10/24/kak-ubrat-soobshheniya-crash-ceph/
views:
    - '109'
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
    - ceph
format: false
---

1\. Посмотреть уведомление crash

\[code lang="plain"\]ceph crash ls\[/code\]

2\. Конкретное сообщение

\[code lang="plain"\]ceph crash info ИД\_СООБЩЕНИЯ\[/code\]

3\. Архивировать сообщение  
\[code lang="plain"\]ceph crash archive ИД\_СООБЩЕНИЯ\[/code\]

или все сообщения  
\[code lang="plain"\]ceph crash archive-all\[/code\]