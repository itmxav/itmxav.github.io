---
id: 3045
title: 'Как заблокировать трафик от определенного MAC на Cisco'
date: '2024-10-03T16:49:01+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3045'
permalink: /2024/10/03/kak-zablokirovat-trafik-ot-opredelennogo-mac-na-cisco/
views:
    - '79'
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
    - 'Записи по Cisco'
tags:
    - cisco
    - сети
format: false
---

Иногда надо заблокировать трафик от определенного MAC на Сisco, особенно если там DHCP крутится.  
Можно сделать это следующим образом:  
1\. Переходим в нужный режим на Cisco и создаем ACL с указанием MAC  
\[code lang="plain"\]conf t mac access-list extended MACL deny any host FFFF.FFFF.FFFF permit any exit\[/code\]   
2\. Вешаем ACL на нужный порт   
\[code lang="plain"\]interface fastEthernet 0/1 mac access-group MACL in\[/code\]