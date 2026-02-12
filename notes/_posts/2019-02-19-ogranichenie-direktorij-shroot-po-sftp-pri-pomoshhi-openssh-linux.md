---
id: 531
title: 'Ограничение директорий (сhroot) по SFTP при помощи OpenSSH [Linux]'
date: '2019-02-19T15:27:23+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=531'
permalink: /2019/02/19/ogranichenie-direktorij-shroot-po-sftp-pri-pomoshhi-openssh-linux/
views:
    - '480'
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

Например, у нас есть серверная ОС Linux Ubuntu. Иногда пользователя необходимо закрыть в домашней директории. Для этого можно ограничить доступ к папкам по sftp через OpenSSH. Например, есть пользователь utest. Владелец папки /home/utest должен быть root, а права на папку 750. В конфиге `/etc/ssh/sshd_config` надо прописать:

> `Subsystem sftp internal-sftpMatch user utestChrootDirectory /home/utestX11Forwarding noAllowTcpForwarding noForceCommand internal-sftp`

Далее проверить конфиг: > `$ sudo sshd -t`

И перечитать конфиг ssh: > `$ sudo service ssh reload`

-- Дополнительная информация - [Chroot ssh](http://docs.mirocow.com/doku.php?id=system:chroot_ssh)