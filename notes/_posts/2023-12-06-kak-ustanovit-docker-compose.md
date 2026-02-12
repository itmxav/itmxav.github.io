---
id: 2443
title: 'Как установить docker-compose?'
date: '2023-12-06T11:50:56+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2443'
permalink: /2023/12/06/kak-ustanovit-docker-compose/
views:
    - '202'
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
image: /wp-content/uploads/2023/12/Надпись-1.jpg
categories:
    - 'Записи по DevOps'
tags:
    - docker
format: false
---

1\. Переходим в локальный bin

```
[code lang="plain"]cd /usr/local/bin/[/code]
```

2\. Качаем docker-compose (в примере v2.23.3)

```
[code lang="plain"]wget https://github.com/docker/compose/releases/download/v2.23.3/docker-compose-linux-x86_64[/code]
```

3\. Переименовываем и добавляем права на исполнение

```
[code lang="plain"]mv docker-compose-linux-x86_64 docker-compose
chmod +x /usr/local/bin/docker-compose[/code]
```

4\. Проверяем работу через просмотр версии

```
[code lang="plain"]docker-compose --version [/code]
```

Видео:

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="220" src="https://www.youtube.com/embed/cv_eKEhC0fs " title="Как установить Docker Compose на Debian?" width="330"></iframe>