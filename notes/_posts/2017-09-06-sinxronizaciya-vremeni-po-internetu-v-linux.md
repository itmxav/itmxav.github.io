---
id: 85
title: 'Синхронизация времени по Интернету в Linux'
date: '2017-09-06T11:01:15+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=85'
permalink: /2017/09/06/sinxronizaciya-vremeni-po-internetu-v-linux/
views:
    - '347'
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
wp_statistics_words_count:
    - '73'
image: /wp-content/uploads/2017/09/time-297498_640.png
categories:
    - 'Записи по Linux'
tags:
    - linux
    - время
format: false
---

Для того чтобы синхронизировать время на Linux машине необходимо установить ntpdate (в данном случае пример на Ubuntu):

> `sudo apt-get install ntpdate`

Переходим в Cron: > `sudo crontab -e`

И прописывает когда нам надо делать синхронизацию: > `40 2 * * * /usr/sbin/ntpdate pool.ntp.org`

pool.ntp.org — это огромный кластер серверов точного времени, предоставляющий надежный и простой в использовании NTP-сервис для миллионов клиентов. -- Источник - [www.pool.ntp.org](http://www.pool.ntp.org/ru/)-- Дополнительная информация: - [Обновление базы данных (tz database) часовых поясов в Linux](/2018/09/12/obnovlenie-bazy-dannyx-tz-database-chasovyx-poyasov-v-linux/)- [Как установить время и дату в Linux вручную (date)?](/2018/09/17/kak-ustanovit-vremya-i-datu-v-linux-vruchnuyu-date/)