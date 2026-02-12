---
id: 2888
title: 'Как заблокировать сайты на Squid?'
date: '2024-05-27T14:29:03+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2888'
permalink: /2024/05/27/kak-zablokirovat-sajty-na-squid/
views:
    - '59'
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
    - 'Записи по сетям'
tags:
    - linux
    - сети
format: false
---

Чтобы заблокировать сайты на прокси со Squid надо:  
1\. Создать список с сайтами для блокировки  
\[code lang="plain"\]nano /etc/squid/blacklistsites\[/code\]  
или  
\[code lang="plain"\]nano /etc/squid3/blacklistwebsites\[/code\]  
2\. Добавляем сайты в список. Например:  
\[code lang="plain"\]site1\\.ru site2\\.ru\[/code\]  
Т.к. работа будет происходить по регулярным выражениям,то точку надо экранировать  
3\. В начале acl'ов указываем каким адресам надо проверять список. В данном примере 10 сети:  
\[code lang="plain"\]acl url\_filtred src 10.0.0.0/8\[/code\]  
и ниже указываем сам пуст к списку:   
\[code lang="plain"\]acl blacklistsites url\_regex -i "/etc/squid/blacklistwebsites"\[/code\]  
4\. Перед всеми http\_access указываем, что надо блокировать соединения из списка:  
\[code lang="plain"\]http\_access deny blacklistsites url\_filtred\[/code\]  
5\. Проверяем конфиг:   
\[code lang="plain"\]squid -k parse\[/code\]  
6\. Если всё хорошо, то перечитываем конфигурационный файл без остановки Squid:  
\[code lang="plain"\]squid -k reconfigure\[/code\]