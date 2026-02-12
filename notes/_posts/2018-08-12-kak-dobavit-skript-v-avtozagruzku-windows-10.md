---
id: 262
title: 'Как добавить скрипт в автозагрузку Windows 10?'
date: '2018-08-12T12:26:59+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=262'
permalink: /2018/08/12/kak-dobavit-skript-v-avtozagruzku-windows-10/
views:
    - '5110'
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
    - 'Записи по Windows'
tags:
    - windows
format: false
---

**Первый способ**Для того чтобы добавить скрипт в автозагрузку в Windows 10 необходимо: 1) Сделать ярлык к файлу скрипту 2) В проводнике прописать shell:startup и добавить в этой папке ярлык нашего скрипта на автозапуск. 3) Смотрим в автозапуске, есть ли наш скрипт там или нет. 4) Перезагружаемся и проверяем работу. **Второй способ**Если для запуска скрипта требуется права администратора, то необходимо сделать автозапуск через планировщик задач: 1) через поиск открывает планировщик задач 2) создаем новую простую задачу ![1](/wp-content/uploads/2018/08/1.png)3) называем задачу и в траггере ставим "При входе в Windows": ![2](/wp-content/uploads/2018/08/2.png)4) отмечаем, что запуск программы: ![3](/wp-content/uploads/2018/08/3.png)5) выбираем программу: ![4](/wp-content/uploads/2018/08/4.png)6) завершаем создание задачи 7) правой кнопкой мыши кликаем по задаче и выбираем свойства. Во вкладке "Общее" ставим галочку "Выполнить с наивысшими правами" и применяем изменения ![5](/wp-content/uploads/2018/08/5.png)8) перезагружаем компьютер и проверяем работу скрипта.