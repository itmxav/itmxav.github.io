---
id: 2435
title: 'Как работать с Docker через прокси?'
date: '2023-12-06T11:27:37+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2435'
permalink: /2023/12/06/kak-rabotat-s-docker-cherez-proksi/
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
    - '56'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по DevOps'
tags:
    - docker
format: false
---

1\. Создаем папку

\[code lang="plain"\]mkdir -p /etc/systemd/system/docker.service.d\[/code\]

2\. Создаем файл конфигурации прокси для Docker

\[code lang="plain"\]nano /etc/systemd/system/docker.service.d/http-proxy.conf\[/code\]

3\. Прописываем нужные параметры

\[code lang="plain"\]\[Service\] Environment="HTTP\_PROXY=http://Address\_Server:PORT" Environment="HTTPS\_PROXY=http://Address\_Server:PORT" Environment="NO\_PROXY="localhost,127.0.0.1,::1" \[/code\]

4\. Смотрим, что получилось

\[code lang="plain"\]systemctl show --property=Environment docker\[/code\]

5\. Перезапускаем

\[code lang="plain"\]systemctl restart docker\[/code\]