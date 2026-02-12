---
id: 2020
title: 'Как запустить wget через прокси?'
date: '2023-01-19T03:21:45+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=2020'
permalink: /2023/01/19/kak-zapustit-wget-cherez-proksi/
views:
    - '211'
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
    - '28'
image: /wp-content/uploads/2023/01/Надпись.jpg
categories:
    - 'Записи по Linux'
tags:
    - linux
format: false
---

Чтобы настроить wget для работы через proxy:

**Первый способ**

1 Создать файл

```
[code lang="plain"]nano ~/.wgetrc[/code]
```

2 Прописать:

\[code lang="plain"\]use\_proxy=yes http\_proxy=127.0.0.1:8080 https\_proxy=127.0.0.1:8080 \[/code\] **Второй способ**

```
[code lang="plain"]wget -e use_proxy=yes -e http_proxy=[IP-сервера]:[порт][/code]
```

Если логин с паролем:

```
[code lang="plain"]wget -e use_proxy=yes -e http_proxy=http://[пользователь]:[пароль]@[IP-сервера]:[порт][/code]
```

Видео:

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="220" src="https://www.youtube.com/embed/52pE77Gfov4" title="" width="330"></iframe>