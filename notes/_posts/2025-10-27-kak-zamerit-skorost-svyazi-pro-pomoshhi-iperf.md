---
id: 3428
title: 'Как замерить скорость связи при помощи iperf?'
date: '2025-10-27T14:25:31+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3428'
permalink: /2025/10/27/kak-zamerit-skorost-svyazi-pro-pomoshhi-iperf/
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
    - '175'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Linux'
    - 'Записи по сетям'
tags:
    - linux
    - сети
format: false
---

1\. Установка на Debian/Ubuntu:

```
[code lang="plain"]sudo apt-get update
sudo apt-get install iperf[/code]
```

Или RHEL/CentOS/Fedora:

```
[code lang="plain"]sudo yum install epel-release -y
sudo yum install iperf [/code]
```

Если нужно iperf3 (3 и 2 версии несовместимы)

```
[code lang="plain"]sudo yum install epel-release -y[/code]
```

Установка iperf3

```
[code lang="plain"]sudo yum install iperf3 -y[/code]
```

Для CentOS 8+ / Rocky Linux:

```
[code lang="plain"]sudo dnf install iperf3 -y[/code]
```

Для Debian/Ubuntu:

```
[code lang="plain"]sudo apt-get update
sudo apt-get install iperf3 -y[/code]
```

2\. Если есть файервол, то для iperf необходимо открыть порт 5001. Для iperf3 5201.

3\. Запускаем на сервере:

```
[code lang="plain"]iperf -s[/code]
```

или

```
[code lang="plain"]iperf3 -s[/code]
```

Если надо указать порт или IP

```
[code lang="plain"]iperf3 -s -B 192.168.1.2 
iperf3 -s -p 5001 [/code]
```

4\. Запускаем на клиенте

```
[code lang="plain"]iperf -c IP-адрес[/code]
```

или

```
[code lang="plain"]iperf3 -c IP-адрес[/code]
```

Дополнительные опции:

```
[code lang="plain"]iperf3 -c IP-адрес -t 20 # тест 20 секунд
iperf3 -c IP-адрес -P 3 # 3 параллельных потока
iperf3 -c IP-адрес -R # обратное направление (сервер → клиент)[/code]
```

Пример вывода для TCP:

```
[code lang="plain"][ ID] Interval Transfer Bandwidth
[ 1] 0.0000-10.0066 sec 10.9 GBytes 9.39 Gbits/sec[/code]
```

5\. Если надо протестировать UDP, то:

```
[code lang="plain"]iperf -c IP-адрес -u -b 100M[/code]
```

или

```
[code lang="plain"]iperf3 -c IP-адрес -u -b 100M[/code]
```

> -u — использовать UDP  
> -b 100M — пропускная способность (100 Мбит/с). Без этого UDP значительно слабее.