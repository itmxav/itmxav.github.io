---
id: 2818
title: 'Блокирование ботов по User-Agent в Nginx'
date: '2024-03-13T14:07:30+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2818'
permalink: /2024/03/13/blokirovanie-botov-po-user-agent-v-nginx/
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
    - '395'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по DevOps'
tags:
    - nginx
    - web
format: false
---

Короткая заметка, чтобы можно было быстро найти.  
[Недавно касался темы ботов](/2024/03/13/zaprosy-s-user-agent-claudebot/). Самый простой вариант заблокировать ботов по User-Agent в Nginx

\[code lang="plain"\]if ($http\_user\_agent ~\* (GPTBot|claudebot|GeedoProductSearch|GeedoBot|Amazonbot|Bytespider|SeopultContentAnalyzer|SeekportBot|DataForSeoBot|Barkrowler|BLEXBot|SemrushBot|MJ12bot|AhrefsBot|bingbot|DotBot|PetalBot|LinkpadBot|SputnikBot|statdom.ru|MegaIndex.ru|WebDataStats|Jooblebot|Baiduspider|BackupLand|NetcraftSurveyAgent|openstat.ru|thesis-research-bot|fidget-spinner-bot|facebookexternalhit)){ return 444; }\[/code\]

Если не хочется загружать конфиг, то можно вынести в отдельное место и подключить файл через include.