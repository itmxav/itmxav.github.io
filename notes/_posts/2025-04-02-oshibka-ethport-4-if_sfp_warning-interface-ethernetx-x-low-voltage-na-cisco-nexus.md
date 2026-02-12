---
id: 3312
title: 'Ошибка %ETHPORT-4-IF_SFP_WARNING: Interface EthernetX/X, Low Voltage на Cisco Nexus'
date: '2025-04-02T12:30:41+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3312'
permalink: /2025/04/02/oshibka-ethport-4-if_sfp_warning-interface-ethernetx-x-low-voltage-na-cisco-nexus/
views:
    - '34'
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
format: false
---

Ошибка %ETHPORT-4-IF\_SFP\_WARNING: Interface EthernetХ/Х, Low Voltage Warning cleared на коммутаторе Cisco Nexus указывает на то, что c модулем SFP или QSFP на интерфейсе EthernetX/X были проблемы с напряжением (оно было низким), но потом они решились.

Если подробнее посмотреть на сообщение то:  
%ETHPORT-4-IF\_SFP\_WARNING - код ошибки и уровень важности. Уровень 4 обычно означает предупреждение (warning);  
Interface EthernetХ/Х - указывает на конкретный интерфейс, где произошла проблема;  
Low Voltage Warning cleared - означает, что предупреждение о низком напряжении было снято, т.е. ситуация нормализовалась.

В любом случае сообщение говорит о том, что модуль SFP/QSFP может работать некорректно при низком напряжении. Причины могут быть разные:  
\- модуль SFP/QSFP неправильно подключен или поврежден;  
\- проблемы с питанием на самом коммутаторе;  
\- проблемы с кабелем или соединением.

Т.к. проблема была снята (судя по сообщению), то это была временная проблема. Если такое повторяется, то необходимо дополнительно понаблюдать за тем что происходило в этот период времени. Варианты проверок:  
\- проверить, что модуль правильно подключен и не поврежден;  
\- попробовать заменить модуль на новый, чтобы исключить его как источник проблемы;  
\- проверьте физическое подключение (вдруг кто-то криворукий подключал): проверить, что кабель правильно подключен и не поврежден; проверьте состояние соседнего порта, если оно есть;  
\- проверить блоки питания коммутатора. Вдруг какой-то вышел из строя;  
\- посмотреть логи и статус интерфейса :

> show interface EthernetХ/Х - информации о состоянии интерфейса;  
> show logging - просмотре всех логов;  
> show interface transceiver detail - состояние SFP/QSFP.