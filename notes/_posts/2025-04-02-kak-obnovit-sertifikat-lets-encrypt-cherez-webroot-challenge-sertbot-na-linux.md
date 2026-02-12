---
id: 3329
title: 'Как обновить сертификат Let&#8217;s Encrypt через Webroot Challenge Certbot на Linux?'
date: '2025-04-02T17:53:37+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3329'
permalink: /2025/04/02/kak-obnovit-sertifikat-lets-encrypt-cherez-webroot-challenge-sertbot-na-linux/
views:
    - '66'
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
    - '110'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по DevOps'
tags:
    - linux
format: false
---

Иногда бывают ситуации, что необходимо получить или обновить сертификат для конкретного веб-сайта, но проверку надо пройти через Webroot Challenge.

1\. Лучше всего чтобы, при проверке, сайт отвечал по 80 порту без редиректов в период обновления или запроса сертификата.  
2\. Делаем запрос через certbot с указанием email для уведомлений, соглашения с условиями, ручного запуска проверки для конкретного сайта с адресом example.org и указанием расположения корня сайта:

```
[code lang="plain"]certbot certonly --webroot --agree-tos --email user@example.org -w /var/www/example.org -d example.org[/code]
```

3\. В процессе проверки будут создан временный файл с текстом, чтобы валидировать сервер и запрос. После подтверждения или неудачного подтверждения файл будет удален.   
4\. Если всё успешно прошло, то будут получены нужные файлы и указано куда они скачались.