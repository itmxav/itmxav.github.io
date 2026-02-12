---
id: 2787
title: 'Вылетел и не поднимается OSD в Ceph+Proxmox'
date: '2024-03-12T22:31:26+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2787'
permalink: /2024/03/12/vyletel-i-ne-podnimaetsya-osd-v-cephproxmox/
views:
    - '66'
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
    - ceph
    - proxmox
format: false
---

Столкнулся с ситуацией, что один OSD в Ceph вылетел, хотя сам диск виден. После выяснения обстоятельств оказалось, что человек случайно ногой зацепил диск в стойке, когда менял провода, и потом вставил его назад. Ceph работает в связке с Proxmox. Попытки поднять OSD оказывались печалью и путь /dev/sdX, после возвращения диска, изменился на другой.  
Т.к. ресурсы были, то можно было пойти «стандартным» маршрутом пересоздания OSD:

1\. Диск отмечен как Out.  
2\. Удаляем OSD. В разделе Ceph(главное не ошибиться с OSD)→More→Destroy  
3\. Далее выбираем узел → Disks→Выбираем нужный диск и стираем его «Wipe Disk»  
4\. После в разделе Ceph добавляем диск как новый OSD.  
Естественно, будет перебалансировка ресурсов в фоне.