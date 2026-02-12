---
id: 2855
title: 'Zelax не отправляет логи в Graylog'
date: '2024-04-05T13:57:41+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2855'
permalink: /2024/04/05/zelax-ne-otpravlyaet-logi-v-graylog/
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
    - '99'
wp_statistics_words_count:
    - '224'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Zelax'
tags:
    - graylog
    - zelax
format: false
---

Наткнулся на ситуацию, когда логи с оборудования Zelax не появляются в Graylog.

Сначала надо настроить Zelax. В документации почему-то информация по настройке Syslog'а yt подходит и настраивается немного иначе:  
1\. Включаем info-center  
\[code lang="plain"\]info-center enable\[/code\]  
2\. Указываем источника для канала  
\[code lang="plain"\]info-center source debug level 7 prefix on channel 2\[/code\]  
Пояснения:

> level Х - уровень сообщений (0 - emergencies, 1 - alerts, 2 - critical, 3 - errors, 4 - warnings, 5 - notifications, 6 - informational, 7 - debugging);  
> channel X - номер канала, где часть каналов уже определена:  
> channel 0 - передача сообщений уровня debugging в консоль;  
> channel 1 - передача сообщений уровня debugging в терминальный монитор;  
> channel 2 - зарезервирован под передачу на Syslog-сервер;  
> channel 3 - передача debugging trap в буфер;  
> channel 4 - передача сообщений уровня warning в память (logsdram);  
> channel 5 - передача сообщений уровня critical в память (lognvram).

3\. Направляем вывод на сервер Graylog  
\[code lang="plain"\]info-center loghost IP\_ADDRESS facility local7 channel 2\[/code\]  
Пояснения:

> IP\_ADDRESS - адрес сервера;  
> facility - категория сообщения для сервера;  
> channel X - номер канала, который должен совпадать с предыдущей настройкой.

И, вроде, должно всё заработать. По анализатору трафика видно, что все пакеты доходят, но почему-то отображения логов нет.  
Момент заключается в том, что Graylog не обрабатывает полученные пакеты, пока в Zelax не будет установлены параметры времени.  
Настраиваем:

\[code lang="plain"\]ntp enable ntp server IP\_ADDRESS\_SERVER clock timezone MSK add 3 0\[/code\]

Странно. На Cisco, Huawei, Eltex, HPE таких моментов нет и Graylog сам фиксирует время, главное чтобы данные пришли, а здесь нет ?