---
id: 140
title: 'Установка zabbix-agent на windows'
date: '2018-01-07T16:03:09+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=140'
permalink: /2018/01/07/ustanovka-zabbix-agent-na-windows/
views:
    - '225'
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
image: /wp-content/uploads/2017/09/1000px-Server-monitoring.svg_.png
categories:
    - 'Записи про мониторинг'
tags:
    - windows
    - zabbix
    - мониторинг
format: false
---

Качаем нужного нам агента [здесь](https://www.zabbix.com/ru/download). Далее создаем папку например С:/zabbix\_agent и копируем туда файлы согласно разрядности системы из подпапки bin, скаченного архива + копируем конфиг из папки conf. Открывает файл конфига и редактируем его:

> `LogType=fileLogFile=С:/zabbix_agent/zabbix_agentd.logLogFileSize=13DebugLevel=3Server=[адрес сервера,где стоит Zabbix]ListenPort=10050SeverActive=[адрес сервера,где стоит Zabbix]Hostname=[Полное имя компа]`

Сохраняем! Далее переименовываем файл конфига в zabbix-agentd.conf и открываем командную строки под Администратором (два тире перед config и install): > `C:> "c:/zabbix_agent/zabbix_agentd.exe" --config "c:/zabbix_agent/zabbix_agentd.conf" --install`

После этого должны появиться две надписи: > `service [Zabbix Agent] installed successfullyevent source [Zabbix Agent] installed successfully`

Удаление: > `C:> "c:/zabbix_agent/zabbix_agentd.exe" --config "c:/zabbix_agent/zabbix_agentd.conf" --uninstall`

После этого должны появиться две надписи: > `service [Zabbix Agent] uninstalled successfullyevent source [Zabbix Agent] uninstalled successfully`

Запускаем агента (два тире перед config и start): > `C:> "c:/zabbix_agent/zabbix_agentd.exe" --config "c:/zabbix_agent/zabbix_agentd.conf" --start`

Остановка: > `C:> "c:/zabbix_agent/zabbix_agentd.exe" --config "c:/zabbix_agent/zabbix_agentd.conf" --stop`

После этого надо посмотреть в службах, что появился zabbix agent и он работает. Заходим в настройка брандмауэра во вкладку "Разрешить взаимодействия с приложением или компонентом в брандмауэре Windows"-&gt; добавляем нашего zabbix\_agentd и ставим нужные галочки. Далее заходим в Zabbix: Настройка-&gt;Узлы сети-&gt; Создать узел сети Создаем узел с указанием ip-адреса или dns компа, где находится агент. Можно добавить шаблоны для OS Windows чтобы снимать показатели, которые установлены в шаблоне. В доступности ZBX должен зеленым загореться. Все.