---
id: 533
title: 'Некорректное отображение файлов и папок при подключении по ftp/sftp к Proftpd'
date: '2019-02-19T15:37:36+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=533'
permalink: /2019/02/19/nekorrektnoe-otobrazhenie-fajlov-i-papok-pri-podklyuchenii-po-ftpsftp-k-proftpd/
views:
    - '254'
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
image: /wp-content/uploads/2018/09/data.png
categories:
    - 'Записи по Linux'
tags:
    - proftpd
format: false
---

Если у вас некорректно отображаются файлов и папки при подключении по ftp/sftp к Proftpd. Т.е. в названии папок и файлов дата+само название, то необходимо прописать в конфиге `/etc/proftpd/proftpd.conf` в самом начале переменную:

> `Unsetenv LANG`

Проверить конфиг > `$ sudo proftpd -t`

и перечитать конфиг. Если ubuntu, то например > `$ sudo service proftpd reload`

-- Подробнее можно прочитать здесь - [ProFTPD module mod\_sftp](http://www.proftpd.org/docs/contrib/mod_sftp.html)