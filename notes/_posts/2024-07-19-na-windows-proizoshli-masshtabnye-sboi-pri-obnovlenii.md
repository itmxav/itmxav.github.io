---
id: 2928
title: 'На Windows произошли масштабные сбои при обновлении'
date: '2024-07-19T13:25:46+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2928'
permalink: /2024/07/19/na-windows-proizoshli-masshtabnye-sboi-pri-obnovlenii/
views:
    - '41'
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
image: /wp-content/uploads/2024/02/Новости.jpg
categories:
    - 'Записи по Windows'
tags:
    - windows
    - Разное
format: false
---

По всему миру произошли масштабные сбои на компьютерах и серверах. Пока что винят ИБ-приложение CrowdStrike.

На Habr'е показывают [решение от производителя ПО](https://habr.com/ru/news/829912/):

> Workaround Steps:  
> 1\. Boot Windows into Safe Mode or the Windows Recovery Environment  
> 2\. Navigate to the C:\\Windows\\System32\\drivers\\CrowdStrike directory  
> 3\. Locate the file matching “C-00000291\*.sys”, and delete it.  
> 4\. Boot the host normally.

Если у кого-то ещё есть варианты решения проблемы, то пишите.

Вообще удивительно как какое-то такое ПО было установлено во многих местах и крайне мало кто знал про его существование. Может поэтому они отказались от Касперского? ?