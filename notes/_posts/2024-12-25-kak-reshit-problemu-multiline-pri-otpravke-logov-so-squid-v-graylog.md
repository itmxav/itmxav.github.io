---
id: 3201
title: 'Как решить проблему multiline при отправке логов со Squid в Graylog?'
date: '2024-12-25T12:14:26+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3201'
permalink: /2024/12/25/kak-reshit-problemu-multiline-pri-otpravke-logov-so-squid-v-graylog/
views:
    - '53'
wp_statistics_words_count:
    - '137'
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
    - 'Записи про мониторинг'
tags:
    - graylog
    - squid
format: false
---

Иногда бывает, что при отправки логов со Squid прилетает множество строчек пачкой, хотя должно было прилетать и обрабатываться по одной строчке. Такое возникает когда пытаются настроить отправку по UDP. Если же настроить отправку по TCP, то проблема множеством строк пропадает.

Вариант настройки может быть такой:

1\. Раскомментируем или создаем, например, вот такой формат логов:

\[code lang="plain"\]logformat squid %{%Y.%m.%d/%H:%M:%S}tl %ts.%03tu %6tr %&amp;gt;a:%&amp;gt;p %Ss/%03&amp;gt;Hs %&amp;lt;st %rm %ru %\[un %Sh/%&amp;lt;a:%&amp;lt;p %mt %&amp;lt;Hs\[/code\]

2\. Указываем как и куда отправлять логи:

\[code lang="plain"\]access\_log tcp://192.168.0.1:19302 squid\[/code\]

Здесь мы указываем, что надо отправлять логи в формате squid по TCP на сервер 192.168.0.1 на порт 19302.

3\. Проверяем конфиг Squid

\[code lang="plain"\]clear;squid -k parse\[/code\]

4\. Если всё нормально, что перечитываем конфиг

\[code lang="plain"\]systemctl reload squid.service\[/code\]

5\. На сервере с Graylog проверяем при помощи tcpdump/wireshark, что пакеты с логами доходят.

6\. Настраиваем альтернативный вариант Input для 19302 с указанием, что это Raw/Plaintext TCP. Проверяем, что логи обрабатываются Graylog'ом