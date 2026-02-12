---
id: 156
title: 'Отключение приветствия SSH'
date: '2018-06-14T14:38:43+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=156'
permalink: /2018/06/14/otklyuchenie-privetstviya-ssh/
views:
    - '383'
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
    - ssh
format: false
---

При успешном логине по SSH выводится динамически генерируемая информация из файла <ins>/run/motd.dynamic</ins>, а также статическая информация (редактируемая администратором) из файла <ins>/etc/motd</ins>. Для отключения вывода этой информации необходимо закомментировать в файле <ins>/etc/pam.d/sshd</ins> следующую строку:

> session optional pam\_motd.so

или все строки с упоминанием <ins>pam\_motd.so</ins>: > session optional pam\_motd.so motd=/run/motd.dynamic noupdate session optional pam\_motd.so # \[1\]

Если требуется отключить приветствие не только по SSH, но и при прямом доступе, закомментируйте так же эти строки в файле <ins>/etc/pam.d/login</ins>. Теперь при входе в систему выводится лишь информация о последней успешной авторизации. Её также можно отключить, изменив в файле <ins>/etc/ssh/sshd\_config</ins> значение <ins>PrintLastLog yes</ins> на <ins>PrintLastLog no</ins> и перезапустив SSH: > sudo /etc/init.d/ssh restart

Однако в целях безопасности отключать информацию о последней авторизации не рекомендуется. --- Источник: <https://neblog.info/otklyuchenie-privetstviya-ssh>