---
id: 2028
title: 'The certificate of  is not trusted. Let’s Encrypt. Debian.'
date: '2023-01-26T04:12:38+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=2028'
permalink: /2023/01/26/the-certificate-of-is-not-trusted-lets-encrypt/
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
    - '229'
image: /wp-content/uploads/2023/01/Надпись-1.jpg
categories:
    - 'Записи по DevOps'
tags:
    - linux
    - web
format: false
---

Из-за изменений [проверки сертификатов от Let's Encrypt ](https://letsencrypt.org/2019/04/15/transitioning-to-isrg-root.html) можно получить ошибки:

\[code lang="plain"\]ERROR: The certificate of ‘web-site’ is not trusted.&amp;lt;br&amp;gt; ERROR: The certificate of ‘web-site’ has expired.\[/code\]

Чтобы убрать неактульный Root для сертификата надо:  
1\. Открыть:  
\[code lang="plain"\]nano /etc/ca-certificates.conf\[/code\]

2\. Найти  
\[code lang="plain"\]mozilla/DST\_Root\_CA\_X3.crt\[/code\]

3\. Исключить и сохранить:  
\[code lang="plain"\]!mozilla/DST\_Root\_CA\_X3.crt\[/code\]

4\. Обновить:  
\[code lang="plain"\]update-ca-certificates -f\[/code\]

Видео:

<iframe allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen="" frameborder="0" height="220" src="https://www.youtube.com/embed/KXJG_FE7pdc" title="The certificate of is not trusted. Let’s Encrypt. Debian." width="330"></iframe>