---
id: 2622
title: 'Как обновить Gitlab?'
date: '2024-02-05T15:05:32+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2622'
permalink: /2024/02/05/kak-obnovit-gitlab/
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
views:
    - '109'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по DevOps'
tags:
    - git
format: false
---

***Заранее сделайте бэкап данных.***

1\. Смотрим, что доступно:

\[code lang="plain"\]# apt list gitlab-ce -a\[/code\]

2\. Обновляем по последним версиям gitlab.  
Т.е. 16.2.3(текущая)-&gt;16.2.9(последняя в 16.2)-&gt;16.3.7(последняя в 16.3)-&gt;16.4.5(последняя в 16.4)-&gt;и т.д. Обновляемся следующим образом:

\[code lang="plain"\]# apt install gitlab-ce=16.2.9-ce.0\[/code\]

3\. После установок можно почистить кэш от пакетов:

\[code lang="plain"\]# apt clean\[/code\]