---
id: 697
title: 'Как отправить почту из терминала Linux через mailutils?'
date: '2020-04-05T21:48:04+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=697'
permalink: /2020/04/05/kak-otpravit-pochtu-iz-terminala-linux-mailutils/
views:
    - '1901'
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
tags:
    - linux
    - mail
format: false
---

Для начала установим mailutils. Если не установить, то увидим примерно следующее оповещение:

> `mail: command not found`

**Установка**В Debian / Ubuntu: > `# apt-get install mailutils`

В CentOS / Red Hat: > `# yum install mailx`

**Отправить можно так:**> `echo "Hi!" | mail -s "Test" test@example.loc`

В данном случае письмо с темой "Test" и содержимым "Hi!" отправляется по адресу test@example.loc Если возникают проблемы, то надо смотреть в логах. Обычно в /var/log/maillog. **Отправить письмо с вложением:**> `echo "Hi!" | mail -s "Test" -a /var/log/maillog test@example.loc`

**Отправить по нескольким адресам:**> `echo "Hi!" | mail -s "Test" test1@example.loc,test2@example.loc`

**Отправить с указанием отправителя:**> `echo "Hi!" | mail -s "Test" test2@example.loc -aFrom:test1@example.loc`

или > `echo "Hi!" | mail -s "Test" -r test1@example.loc test2@example.loc`

**Отправить письмо через другой SMTP сервер:**> `echo "Hi!" | mail -s "Test" -S smtp="smtp.example.loc:25" test@example.loc`

Если есть шифрование, то необходимо указывать соответствующие параметры для отправки письма. Например: сервер отправки по smtp, порт для подключения, указать тип шифрования, от кого. Все зависит от того? как настроен сервер отправки. Подробней про параметры смотрите через man, help. -- Источник - [Отправка почты из командной строки Linux](https://www.dmosk.ru/miniinstruktions.php?mini=mail-shell)