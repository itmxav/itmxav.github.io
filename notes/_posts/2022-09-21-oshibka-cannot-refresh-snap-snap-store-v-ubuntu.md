---
id: 1674
title: 'Ошибка cannot refresh snap &#171;snap-store&#187; в Ubuntu'
date: '2022-09-21T18:18:05+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=1674'
permalink: /2022/09/21/oshibka-cannot-refresh-snap-snap-store-v-ubuntu/
views:
    - '968'
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
    - 'Debian, Ubuntu etc.'
tags:
    - linux
    - ubuntu
format: false
---

На Ubuntu 20/22 может возникнуть ошибка:

\[code lang="plain"\]snapstate.go: cannot refresh snap "snap-store": snap "snap-store" has running apps (ubuntu-software)\[/code\]

Можно решить следующим образом - убить процессы все и перезапустить snap:

\[code lang="plain"\]killall snap-store snap refresh\[/code\] 