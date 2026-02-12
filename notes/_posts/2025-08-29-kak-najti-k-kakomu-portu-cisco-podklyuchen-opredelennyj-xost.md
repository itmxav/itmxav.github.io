---
id: 3389
title: 'Как найти к какому порту Cisco подключен определенный хост?'
date: '2025-08-29T12:14:47+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3389'
permalink: /2025/08/29/kak-najti-k-kakomu-portu-cisco-podklyuchen-opredelennyj-xost/
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
    - '31'
wp_statistics_words_count:
    - '285'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Cisco'
tags:
    - cisco
    - сети
format: false
---

Иногда бывают ситуации когда надо определить к какому порту Cisco подключен определенный хост. Сделать можно так:

Возможно, есть цепочка коммутаторов, поэтому надо сначала пингануть чтобы сформировалась актуальная MAC-таблица:  
1\. Пингуем

```
[code lang="plain"]# ping 192.168.1.11[/code]
```

2\. Далее определяем MAC по IP

```
[code lang="plain"]# show arp | include 192.168.1.11 [/code]
```

или

```
[code lang="plain"]# show arp | beg 192.168.1.11[/code]
```

3\. Смотрим по таблице к какому порту этот MAC относится

```
[code lang="plain"]# show mac-address-table address xxxx.xxxx.xxxx[/code]
```

или

```
[code lang="plain"]# show mac address-table address xxxx.xxxx.xxxx[/code]
```

4\. Если указан PortChannel, то смотри какие порты входят в него, если номер 1:

```
[code lang="plain"]show etherchannel 1 summary[/code]
```

или

```
[code lang="plain"]show etherchannel summary[/code]
```

4.1 Самое просто, но может создать проблемы временное отключение портов по одному чтобы понять на какой из них исчезнет MAC.  
4.2 Или применить команду *test etherchannel load-balance*, но сначала надо понять на основе чего идет балансировка. Выполняем:

```
[code lang="plain"]show etherchannel load-balance[/code]
```

и видим результат

```
[code lang="plain"]Load-balancing on Port-channels configured globally:
src-mac[/code]
```

или

```
[code lang="plain"]src-dst-ip - балансировка по IP источника и назначения 
src-ip - IP источника
dst-mac - MAC назначения[/code]
```

Вообще *test etherchannel load-balance* - диагностическая команда Cisco, которая не влияет на реальный трафик, а имитирует алгоритм балансировки EtherChannel (LACP/PAgP), чтобы определить, какой физический порт в составе Port-channel будет использован для передачи трафика с заданными параметрами. Она симулирует процесс выбора порта в агрегированном канале на основе указанных параметров: текущей политики балансировки, указанных MAC-адресов источника и назначения, и номера Port-channel.

4.3 Если src-mac, то балансировка по MAC-адресам источника

```
[code lang="plain"]test etherchannel load-balance interface port-channel 1 mac-source xxxx.xxxx.xxxx mac-dest ffff.ffff.ffff[/code]
```

Пример результата

```
[code lang="plain"]Would select interface GigabitEthernet1/0/2[/code]
```

Для src-dst-ip

```
[code lang="plain"]test etherchannel load-balance interface port-channel 1 ip-source 192.168.1.11 ip-dest 192.168.1.1[/code]
```

! !Если используется src-dst-ip, то результат test команды должен включать IP-адреса.

Другие варианты:

```
[code lang="plain"]src-ip - test etherchannel ... ip-source 192.168.1.11
dst-mac - test etherchannel ... mac-dest aaaa.bbbb.cccc[/code]
```

5\. Если коммутатор не конечный, то смотрим через CDP какой следующий:

```
[code lang="plain"]show cdp neighbors GiX/X/X detail[/code]
```

Переходим на следующий коммутатор и повторяем шаги.