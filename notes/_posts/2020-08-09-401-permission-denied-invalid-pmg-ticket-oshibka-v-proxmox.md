---
id: 756
title: '401 permission denied &#8212; invalid PMG ticket. Ошибка в Proxmox'
date: '2020-08-09T21:07:59+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=756'
permalink: /2020/08/09/401-permission-denied-invalid-pmg-ticket-oshibka-v-proxmox/
views:
    - '1290'
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
    - Виртуализация
tags:
    - linux
    - proxmox
format: false
---

Иногда в кластере на узлах Proxmox может появится такая ошибка:

> `401 permission denied - invalid PMG ticket`

Часто она возникает из-за некорректного время на узлах (что влияет на корректность работы ticket'ов). Поэтому надо поверить время на узлах, связь с NTP-сервером и синхронизировать все узлы.