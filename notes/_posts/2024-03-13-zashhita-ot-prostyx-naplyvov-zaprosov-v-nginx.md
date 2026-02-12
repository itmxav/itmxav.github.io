---
id: 2795
title: 'Защита от простых наплывов запросов в Nginx'
date: '2024-03-13T11:57:20+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2795'
permalink: /2024/03/13/zashhita-ot-prostyx-naplyvov-zaprosov-v-nginx/
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
    - '84'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по DevOps'
    - 'Записи по Linux'
tags:
    - nginx
    - web
format: false
---

Часто, когда сайт начинает становится более популярным, всякие нехорошие люди (ботов люди создают) пытаются его положить наплывом запросов.

Можно попытаться защититься стандартными решениями на Nginx. В качестве ответов сервера здесь выдается 444 код (закрывает соединение без отправки данных), но можно ставить тот, который посчитаете нужным.

**1. Когда в запросах идут левые заголовки**, то можно оставить только нужные, а по остальным не отвечать:

\[code lang="plain"\]if ($request\_method !~ ^(GET|POST|HEAD)$ ) { return 444; }\[/code\]

**2. Если запросы идут внешне нормальные, но с разными http\_referer** (например, с взломанных сайтов), то можно вести черные список при помощи map.

2.1 Перед разделом server в vhost создаем map

\[code lang="plain"\]map $http\_referer $bad\_referer { default 0; "~https://example.com" 1; }\[/code\]

Аналогично example.com можно добавлять в новой строке и другие http\_referer.

2.2 В разделе server создаем условие на проверку

\[code lang="plain"\]if ($bad\_referer) { return 444; }\[/code\]

Если в http\_referer указан https://example.com, то он будет получать 444 от Nginx.

**3. Если нужно ограничить количество запросов от IP-адресов**, но некоторые адреса надо исключить, то можно применять limit\_req со списком исключений (geo+map).

3.1 Формируем список перед разделом server в vhost

\[code lang="plain"\]geo $limited\_net { default 1; 192.168.1.0/24 0; }\[/code\]

Сеть 192.168.1.0/24 будет в исключениях.

3.2 Создаем map c $binary\_remote\_addr

\[code lang="plain"\]map $limited\_net $addr\_to\_limit { 0 ""; 1 $binary\_remote\_addr; }\[/code\]

$binary\_remote\_addr - параметр в Nginx, который отвечающий за адрес клиента.

3.3 Перед разделом server создаем условия по запросам. В данном случае создаем зону reqtest, где возможно отправлять с одного IP 10 запросов в секунду.

\[code lang="plain"\]limit\_req\_zone $addr\_to\_limit zone=reqtest:10m rate=10r/s;\[/code\]

3.4 В location ставим limit\_req с возможностью всплеска 50:

\[code lang="plain"\]limit\_req zone=reqtest burst=50;\[/code\]

Если нужно без задержек обрабатывать всплески, то надо добавить nodelay после burst. Если запросы выше всплеска, то будут отбрасываться.

**4. Если надо ограничить количество одновременных запросов от IP-адреса,** то можно применить \[code lang="plain"\]limit\_conn\_zone.\[/code\]

4.1 Перед разделом server создаем зону.

\[code lang="plain"\]limit\_conn\_zone $binary\_remote\_addr zone=conntest:10m;\[/code\]

4.2 В разделе server указываем условия одновременных подключений. В данном примере 30.

\[code lang="plain"\]limit\_conn conntest 30;\[/code\]

Конечно, это всё защита не от серьезного DDOS'a, но в блокировке всяких мутных ботов может помочь. Плюс хорошо бы ещё добавить fail2ban для выявления и блокирования странных запросов в логах.