---
id: 3307
title: 'Как подключиться по OpenVPN через терминал на Linux не вводя логин и пароль?'
date: '2025-04-02T12:08:22+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3307'
permalink: /2025/04/02/kak-podklyuchitsya-po-openvpn-cherez-terminal-na-linux-ne-vvodya-login-i-parol/
views:
    - '38'
wp_statistics_words_count:
    - '94'
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
    - vpn
format: false
---

Здесь нет информации по настройке VPN для обхода блокировок 😊   
Иногда хочется пропустить момент с вводом пароля при установлении соединения к компьютерной сети по OpenVPN через терминал для решения своих рабочих задач. Вариант решения может быть такой:  
1\. Создается текстовый файл под нужным пользователем

> touch passw

и в него записываются в каждой строке  
> Login  
> Password

2. Файлу выставляются права только на чтения  
> chmod 400 passw

3. В файле .ovpn устанавливаются нужны параметры. Добавляем или изменяем параметр auth-user-pass и указываем путь к файлу:  
> auth-user-pass /path/to/file/passw

Пишут, что можно ещё вот такую конструкцию добавить, но не проверял  
> &lt;auth-user-pass&gt;  
> LoginPassword  
> &lt;/auth-user-pass&gt;

4. Далее через терминал осуществляется установка соединения  
> sudo openvpn --config YOUR\_FILE.ovpn