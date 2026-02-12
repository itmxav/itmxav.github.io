---
id: 3373
title: 'Проблемы обновления сертификатов Let&#8217;s Encrypt через certbot на AltLinux при проверки через webroot'
date: '2025-08-25T17:52:12+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3373'
permalink: /2025/08/25/problemy-obnovleniya-lets-encrypt-certbot-altlinux-proverki-webroot/
views:
    - '21'
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
    - altlinux
format: false
---

Неожиданно столкнулся с проблемой, что сертификаты Let's Encrypt не обновляются через certbot на AltLinux. Ошибка такая:

```
[code lang="plain"]
All renewal attempts failed. The following certs could not be renewed:
/etc/letsencrypt/live/domain_name/fullchain.pem (failure)
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1 renew failure(s), 0 parse failure(s)

IMPORTANT NOTES:
- The following errors were reported by the server:

Domain: domain_name
Type: unauthorized
Detail: IP_address: Invalid response from
http://domain_name/.well-known/acme-challenge/234desfsfsdfs:
404
[/code]
```

  
Редиректов нет. Тестовый файл по адресу http://domain\_name/.well-known/acme-challenge/1 открылся нормально, но при renew выдает, что не может найти проверочный файл. По правам на папки тоже всё нормально, т.е. создаваться всё может в этой папке без проблем. Решить удалось только когда вручную был создан запрос и указан путь к корню сайта:

```
[code lang="plain"]certbot certonly --email pochta@example.org --webroot -w /var/www/site/ -d domain_name[/code]
```