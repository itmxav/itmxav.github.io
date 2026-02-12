---
id: 2380
title: 'Как работать с Docker под своим пользователем?'
date: '2023-10-17T12:54:27+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=2380'
permalink: /2023/10/17/kak-rabotat-s-docker-pod-svoim-polzovatelem/
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
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по DevOps'
tags:
    - docker
format: false
---

Чтобы не сидеть под root, а работать под своим пользователем надо пользователя закинуть в группу Docker'а:

\[code lang="plain"\]usermod -aG docker ИМЯ\_пользователя\[/code\]