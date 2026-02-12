---
id: 2440
title: 'Docker &#8212; x509 certificate signed by unknown authority self signed'
date: '2023-12-06T11:38:06+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2440'
permalink: /2023/12/06/docker-x509-certificate-signed-by-unknown-authority-self-signed/
views:
    - '122'
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
    - docker
format: false
---

Если при push в Docker возникает ошибка *"x509 certificate signed by unknown authority self signed"*, то её можно решить следующим образом:

1\. Забираем самоподписанный сертификат при помощи scp

\[code lang="plain"\]scp docker\_user@Address\_Server:/etc/docker/certs.d/Address\_Server/ca.crt /etc/docker/certs.d/Address\_Server/ca.crt\[/code\]

  
2\. Логинимся и пробуем сделать push

\[code lang="plain"\]docker login Address\_Server docker push Address\_Server/registry/nameContainer:tag \[/code\]