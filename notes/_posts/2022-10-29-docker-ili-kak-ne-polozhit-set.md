---
id: 1836
title: 'Docker или как не положить сеть?'
date: '2022-10-29T16:29:06+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=1836'
permalink: /2022/10/29/docker-ili-kak-ne-polozhit-set/
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
    - '590'
image: /wp-content/uploads/2021/08/question-1015308_640-e1627931854783.jpg
categories:
    - 'Записи по DevOps'
tags:
    - docker
    - linux
format: false
---

  
***Почему есть проблема с докером?***

IP-адресное пространство, создаваемое докером, частично может перекрываться с адресным пространством сети, где находится комп. Если это никак не фиксить,то проблемесы появляются из-за конфликта адресов (два одинаковых в рамках одной логической сети). Оптимальным вариантом является создать песочницу и там экспериментировать. Например, установить VirtualBox и развернуть там Debian серверный (немного жрет и весит), пробросить порты, сделать снапшот для восстановления и в этой виртуальной машине экспериментировать с докером.

***Зачем нужна песочница?***

В процессе обучения, очевидно, что что-то будет ломаться и надо быстро откатиться назад. Через снапшоты это легко делать + за счёт хоть какой-то изоляции можно хоть как-то по минимуму влиять на рабочую конфигурацию, зависимости основной рабочей машины.  
Поэтому и слово - "песочница", т.е. там можно экспериментировать: ломать, собирать, разбирать что-то не боясь, что поломается рабочая машина.

***Обязательно Debian ставить?***

Делать можно на чем хочешь, но лучше на том, что более распространено, т.к. легче фиксить, инфы много, мусора меньше.

***Почему не WSL2?***

Потому что хост может быть не Windows. Вирталбокс на разных платформах похоже легко настраивается для людей, которые далеки от этого всего+документации много в инете с видео и картинками. Поэтому предпочтение виртуалбоксу. Конечно, это не значит, что надо только его использовать. Можно и VMWare, и WSL2.

***А можно через Docker Desktop работать на Windows?***

Да. Вот пример установки Docker Desktop на Windows 11:

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="220" src="https://www.youtube.com/embed/TFhU2OnblHM" title="Как установить Docker Desktop на Windows 11? [FastHowTo]" width="330"></iframe>

Вот пример изменения сетевого адресного пространства для контейнеров:

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="220" src="https://www.youtube.com/embed/q-mWe0SOX9o" title="Как изменить сеть для контейнеров в Docker Desktop на Windows 11?  [FastHowTo]" width="330"></iframe>

***Можно просто в Linux поменять сеть Docker'a для контейнеров?***

Можно. Вот пример как можно поменять:

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="220" src="https://www.youtube.com/embed/I12W2c-PgOI" title="Как изменить сеть для контейнеров в Docker на Linux (Debian)?" width="330"></iframe>

***Где скачать VirtualBox?***

<https://www.virtualbox.org/wiki/Downloads>

***Где взять образ Debian или другой образ ОС?***

Образы ОС можно взять на оф.сайтах соответствующих дистрибутивов. Например, Debian можно взять здесь -[ https://www.debian.org/download](https://www.debian.org/download)

***Краткий HowTo по настройке песочницы:***

1\. Vbox скачать и поставить

2\. Проверить, что в типах гостевых ОС есть \*64 версии (64 версии часто по умолчанию идут)

2.1 Выбрать, что хочешь поставить и отметить нужные тебе настройки виртуальной машины

3\. Скачать образ с нужной ОС

4\. Смонтировать в виртуальный привод VB образ и запустить машину

4.1 Следовать шагам установщика (если возникает вопрос по x11, то, желательно, поставить без поддержки х11 и графического управления. Только консольный вариант)

4.2 Настроить ssh <https://losst.pro/nastrojka-ssh-v-debian>

4.3 Пробросить порты в VB <https://losst.pro/probros-portov-virtualbox>

4.4 Проверить соединение по SSH к виртуальной машине

5\. Сделать снапшот <https://tavalik.ru/snapshots-in-virtualbox/?ysclid=l9txnadcxw344780093>

6\. Установить докер <https://docs.docker.com/engine/install/debian/>

7\. Учиться рулить докером

***Дополнительные матариалы для обучения?***

[Страница с дополнительными материалами.](/2020/04/06/dopolnitelnaya-informaciy)

[Скачать готовую виртуальную машину с докером на Debian 11 для VB.](https://cloud.mail.ru/public/VvXE/MJdnG28SN)

Видео:

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="220" src="https://www.youtube.com/embed/UeR7N1P6zCk" title="Docker на Debian и VirtualBox" width="330"></iframe>