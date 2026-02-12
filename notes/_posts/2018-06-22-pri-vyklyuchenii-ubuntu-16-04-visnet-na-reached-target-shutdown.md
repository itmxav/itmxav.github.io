---
id: 172
title: 'При выключении Ubuntu 16.04 виснет на Reached Target Shutdown'
date: '2018-06-22T14:52:58+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=172'
permalink: /2018/06/22/pri-vyklyuchenii-ubuntu-16-04-visnet-na-reached-target-shutdown/
views:
    - '596'
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

При выключении Ubuntu 16.04 выснет на Reached Target Shutdown. В данном случает помогает пересборка initramfs:

> `sudo update-initramfs -u`