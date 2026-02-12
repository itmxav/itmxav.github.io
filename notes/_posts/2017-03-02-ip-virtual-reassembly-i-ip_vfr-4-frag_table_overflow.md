---
id: 34
title: 'ip virtual-reassembly и IP_VFR-4-FRAG_TABLE_OVERFLOW'
date: '2017-03-02T21:04:04+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=34'
permalink: /2017/03/02/ip-virtual-reassembly-i-ip_vfr-4-frag_table_overflow/
views:
    - '1550'
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
image: /wp-content/uploads/2017/03/12313.png
categories:
    - 'Записи по Cisco'
tags:
    - cisco
    - сети
format: false
---

> Копипаст [этой статьи](http://sergeyn.blogspot.ru/2009/03/ipvfr-4-fragtableoverflow.html) дабы не потерять инфу.

IP\_VFR-4-FRAG\_TABLE\_OVERFLOW и ip virtual-reassembly Mar 20 11:48:14 192.168.20.10 832: Mar 20 08:48:13.629: %IP\_VFR-4-FRAG\_TABLE\_OVERFLOW: GigabitEthernet0/1: the fragment table has reached its maximum threshold 64 Mar 20 11:48:32 192.168.20.10 833: Mar 20 08:48:31.437: %IP\_VFR-4-TOO\_MANY\_FRAGMENTS: GigabitEthernet0/1: Too many fragments per datagram (more than 32) - sent by \*.\*.\*.\*, destined to \*.\*.\*.\* %IP\_VFR-4-FRAG\_TABLE\_OVERFLOW : \[chars\]: the fragment table has reached its maximum threshold \[dec\] Explanation: The number of datagrams being reassembled at any one time has reached it maximum limit. Recommended Action: Increase the maximum number of datagrams that can be reassembled by entering the ip virtual-reassembly max-reassemblies number command, with number being the maximum number of datagrams that can be reassembled at any one time. т.е. количество датаграмм, собранных за промежуток времени, достигло максимального лимита Рекомендуемые действия: увеличить максимальное число датаграмм которые могут быть собраны, путем ввода команды ip virtual-reassembly с числом максимального количества датаграмм, которые могут быть собраны в промежуток времени. Небольшое пояснение: IP пакеты фрагменируются и буферизруются маршрутизатором, до тех пор пока не соберутся в датаграмму и в конце концов не передадутся. Маршрутизатор распределяет пространство для количества датаграмм (и фрагментов на датаграмму) которые ждут сборки. Вы можете увеличить размер таблицы фрагменов, но так же стоит выяснить что вызывает фрагментацию. Это могут быть значения MTU, действия злоумышленника с целью забить всю память фрагментами пакетов или не корректной настройкой оборудования. выдержка из документации с cisco.com по синтаксису команды ip virtual-reassembly: Что бы включить сборку виртуальных фрагментов (VFR) на интерфейсе, используйте команду ip virtual-reassembly в режиме конфигурации интерфейса. Что бы отключить VFR нужно использовать no с это командой. синтаксис: ip virtual-reassembly \[max-reassemblies number\] \[max-fragments number\] \[timeout seconds\] \[drop-fragments\] no ip virtual-reassembly \[max-reassemblies number\] \[max-fragments number\] \[timeout seconds\] \[drop-fragments\] max-reassemblies number: (Опционально) Максимальное количество IP датаграмм, которые могут быть собраны в заданное время. Значение по умолчанию: 16. Если достигнуто максимальное значение, то все последующие фрагменты будут отбрасываться и в системный журнал будут отправлены тревожные сообщения. max-fragments number: (Опционально) Максимальное количество фрагментов на одну IP датаграмму (фрагмент). Значение по умолчанию: 32. Если собирающаяся IP датаграмма получает больше максимального числа разрешенных фрагментов, то IP датаграмма будет отброшена и в системный журнал будет отправлено тревожное сообщение. timeout seconds: (Опционально) значение таймаута в секундах для сборки IP датаграммы. Значение по умолчанию: 3. Если IP датаграмма не получит все фрагменты в установленное время, то IP датаграмма (и все ее фрагменты) будет отброшена. drop-fragments: (Опционально) Включает функцию VFR отбрасывать все пакеты, которые приходят на сконфигурированный интерфейс. По умолчанию эта функция отключена. Использование: Когда злоумышленник продолжительное время посылает большое количество дефектных пакетов, может быть осуществлена атака переполнения буфера. Firewall теряет время и память когда пытается пересобрать фейковые пакеты. Опции max-reassemblies и max-fragments позволяют вам сконфигурировать максимальные пороговые значения, и предотвратить атаку переполнения буфера и контролировать потребление потребление памяти. В дополнение к конфигурированию максимальных пороговых значений, каждая IP датаграмма ассоциируется с управляемым таймером. Если IP датаграмма не получит все фрагменты через указанный период (который можно установить опцией timeout), время истечет и IP датаграмма (со всеми фрагментами) будет отброшена. Автоматическое включение и выключение VFR: VFR реализована для работы с любой функцией которая использует сборку фрагментов (таких как Cisco IOS firewall и NAT). В данный момент NAT включает и выключает VFR автоматически. т.е. когда NAT включен на интерфейсе, то на этом интерфейсе автоматически включена VFR. Если более чем одна функция пытается автоматически включить VFR на интерфейсе, VFR начинает вести учет функций использующих его, и когда это количество становится равным нулю - он автоматически отключается.