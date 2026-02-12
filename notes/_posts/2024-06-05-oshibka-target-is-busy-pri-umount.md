---
id: 2903
title: 'Ошибка target is busy при umount'
date: '2024-06-05T14:27:00+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2903'
permalink: /2024/06/05/oshibka-target-is-busy-pri-umount/
views:
    - '594'
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
    - '120'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Linux'
tags:
    - linux
format: false
---

Иногда при отмонтировании можно получить ошибку umount target is busy.  
1\. Это значит, что какая-то программа работает ещё с тем, что нужно отмонтировать

```
[code lang="plain"]sudo umount /path/to/target
umount: /path/to/target: target is busy[/code]
```

2. С помощью lsof можно узнать какой процесс задействован. &lt;pre&gt;\[code lang="plain"\]sudo lsof /path/to/target\[/code\]   
И получили вот такой вывод

```
[code lang="plain"]lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
Output information may be incomplete.
lsof: WARNING: can't stat() fuse file system /run/user/1000/doc
Output information may be incomplete.
COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME
bash 2463085 user cwd DIR 7,65 2048 1792 /path/to/target[/code]
```

3\. В данном случае у нас задействован процесс с PID 2463085. Точнее работатет BASH. B правда был открыт терминал и нахлодились именно /path/to/target. После закрытия терминала или перехода в другую папку всё отмонтировалось как надо.

```
[code lang="plain"]sudo umount /path/to/target[/code]
```