---
id: 922
title: 'Сброс пароля на коммутаторах Cisco Catalyst / Cisco Catalyst Password Recovery'
date: '2022-02-21T17:44:30+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=922'
permalink: /2022/02/21/sbros-parolya-na-kommutatorax-cisco-catalyst-cisco-catalyst-password-recovery/
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
    - '251'
wp_statistics_words_count:
    - '92'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Cisco'
tags:
    - cisco
    - сети
format: false
---

1\. Подключаем консольный кабель. 2. Выключаем по питанию. 3. Нажимает кнопку Mode и держим 4. Включаем. Ждем 12 секунд и отпускаем кнопку Mode. 5. Ждем поле для ввода команд

> `Switch:`

6. Вводим flash\_init и load\_helper: > `Switch: flash_initSwitch: load_helper`

7. Смотрим файл конфига во flash и переименовываем его: > `dir flash:rename flash:config.text flash:config.old`

8. После изменения загружаемся: > `Switch: boot`

9. Переходим в привелегерованный режим и возвращаем файл: > `Switch>enSwitch#rename flash:config.old flash:config.textSwitch#copy flash:config.text system:running-config`

10. Удаляем старый пароль и, если нужно, то делаем другие настройки: > `Switch(conf)#no enable secret`

11. Устанавливаем новый пароль и сохраняем конфигурацию: > `Switch(conf)#enable secret PASSWORDSwitch# copy runn start`

или > `Switch# wr mem`

Если у вас Catalyst версии R, то см. [здесь](/2022/02/21/sbros-parolya-na-cisco-catalyst-3850r-cisco-catalyst-3850r-password-recovery/). -- Источник - [wiki.merionet.ru](https://wiki.merionet.ru/ip-telephoniya/64/sbros-parolya-na-kommutatorax-i-marshrutizatorax-cisco/)