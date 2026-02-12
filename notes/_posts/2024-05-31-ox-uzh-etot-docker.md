---
id: 2894
title: 'Ох уж этот Docker!'
date: '2024-05-31T14:07:44+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2894'
permalink: /2024/05/31/ox-uzh-etot-docker/
views:
    - '87'
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
    - '61'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по DevOps'
tags:
    - docker
format: false
---

Как дальше жить, если кит уплывает:  
1\. Прописать registry-mirrors

```
[code lang="plain"]{ &amp;quot;registry-mirrors&amp;quot; : [ &amp;quot;https://куда-то-там&amp;quot; ] }[/code]
```

в Linux

```
[code lang="plain"]/etc/docker/daemon.json[/code]
```

или

```
[code lang="plain"]~/.config/docker/daemon.json[/code]
```

Для Windows

```
[code lang="plain"]C:\ProgramData\docker\config\daemon.json[/code]
```

Для Windows с Docker Desktop

```
[code lang="plain"]C:\Users\&amp;lt;Пользователь&amp;gt;\.docker\daemon.json[/code]
```

И перечитать конфиг

```
[code lang="plain"]systemctl reload docker[/code]
```

Но если скучно и одиноко в этом сером, мрачном мире, то

```
[code lang="plain"]systemctl restart docker[/code]
```

2\. Поднять свой удобный прокси и пустить все через него. Вот [здесь](/2023/12/06/kak-rabotat-s-docker-cherez-proksi/) описывал как настроить работу Docker через прокси.