---
id: 3068
title: 'Как перейти в chroot и запустить инициализацию Linux?'
date: '2024-10-07T12:53:49+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3068'
permalink: /2024/10/07/kak-perejti-v-chroot-i-zapustit-inicializaciyu-linux/
views:
    - '48'
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
    - 'Записи по Linux'
tags:
    - linux
format: false
---

Когда ломается система на Linux и зависает при загрузке, то иногда полезно попробовать запуститься через chroot и посмотреть на каком шаге всё ломается при загрузке.  
1\. Запускаемся с Live-CD сервер.  
2\. Монтируем нужный раздел, посмотрев всё предварительно через blkid, fdisk -l. Например, sda2

```
[code lang="plain"]mount /dev/sda2 /путь/к/точке/монтирования[/code]
```

2\. Создаем временную папку, которая будет новым корнем и заходим в нее

```
[code lang="plain"]# mkdir /путь/к/новому/корню; cd /путь/к/новому/корню[/code]
```

  
3\. Мониторуем каталоги для chroot

```
[code lang="plain"]# mount -t proc proc proc/
# mount -t sysfs /sys sys/
# mount --rbind /dev dev/[/code]
```

Дополнительна информация:  
Если нужен раздел run, то можно примонтировать вот так

```
[code lang="plain"]mount --rbind /run run/[/code]
```

Если у есть UEFI, то надо примонтировать ещё

```
[code lang="plain"]mount --rbind /sys/firmware/efi/efivars sys/firmware/efi/efivars/[/code]
```

Для работы по сети копируем resolv.conf

```
[code lang="plain"]cp /etc/resolv.conf etc/resolv.conf[/code]
```

4\. Пробуем зайти в оболочку

```
[code lang="plain"]chroot /путь/к/новому/корню /bin/bash[/code]
```

5\. Запускаем инициализацию/

```
[code lang="plain"]make-initrd --kernel=`uname -r`[/code]
```

  
или можно полный путь указать к ядру вместо `uname -r`.

Чтобы всё размонтировать

```
[code lang="plain"]umount --recursive /путь/к/новому/корню[/code]
```