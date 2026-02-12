---
id: 2220
title: 'Какой формат логов в Nginx?'
date: '2023-04-24T14:22:40+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=2220'
permalink: /2023/04/24/kakoj-format-logov-v-nginx/
views:
    - '96'
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
format: false
---

Формат логов в nginx по умолчанию:

\[code lang="plain"\]$remote\_addr - $remote\_user \[$time\_local\] "$request" $status $body\_bytes\_sent "$http\_referer" "$http\_user\_agent" \[/code\]

Расшифровка полей:

\[code lang="plain"\] $remote\_addr – IP с которого был сделан запрос. $remote\_user – Пользователь, аутентифицированный через HTTP аутентификацию, обычно пустое. \[$time\_local\] – Время посещения в часовом поясе сервера. “$request” - Тип HTTP-запроса + запрошенный путь без аргументов + версия HTTP. $status - код ответа от сервера. $body\_bytes\_sent - размер ответа сервера в байтах. “$http\_referer” - реферал (если есть). “$http\_user\_agent” - юзер-агент \[/code\]