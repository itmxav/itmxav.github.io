---
id: 235
title: 'Certbot. Удалить ненужный сертификат от letsencrypt'
date: '2018-07-23T15:04:13+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=235'
permalink: /2018/07/23/certbot-udalit-nenuzhnyj-sertifikat-ot-letsencrypt/
views:
    - '1079'
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
    - 'Записи по Linux'
tags:
    - linux
format: false
---

Удалить информацию с серверов letsenrypt:

> `certbot revoke --cert-path /etc/letsencrypt/live/CERTNAME/cert.pem`

Удалить сертификаты и все симлинки на локальном сервере: > `certbot delete --cert-name example.com`

Если скачанный certbot,то в папке certbot: > `./certbot-auto revoke --cert-path /etc/letsencrypt/live/CERTNAME/cert.pem``./certbot-auto delete --cert-name example.com`