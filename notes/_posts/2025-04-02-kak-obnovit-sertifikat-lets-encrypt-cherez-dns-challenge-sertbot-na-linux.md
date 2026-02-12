---
id: 3327
title: 'Как обновить сертификат Let&#8217;s Encrypt через DNS Challenge Certbot на Linux?'
date: '2025-04-02T17:51:47+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3327'
permalink: /2025/04/02/kak-obnovit-sertifikat-lets-encrypt-cherez-dns-challenge-sertbot-na-linux/
views:
    - '49'
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
    - linux
format: false
---

Иногда бывают ситуации, что необходимо получить или обновить сертификат для конкретного веб-сайта, но проверку надо пройти через DNS.   
Пройти проверку можно следующим образом:  
1\. Делаем запрос через certbot с указанием email для уведомлений, соглашения с условиями, ручного запуска проверки для конкретного сайта с адресом example.org:

```
[code lang="plain"]certbot --text --agree-tos --email user@example.org -d test.example.org --manual --preferred-challenges dns --expand certonly[/code]
```

2\. После запуска будет получен текст и куда его надо разместить. Главное не нажимать ничего пока TXT-запись не будет внесена в DNS. Пример записи в части example.org:

```
[code lang="plain"]_acme-challenge.test IN TXT "Полученный_текст"[/code]
```

3\. После внесения записи и её проверки можно нажимать Enter, чтобы пройти DNS Challenge.  
4\. Если всё успешно прошло, то будут получены нужные файлы.