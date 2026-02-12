---
id: 3048
title: 'GitLab не обновляет сертификат Let&#8217;s Encrypt после своего upgrade'
date: '2024-10-03T17:00:59+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3048'
permalink: /2024/10/03/gitlab-ne-obnovlyaet-sertifikat-lets-encrypt-posle-svoego-upgrade/
views:
    - '59'
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
wp_statistics_words_count:
    - '44'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по DevOps'
    - 'Записи по Linux'
tags:
    - git
format: false
---

Спустя несколько месяцев после upgrade GitLab начал выдавать ошибку, что не смог обновить сертификат от Let's Encrypt. При обновлении вручную через

```
[code lang="plain"]gitlab-ctl renew-le-certs [/code]
```

сертификат тоже не хотел обновляться.   
Помогла реконфигурация, в процессе которой GitLab запросил новый сертификат и нормально всё обновил.

```
[code lang="plain"]gitlab-ctl reconfigure [/code]
```