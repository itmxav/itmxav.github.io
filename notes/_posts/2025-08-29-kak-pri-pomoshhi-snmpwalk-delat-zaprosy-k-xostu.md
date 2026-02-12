---
id: 3397
title: 'Как при помощи snmpwalk делать запросы к хосту?'
date: '2025-08-29T15:04:36+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3397'
permalink: /2025/08/29/kak-pri-pomoshhi-snmpwalk-delat-zaprosy-k-xostu/
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
    - '78'
wp_statistics_words_count:
    - '232'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Linux'
    - 'Записи про мониторинг'
tags:
    - linux
    - мониторинг
    - сети
format: false
---

Иногда бывает нужно проверить работы по SNMP c Linux. Сделать это можно через snmpwalk.   
1\. Установить snmpwalk можно так:  
Для Ubuntu / Debian / Linux Mint

```
[code lang="plain"]sudo apt-get update
sudo apt-get install snmp[/code]
```

Проверка:

```
[code lang="plain"]snmpwalk --version[/code]
```

Или для CentOS / RHEL / AlmaLinux / Rocky Linux (8 и выше)

```
[code lang="plain"]sudo yum install net-snmp-utils[/code]
```

или

```
[code lang="plain"]sudo dnf install net-snmp-utils[/code]
```

Проверка:

```
[code lang="plain"]snmpwalk -h[/code]
```

2\. Синтаксис следующий:

```
[code lang="plain"]snmpwalk -v <версия> -c <community> <хост> <OID>[/code]
Расшифровка:
[code lang="plain"]-v1/-v2c/-v3 - версия SNMP (1, 2c или 3)
-c <community> - ключ и указазания community string (например,public), используется в SNMPv1/v2c
<хост> - IP-адрес или имя хоста устройства
<OID> - Объектный идентификатор (например,1.3.6.1.2.1.1)
[/code]
```

3\. Примеры для -v1 и-v2c:

Получить всё

```
[code lang="plain"]snmpwalk -v1 -c "public" 192.168.1.1 .1[/code]
```

Запрос всех данных из MIB-II (стандартная ветвь)

```
[code lang="plain"]snmpwalk -v2c -c "public" 192.168.1.1 .1.3.6.1.2.1[/code]
```

Получить всё

```
[code lang="plain"]snmpwalk -v2c -c "public" 192.168.1.1 .1[/code]
```

или по OID:

```
[code lang="plain"]snmpwalk -v2c -c "public" 192.168.1.1 .1.3.6.1.2.1.1[/code]
```

4\. Использование SNMPv3  
Синтаксис:

```
[code lang="plain"]snmpwalk -v3 -u <username> -l authPriv -a SHA -A <auth_password> -x AES -X <priv_password> 192.168.1.1 .1[/code]
```

Где:

```
[code lang="plain"]-u — имя пользователя
-l — уровень безопасности: noAuthNoPriv, authNoPriv, authPriv
-a — алгоритм аутентификации (MD5, SHA)
-A — пароль аутентификации
-x — алгоритм шифрования (AES, DES)
-X — пароль шифрования[/code]
```

Пример с аутентификацией, но без шифрования трафика (authNoPriv):

```
[code lang="plain"]snmpwalk -v3 -u myuser -l authNoPriv -a SHA -A "myAuthPassword123" 192.168.1.1 .1[/code]
```

Тоже самое, но с MD5

```
[code lang="plain"]snmpwalk -v3 -u myuser -l authNoPriv -a MD5 -A "myAuthPassword123" 192.168.1.1 .1[/code]
```

Пример с аутентификацией и шифрованием трафика (authPriv):

```
[code lang="plain"]snmpwalk -v3 -u myuser -l authPriv -a SHA -A "myAuthPassword123" -x AES -X myPrivPassword456 192.168.1.1 .1[/code]
```