---
id: 3074
title: 'Как включить fastboot при загрузке в Linux?'
date: '2024-10-07T13:20:06+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3074'
permalink: /2024/10/07/kak-vklyuchit-fastboot-pri-zagruzke-v-linux/
views:
    - '77'
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

Иногда бывают ситуации когда при загрузке нужно быстрее управление ОС. Например, проигнорировать тестирование разных устройств перед загрузкой. Это можно сделать добавив в GRUB параметр fastboot.  
1\. В процессе загрузки GRUB нажимает "e"  
2\. Ищем строчку наподобие

```
[code lang="plain"]linux /boot/vmlinuz root=UUID=..... panic=30 splash[/code]
```

  
3\. В конце через пробел добавляем fastboot

```
[code lang="plain"]linux /boot/vmlinuz root=UUID=..... panic=30 splash fastboot[/code]
```

4\. Загружаемся