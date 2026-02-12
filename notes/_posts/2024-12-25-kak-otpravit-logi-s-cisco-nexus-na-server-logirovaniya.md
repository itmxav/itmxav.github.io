---
id: 3195
title: 'Как отправить логи с Cisco Nexus на сервер логирования?'
date: '2024-12-25T11:40:41+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3195'
permalink: /2024/12/25/kak-otpravit-logi-s-cisco-nexus-na-server-logirovaniya/
views:
    - '44'
wp_statistics_words_count:
    - '123'
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

Система NXOS отличается от IOS. Настройка отправки логов на сервер логирования в Cisco Nexus происходит иначе:

1\. Указываем, что надо отправлять логи на сервер

```
[code lang="plain"]logging server 192.168.0.1 6 use-vrf default facility syslog[/code]
```

*192.168.0.1* - пример IP-адреса сервера логирования  
*6* - это уровень логов, которые надо отправлять  
*use-vrf default* - VRF по умолчанию. Если вы на Nexus настраивали что-то с VRF, то надо это учитывать.   
*facility syslog* - объект, который будет использоваться для отправки логов

2\. Указываем через какой интерфейс (например, 1/16) будут отправляться логи:

```
[code lang="plain"]logging source-interface Ethernet1/16[/code]
```

3\. Дополнительная конфигурация. Устанавливаем отправку команд в aaa на уровне 6, чтобы записи отправлялись на сервер логирования:

```
[code lang="plain"]logging level aaa 6[/code]
```

4\. Проверяем логи на сервере логирования через систему логирования и tcpdump/wireshark, что логи доходят. Сохраняем текущий конфиг в startup-config:

```
[code lang="plain"]copy running-config startup-config[/code]
```