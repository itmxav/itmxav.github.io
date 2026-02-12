---
id: 540
title: 'Git через другой (нестандартный) порт ssh'
date: '2019-02-21T15:04:52+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=540'
permalink: /2019/02/21/git-cherez-drugoj-nestandartnyj-port-ssh/
views:
    - '299'
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
    - git
format: false
---

Иногда ssh находится на другом порту, тогда надо его указать. Например:

> `git clone ssh://user@example.org:port/~/my_project/.git`