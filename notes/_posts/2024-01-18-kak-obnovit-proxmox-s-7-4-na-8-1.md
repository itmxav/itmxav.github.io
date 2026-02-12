---
id: 2536
title: 'Как обновить Proxmox с 7.4 на 8.1?'
date: '2024-01-18T21:01:49+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2536'
permalink: /2024/01/18/kak-obnovit-proxmox-s-7-4-na-8-1/
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
    - '316'
image: /wp-content/uploads/2024/01/Надпись-2.jpg
categories:
    - Виртуализация
tags:
    - proxmox
format: false
---

*Если используется Ceph, то читайте процесс обновления [здесь](https://pve.proxmox.com/wiki/Upgrade_from_7_to_8#Actions_step-by-step). Желательно выключить все машины перед обновлением, на всякий случай.*

1.Выключаем pve-enterprise.list через комментирование

\[code lang="plain"\]# nano /etc/apt/sources.list.d/pve-enterprise.list #deb https://enterprise.proxmox.com/debian/pve bookworm pve-enterprise\[/code\]

2\. Обновляем нашу ветку

\[code lang="plain"\]# apt update; apt dist-upgrade \[/code\]

3\. Добавляем репозиторий pve-no-subscription

\[code lang="plain"\]deb http://download.proxmox.com/debian bullseye pve-no-subscription\[/code\]

4\. Прогоняем

\[code lang="plain"\]# apt update\[/code\]

5\. Проверяем всё ли нормально для перехода на 8 версию через запуск специального скрипта.

\[code lang="plain"\]# pve7to8\[/code\]

6\. Если есть ошибки, то исправляем. Если нет, то бэкапил sources.list и меняем на новую версию репозитории Debian 12 bookworm, т.к. 8 версия на её основе сделана.

\[code lang="plain"\]# cp /etc/apt/sources.list /etc/apt/sources.list.bak # sed -i 's/bullseye/bookworm/g' /etc/apt/sources.list\[/code\]

7\. Смотрим список обновления

\[code lang="plain"\]# apt list --upgradable\[/code\]

8\. Обновляемся и смотрим, что получилось.

\[code lang="plain"\]# apt dist-upgrade\[/code\]

Видео:

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="220" src="https://www.youtube.com/embed/u6KKbU_Id0o  " title="Как обновить Proxmox с 7.4 на 8.1?" width="330"></iframe>