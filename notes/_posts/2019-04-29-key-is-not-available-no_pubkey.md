---
id: 613
title: 'key is not available: NO_PUBKEY'
date: '2019-04-29T21:38:20+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=613'
permalink: /2019/04/29/key-is-not-available-no_pubkey/
views:
    - '354'
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
format: false
---

При update, например, в ubuntu появляется такая ошибка **«W: GPG error: \[..\] Release: The following signatures couldn’t be verified because the public key is not available: NO\_PUBKEY \[..\]**. Решить эту проблему можно так:

> `# gpg --keyserver keyserver.ubuntu.com --recv-keys [тут key GPG]`

> `# gpg --export --armor [тут key GPG] | apt-key add -`

> `# apt-get update `

или можно все ключи обновить: > `# apt-key adv --recv-keys --keyserver keyserver.ubuntu.com `apt-get update 2>&1 | grep -o '[0-9A-Z]\{16\}$' | xargs``