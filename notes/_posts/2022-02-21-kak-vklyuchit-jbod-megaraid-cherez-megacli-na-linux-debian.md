---
id: 929
title: 'Как включить JBOD MegaRAID через megacli на Linux Debian?'
date: '2022-02-21T18:02:27+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=929'
permalink: /2022/02/21/kak-vklyuchit-jbod-megaraid-cherez-megacli-na-linux-debian/
views:
    - '408'
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
    - 'Debian, Ubuntu etc.'
tags:
    - linux
    - raid
format: false
---

0\. Посмотреть есть ли нужная поддержка в контроллере вот [здесь](https://www.broadcom.com/support/knowledgebase/1211161496893/megaraid-3ware-and-hba-support-for-various-raid-levels-and-jbod-).  
1\. Загружаемся с флешки или установленной ОС, если она уже стоит. Создаем папку, переходим туда, устанавливаем доп ПО, качаем MegaCli:

> `<br></br>mkdir megacli; cd megacli/; apt install alien libncurses5 unzip; wget https://docs.broadcom.com/docs-and-downloads/raid-controllers/raid-controllers-common-files/8-07-14_MegaCLI.zip<br></br>`

2\. Распаковываем, переходим в папку Linux и конвертируем из rpm в deb формат:

> `<br></br>unzip 8-07-14_MegaCLI.zip; cd Linux/; alien  -k --scripts MegaCli-8.07.14-1.noarch.rpm<br></br>`

3\. Устанавливаем:

> `<br></br>dpkg  -i megacli_8.07.14-1_all.deb<br></br>`

4\. Переходим в папку с MegaCli и смотрим версию:

> `<br></br>cd /opt/MegaRAID/MegaCli/; ls -lah; /opt/MegaRAID/MegaCli/MegaCli64 -v<br></br>`

5\. Запускаем установку параметра JBOD на все диски:

> `<br></br>/opt/MegaRAID/MegaCli/MegaCli64 -AdpSetProp EnableJBOD 1 -aALL<br></br>`

6\. Перезагружаемся.