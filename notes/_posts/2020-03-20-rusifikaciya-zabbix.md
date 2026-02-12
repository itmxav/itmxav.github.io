---
id: 687
title: 'Русификация Zabbix'
date: '2020-03-20T15:37:19+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=687'
permalink: /2020/03/20/rusifikaciya-zabbix/
views:
    - '9824'
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
    - zabbix
    - мониторинг
format: false
---

В настройках при попытке сменить язык на русский выпадает ошибка: *"You are not able to choose some of the languages, because locales for them are not installed on the web server."*Смотрим какие какие локали установлены в ОС (на linux):

> `# locale -a`

Смотрим относительно русского: > `# cat /usr/share/i18n/SUPPORTED | grep ru_ru_RU.KOI8-R KOI8-Rru_RU.UTF-8 UTF-8ru_RU ISO-8859-5ru_RU.CP1251 CP1251ru_UA.UTF-8 UTF-8ru_UA KOI8-U`

Видно какие локали доступы, ставим нужное: > `# locale-gen ru_RUGenerating locales…ru_RU.ISO-8859-5… doneGeneration complete.`

Далее: > `# locale-gen ru_RU.UTF8# dpkg-reconfigure localesGenerating locales…en_AG.UTF-8… doneen_AU.UTF-8… doneen_BW.UTF-8… doneen_CA.UTF-8… doneen_DK.UTF-8… doneen_GB.UTF-8… doneen_HK.UTF-8… doneen_IE.UTF-8… doneen_IN.UTF-8… doneen_NG.UTF-8… doneen_NZ.UTF-8… doneen_PH.UTF-8… doneen_SG.UTF-8… doneen_US.UTF-8… doneen_ZA.UTF-8… doneen_ZM.UTF-8… doneen_ZW.UTF-8… doneru_RU.ISO-8859-5… up-to-dateGeneration complete.`

Перезагружаем сервис: > `# service apache2 restart`

Далее переходим в профиль-настройки-выбираем Russian (ru\_RU) -- Источник - [Русификация системы мониторинга Zabbix](https://www.ekzorchik.ru/2015/09/russification-zabbix-system/)