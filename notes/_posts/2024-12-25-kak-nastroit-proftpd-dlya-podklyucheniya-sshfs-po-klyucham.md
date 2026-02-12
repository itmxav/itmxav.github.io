---
id: 3210
title: 'Как настроить proftpd для подключения sshfs по ключам?'
date: '2024-12-25T12:55:39+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3210'
permalink: /2024/12/25/kak-nastroit-proftpd-dlya-podklyucheniya-sshfs-po-klyucham/
views:
    - '56'
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
    - '140'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Linux'
tags:
    - linux
    - proftpd
format: false
---

Бывает возникают ситуации, что необходимо настроить proftpd только к определенной области каталогов пользователю для sshfs по ключам. Основную настройку proftpd не будет описавать, т.к. она стандартная. Отмечу только некоторые моменты:  
0\. Некоторые моменты:  
Пример chroot-папки для конкретного пользователя

\[code lang="plain"\]DefaultRoot /home/user123 user123\[/code\]

Хорошо бы чтобы были ограничения по пользователям

> Limit LOGIN&gt;  
> DenyALL  
> AllowUser user123  
> &lt;/Limit&gt;

1\. Далее настраиваем sftp

> &lt;IfModule mod\_sftp.c&gt;  
> SFTPEngine on  
> SFTPHostKey /etc/ssh/ssh\_host\_dsa\_key  
> SFTPHostKey /etc/ssh/ssh\_host\_rsa\_key  
> SFTPLog /var/log/proftpd/sftp.log  
> SFTPCompression delayed  
> SFTPAuthMethods password publickey #способ проверки по пароли, по ключам  
> SFTPAuthorizedUserKeys file:/etc/proftpd/authorized\_keys/%u  
> &lt;/IfModule&gt;

Да, в параметре *SFTPAuthorizedUserKeys* надо указать переменную *%u*. Это надо для проверки ключа конкретного пользователя через его имя.

2\. В директории */etc/proftpd/authorized\_keys/* создаем файл с именем пользователя, например, при помощи редактора nano, и закидываем туда публичный ключ

\[code lang="plain"\]cd /etc/proftpd/authorized\_keys/ nano user123\[/code\]

Ключ в виде

\[code lang="plain"\]---- BEGIN SSH2 PUBLIC KEY ---- AA... ... ... ---- END SSH2 PUBLIC KEY ----\[/code\]

3\. Проверяем конфиг и если всё нормально, то перечитываем конфигурацию proftpd.

\[code lang="plain"\]proftpd -td5 systemctl reload proftpd.service\[/code\]

4\. Пробуем подключиться

\[code lang="plain"\]sshfs user123@IP-address-server:/ /куда/примонтировать\[/code\]

Отмонтироваться можно так

\[code lang="plain"\]fusermount -u /куда/примонтировали\[/code\]