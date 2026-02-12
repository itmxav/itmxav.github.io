---
id: 702
title: 'Как отправить почту из терминала Linux через mutt?'
date: '2020-04-05T21:58:38+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=702'
permalink: /2020/04/05/kak-otpravit-pochtu-iz-terminala-linux-cherez-mutt/
views:
    - '235'
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
    - 'RedHat, CentOS etc.'
    - 'Записи по Linux'
format: false
---

Для начала установим mutt. Если не установить, то увидим примерно следующее оповещение:

> `mail: command not found`

**Установка**В Debian / Ubuntu: > `# apt-get install mutt`

В CentOS / Red Hat: > `# yum install mutt`

**Если нужно указать отправителя, то:**> `echo "Hi!" | mail -s "Test" -e 'my_hdr From: UserName <testusername@example.loc>' -- test@example.loc`

**Отправить письмо с вложением:**> `echo "Hi!" | mail -s "Test" -a /var/log/maillog -- test@example.loc`

-- Источник - [Отправка почты из командной строки Linux](https://www.dmosk.ru/miniinstruktions.php?mini=mail-shell)