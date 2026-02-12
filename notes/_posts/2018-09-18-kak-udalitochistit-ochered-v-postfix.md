---
id: 316
title: 'Как удалить/очистить очередь в Postfix?'
date: '2018-09-18T14:16:03+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=316'
permalink: /2018/09/18/kak-udalitochistit-ochered-v-postfix/
views:
    - '314'
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
    - 'Записи по Linux'
tags:
    - linux
    - postfix
format: false
---

Просмотр очереди:

> `# postqueue -p`

Просмотр сообщения (cодержимое, заголовок и тело): > `# postcat -vq mail_queue_id`

Если необходимо удалить конкретное письмо (надо знать письма ID): > `# postsuper -d mail_queue_id`

Чтобы очистить очередь в Postfix MTA: > `# postfix flushили# postfix -f`

Чтобы удалить всю почту из очереди: > `# postsuper -d ALL`

Чтобы удалить все письма в отложенной очереди (deferred): > `# postsuper -d ALL deferred`

Чтобы удалить все письма из почтовой очереди, которые пришли с test\_user@example.org или отправлены на адрес test\_user@example.org (команда одинакова независимо от того, является ли это адресом отправителя или получателя), вы можете использовать mailq с командами: > `# mailq | tail -n +2 | awk 'BEGIN { RS = "" } /test_user@example\.org$/ { print $1 }' | tr -d '*!' | postsuper -d -`

-- Источник - [linux-notes.ru](https://linux-notes.org/udalit-ochistit-sbrosit-ochered-v-postfix/)