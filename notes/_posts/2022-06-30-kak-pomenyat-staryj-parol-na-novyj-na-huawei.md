---
id: 1344
title: 'Как поменять старый пароль на новый на Huawei?'
date: '2022-06-30T11:56:02+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=1344'
permalink: /2022/06/30/kak-pomenyat-staryj-parol-na-novyj-na-huawei/
views:
    - '182'
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
    - 'Записи по Huawei'
tags:
    - huawei
    - сети
format: false
---

<div class="comment-body">Если есть привилегированный доступ 15 уровня и надо сменить на условный пароль hua@321, то

> ` <HuaSW> system-view<br></br>[HuaSW] user-interface console 0<br></br>[HuaSW-ui-console0] authentication-mode password<br></br>[HuaSW-ui-console0] set authentication password cipher<br></br>Enter Password(<6-16>): hua@321<br></br>Confirm Password: hua@321<br></br>[HuaSW-ui-console0] return`

Далее проверить изменился ли пароль. Если всё хорошо, то сохранить конфиг.

> `[HuaSW] save`

  
Источники - [Форум Huawei](https://forum.huawei.com/enterprise/ru/faq-как-поменять-сбросить-пароль-на-сетевом-оборудовании/thread/496609-100335)</div>