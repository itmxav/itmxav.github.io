---
id: 2368
title: 'Установка RustDesk через docker-compose'
date: '2023-10-17T12:44:27+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=2368'
permalink: /2023/10/17/ustanovka-rustdesk-cherez-docker-compose/
views:
    - '785'
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

1\. Создаем файл \[code lang="plain"\]docker-compose.yml\[/code\]  
2\. Прописываем следующие параметры для образа

\[code lang="plain"\]version: '3' networks: rustdesk-net: external: false services: hbbs: container\_name: hbbs ports: - 21115:21115 - 21116:21116 - 21116:21116/udp - 21118:21118 image: rustdesk/rustdesk-server:latest command: hbbs -r &amp;lt;ip-адрес машины&amp;gt;:21117 -k \_ volumes: - ./data:/root networks: - rustdesk-net depends\_on: - hbbr restart: unless-stopped hbbr: container\_name: hbbr ports: - 21117:21117 - 21119:21119 image: rustdesk/rustdesk-server:latest command: hbbr -k \_ volumes: - ./data:/root networks: - rustdesk-net restart: unless-stopped\[/code\] 3\. Ключ \[code lang="plain"\]-k \_ \[/code\] говорить о том, что будет использоваться только шифрованное соединение. Открытый ключ хранится в папке data

4\. Запускаем \[code lang="plain"\]docker-compose up -d\[/code\]

5\. На клиенте указываем ip-адрес машины (id серверва, шлюз ретранслятора), открытый ключ и пробуем подключиться.