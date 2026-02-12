---
id: 3455
title: 'Отправка логов с Zelax 5054 в Syslog (Graylog)'
date: '2025-11-12T11:56:13+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3455'
permalink: /2025/11/12/otpravka-logov-s-zelax-5054-v-syslog-graylog/
views:
    - '92'
wp_statistics_words_count:
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
    - 'Записи по Zelax'
tags:
    - graylog
    - zelax
    - сети
format: false
---

В Zelax 5054 отправка логов настраивается через функцию info-center, поэтому не работает вариант:

```
[code lang="plain"]logging IP_ADDRESS level debugging[/code]
```

Настройка происходит иначе:  
1\. Переходим в нужный режим

```
[code lang="plain"]config t [/code]
```

2\. Включаем запись комманд (будут записываться локально и отправляться на сервер) и логирование входа

```
[code lang="plain"]logging executed-commands enable
authentication logging enable[/code]
```

3\. Указываем уровень логирования и куда отправлять логи

```
[code lang="plain"]info-center loghost 1 match level debugging 
info-center loghost 1 config IP_ADDRESS facility local7[/code]
```

4\. Включаем

```
[code lang="plain"]info-center loghost 1 output-enable[/code]
```

5\. Выходим режима и незабываем сохранять конфигурацию

```
[code lang="plain"]copy running-config startup-config[/code]
```