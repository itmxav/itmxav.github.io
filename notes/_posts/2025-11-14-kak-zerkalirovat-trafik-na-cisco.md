---
id: 3457
title: 'Как зеркалировать трафик на Cisco?'
date: '2025-11-14T11:49:05+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3457'
permalink: /2025/11/14/kak-zerkalirovat-trafik-na-cisco/
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
    - '72'
wp_statistics_words_count:
    - '213'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Cisco'
tags:
    - cisco
    - сети
format: false
---

Иногда для диагностики ситуации надо получить дамп трафика, а для этого требуется его зеркалировать на Cisco.

**SPAN (Switch Port Analyzer)**  
Чтобы просто зеркалировать трафик на одном коммутаторе надо определить на какой порт будет идти зеркальный трафик, этот порт должен быть ненастроенный, и откуда отправлять трафик.  
1\. Пример конфига куда будет зеркалироваться трафик:

```
[code lang="plain"]!
interface GigabitEthernet1/0/40
![/code]
```

2\. Далее определяем откуда будет зеркалироваться трафик:

```
[code lang="plain"]switch(config)# monitor session 1 source interface Te1/1/1[/code]
```

Если надо несколько портов, то

```
[code lang="plain"]switch(config)# monitor session 1 source interface Te1/1/1 - 2[/code]
```

или

```
[code lang="plain"]switch(config)# monitor session 1 source interface GigabitEthernet1/0/25 - 26 , gigabitEthernet 1/0/29[/code]
```

3\. Указываем куда зеркалировать:

```
[code lang="plain"]switch(config)# monitor session 1 destination interface Gi1/0/40[/code]
```

**RSPAN (Remote Switch Port Analyzer)**

Может возникнуть ситуация, когда надо сделать удаленно зеркалирование трафика с vlan одного коммутатора (switch1) на порт другого коммутатора (switch2) и эти коммутаторы соединены через trunk.  
Например, надо зеркалировать трафик с switch1 vlan 11 на 5 порт switch2. Настраивается так:  
1\. На switch1 и switch2 поднимает vlan 77 для зеркалирования:

```
[code lang="plain"]switch1(config)# vlan 77
switch1(config-vlan)# remote-span
switch2(config)# vlan 77
switch2(config-vlan)# remote-span[/code]
```

2\. На switch1 указываем откуда и куда надо зеркалировать трафик

```
[code lang="plain"]switch1(config)# monitor session 1 source vlan 11
switch1(config)# monitor session 1 destination remote vlan 77[/code]
```

3\. На switch2 указываем откуда и куда надо зеркалировать трафик

```
[code lang="plain"] switch2(config)# monitor session 1 source remote vlan 77
switch2(config)# monitor session 1 destination interface Gi0/5[/code]
```

Не забываем сохранить конфиг и снимаем трафик, например, с помощью Wireshark.