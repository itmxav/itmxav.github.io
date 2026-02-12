---
id: 3278
title: 'Как установить терминальный сервер X2Go на Debian?'
date: '2025-02-07T00:21:19+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3278'
permalink: /2025/02/07/kak-ustanovit-terminalnyj-server-x2go-na-debian/
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
    - '91'
image: /wp-content/uploads/2025/02/x2go_mini.jpg
categories:
    - 'Debian, Ubuntu etc.'
tags:
    - debian
    - linux
    - x2go
format: false
---

Для работы с терминальным сервером необходимо на серверной стороне устновить среду и серверную часть x2go. В качестве среды будет использоваться XFCE:   
1\. Можно установить базовый набор пакетов:

> sudo apt-get install xfce4

  
Или полный (включает текстовый редактор, веб-браузер и т.д.)  
> sudo apt-get install task-xfce-desktop

  
2. Далее ставим X2Go  
> sudo apt-get install x2goserver x2goserver-xsession

  
Базовых параметров достаточно.  
3. Переходим на клиентскую машину. В качестве примера машина с дистрибутивом debian-base  
> sudo apt-get install x2goclient

  
Подробнее про клиента можно почитать [в документации](http://wiki.x2go.org/doku.php/download:start)  
4. Запускаем клиент. Создаем новую сессию, вводим адрес сервера, имя пользователя, порт SSH, указываем в типе сессии XFCE и подключаемся.  
При успешном подключении откроется рабочий стол.   
Далее в клиенте, в настройке сессии, можно подобрать вручную настройки для более удобной работы, если это необходимо. Видео на Youtube:

<iframe allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen="" frameborder="0" height="220" referrerpolicy="strict-origin-when-cross-origin" src="https://www.youtube.com/embed/n7_E-QTrRjg" title="Как установить терминальный сервер X2Go на Debian? [FastHowTo]" width="330"></iframe>

Видео на Rutube:

<iframe allow="clipboard-write; autoplay" allowfullscreen="" frameborder="0" height="220" mozallowfullscreen="" src="https://rutube.ru/play/embed/6da35879a1af0875da4fe96473aa8357" webkitallowfullscreen="" width="330"></iframe>