---
id: 708
title: 'Как отключить IPv6 в дистрибутиве Linux?'
date: '2020-04-06T00:28:05+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=708'
permalink: /2020/04/06/kak-otklyuchit-ipv6-v-distributive-linux/
views:
    - '219'
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
    - сети
format: false
---

Чтобы отключить IPv6: Fedora/OpenSUSE и другие ОС RedHat

> `# sysctl -w net.ipv6.conf.all.disable_ipv6 = 1`

ОС на основе Ubuntu/Debian > `# echo '' >> /etc/sysctl.conf# echo 'net.ipv6.conf.all.disable_ipv6 = 1' >> /etc/sysctl.conf`

Далее: Fedora/OpenSUSE и другие ОС RedHat > `# sysctl -w net.ipv6.conf.default.disable_ipv6 = 1`

ОС на основе Ubuntu/Debian > `# echo 'net.ipv6.conf.default.disable_ipv6 = 1' >> /etc/sysctl.conf# echo 'net.ipv6.conf.lo.disable_ipv6 = 1' >> /etc/sysctl.conf`

Если команды успешно завершились,то Linux-машина больше не должна иметь возможность использовать IPv6. Иногда нужно бывает перезапустить машину или сервис *sysctl -p*.