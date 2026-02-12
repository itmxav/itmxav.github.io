---
id: 3065
title: 'Как вывести виртуальную машину Proxmox из error state?'
date: '2024-10-07T12:00:33+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3065'
permalink: /2024/10/07/kak-vyvesti-virtualnuyu-mashinu-proxmox-iz-error-state/
views:
    - '44'
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
wp_statistics_words_count:
    - '29'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - Виртуализация
tags:
    - proxmox
format: false
---

Из-за различный ситуаций виртуальная машина, которая находится в общей HA-группе или нет, может улететь в ошибку. Чтобы изменить её состояние можно на узле сделать:

\[code lang="plain"\]ha-manager set vm:&lt;VMID&gt; --state disabled\[/code\]