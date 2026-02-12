---
id: 843
title: 'Как сохранить правила iptables в Ubuntu 20 / Debian?'
date: '2021-06-02T00:24:26+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=843'
permalink: /2021/06/02/kak-soxranit-pravila-iptables-v-ubuntu-20-debian/
views:
    - '1650'
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
    - 'Debian, Ubuntu etc.'
tags:
    - debian
    - firewall
    - linux
    - ubuntu
format: false
---

Классический способ сохранения правил. 1. Сохраняем правила в файл:

> `# iptables-save > /etc/iptables.v4rules`

2. Создаем скрипт в загрузке интерфейсов: > `# nano /etc/network/if-up.d/00-iptables`

3. Прописываем восстановление правил: > `#!/bin/shiptables-restore < /etc/iptables.v4rules`

4. Даем права на выполенение скрипта: > `# chmod +x /etc/network/if-up.d/00-iptables`

5. Перезагружаемся и проверяем.