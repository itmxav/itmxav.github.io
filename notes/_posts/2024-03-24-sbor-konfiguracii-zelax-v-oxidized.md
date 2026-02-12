---
id: 2827
title: 'Сбор конфигурации Zelax в Oxidized'
date: '2024-03-24T22:25:31+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2827'
permalink: /2024/03/24/sbor-konfiguracii-zelax-v-oxidized/
views:
    - '132'
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
    - 'Записи по DevOps'
    - 'Записи по Zelax'
tags:
    - oxidized
    - zelax
    - сети
format: false
---

Столкнулся с ситуацией, что для коммутаторов Zelax 30ХХ, на данный момент, нет модели в [Oxidized](https://github.com/ytti/oxidized/blob/master/docs/Supported-OS-Types.md).  
В качестве тестового примера можно закоментить лишнее в ios.rb и назвать файл типа zlx.rb в папке model, потому что синтаксис необходимых команд схож.  
В router.db можно добавить

```
[code lang="plain"]NameRouter:zlx:cisco:IPAddress[/code]
```

В config можно добавить:

```
[code lang="plain"]groups:
   cisco:
     username: usernameZLX
     password: passwordZLX
model_map:
   cisco: zlx
[/code]
```

Конечно, пользователь на Zelax был создан заранее с нужным уровнем и нужными разрешенными командами, как в Cisco.  
В тестовом варианте конфиг собрался. Может модель скоро и в официальном репозитории Oxidized появится.