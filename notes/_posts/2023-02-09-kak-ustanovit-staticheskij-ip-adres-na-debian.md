---
id: 2121
title: 'Как установить статический IP-адрес на Debian?'
date: '2023-02-09T23:09:52+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=2121'
permalink: /2023/02/09/kak-ustanovit-staticheskij-ip-adres-na-debian/
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
views:
    - '460'
image: /wp-content/uploads/2023/02/Надпись-1.png
categories:
    - 'Debian, Ubuntu etc.'
tags:
    - debian
    - linux
    - сети
format: false
---

1\. Открыть   
\[code lang="plain"\]nano /etc/network/interfaces&lt;/p&gt;\[/code\]

2\. Прописать   
\[code lang="plain"\]iface &lt;сетевой интерфейс&gt; inet static address &lt;IP-адрес&gt; netmask &lt;маска сети&gt; gateway &lt;адрес шлюза&gt; dns-nameservers &lt;адрес dns&gt;\[/code\]

3\. Сохраниться и перезагрузиться. Можно перезапустить сервис networking, но он не всегда нормально отрабатывает.

Видео:

<iframe allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen="" frameborder="0" height="220" src="https://www.youtube.com/embed/k62YFEF6xYM" title="Как установить статический IP-адрес на Debian?" width="330"></iframe>