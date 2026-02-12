---
id: 722
title: 'Как настроить работу через прокси в CentOS Linux?'
date: '2020-04-07T02:32:39+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=722'
permalink: /2020/04/07/kak-nastroit-rabotu-cherez-proksi-v-centos-linux/
views:
    - '1007'
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
    - centos
    - linux
    - proxy
format: false
---

**Настройка системы для работы через proxy**Добавляем в конец файла /etc/profile строки: > `MY_PROXY_URL="http://user:password@ServerProxy:8080/"HTTP_PROXY=$MY_PROXY_URLHTTPS_PROXY=$MY_PROXY_URLFTP_PROXY=$MY_PROXY_URLhttp_proxy=$MY_PROXY_URLhttps_proxy=$MY_PROXY_URLftp_proxy=$MY_PROXY_URLexport HTTP_PROXY HTTPS_PROXY FTP_PROXY http_proxy https_proxy ftp_proxy`

**Настройка работы через proxy для конкретного пользователя**В домашней папке пользователя нужно отредактировать файл .bash\_profile: > `MY_PROXY_URL="http://user:password@ServerProxy:8080/"HTTP_PROXY=$MY_PROXY_URLHTTPS_PROXY=$MY_PROXY_URLFTP_PROXY=$MY_PROXY_URLhttp_proxy=$MY_PROXY_URLhttps_proxy=$MY_PROXY_URLftp_proxy=$MY_PROXY_URLexport HTTP_PROXY HTTPS_PROXY FTP_PROXY http_proxy https_proxy ftp_proxy`

После этого выйти из системы и зайти заново. **Настройка yum для работы через proxy**Надо отредактировать файл /etc/yum.conf в секции main: > `[main]proxy=http://xxx.xxx.xx.x:8080proxy_username=domain\userproxy_password=password`

**Настройка wget для работы через proxy**Надо отредактировать файл /etc/wgetrc. Добавляем: > `http_proxy=http://xxx.xxx.xx.xx:8080https_proxy=http://xxx.xxx.xx.xx:8080proxy_user=domain\userproxy_passwd=password`

-- Источник - [Настройка системного прокси в CentOS Linux ](https://sys-adm.in/os/nix/618-nastrojka-sistemnogo-proksi-v-centos-linux)