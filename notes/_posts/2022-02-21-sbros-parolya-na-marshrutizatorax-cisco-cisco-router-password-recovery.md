---
id: 925
title: 'Сброс пароля на маршрутизаторах Cisco / Cisco Router Password Recovery'
date: '2022-02-21T17:54:02+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=925'
permalink: /2022/02/21/sbros-parolya-na-marshrutizatorax-cisco-cisco-router-password-recovery/
views:
    - '223'
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
    - 'Записи по Cisco'
tags:
    - cisco
    - сети
format: false
---

  
1\. Подключаем консольный кабель.  
2\. Выключаем по питанию.  
3\. Когда идет загрузка IOS отправляем сигнал прерывания Ctrl+Break.  
4\. Попадаем в rommon режим:

> `rommon 1 >`

5\. Меняем регистр комманд чтобы маршрутизатор не использовал конфиг во flash и перезагружаемся:

> `rommon 1 > confreg 0x2142<br></br>rommon 2 > reset`

6\. Переходим в привелегерованный режим и возвращаем конфигурацию:

> `Router> en<br></br>Router# copy startup-config running-config`

7\. Удаляем старый пароль и, если нужно, то делаем другие настройки:

> `R1(conf)# no enable secret`

8\. Устанавливаем новый пароль, возвращаем значение регистра и сохраняем конфигурацию:

> `R1(conf)# enable secret PASSWORD<br></br>R1(config)# config-register 0x2102<br></br>R1# copy runn start`

или

> `R1# wr mem`

9\. Можем перезагрузиться:

> `R1# reload`

\--

Источник - [wiki.merionet.ru](https://wiki.merionet.ru/ip-telephoniya/64/sbros-parolya-na-kommutatorax-i-marshrutizatorax-cisco/)