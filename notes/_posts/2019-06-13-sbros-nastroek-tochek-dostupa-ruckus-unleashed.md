---
id: 634
title: 'Сброс настроек точек доступа Ruckus Unleashed'
date: '2019-06-13T15:04:38+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=634'
permalink: /2019/06/13/sbros-nastroek-tochek-dostupa-ruckus-unleashed/
views:
    - '587'
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
image: /wp-content/uploads/2018/09/data.png
categories:
    - 'Записи по сетям'
tags:
    - сети
format: false
---

**1 способ - кнопка Reset**1. Сзади оборудования есть кнопка Reset. 2. Нажимаем на нее и удерживаем 10 секунд и отпускам. 3. Светодиод PWR засветиться красным. 4. Дожидаемся загрузки точки доступа. **2 способ - Web-интерфейс**1. Надо перейти в Admin &amp; Services - Administer - Backup &amp; Restore 2. Выбрать Restore to Factory Setting и нажать Ok. После этого появится прогресс-бар. 3. Надо дождаться завершения сброса конфигурации. **3 способ - SSH**1. Подключаемся по SSH и вводим логин c паролем (по умолчанию - super / sp-admin) 2. После того как попали в командную строку, вводим set factory и Enter 3. Далее набиваем reboot и Enter 4. Дожидаемся перезагрузки точки доступа