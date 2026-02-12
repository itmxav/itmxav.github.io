---
id: 2930
title: 'Как установить Docker Desktop на Windows 11?'
date: '2024-07-22T20:27:08+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2930'
permalink: /2024/07/22/kak-ustanovit-docker-desktop-na-windows-11/
views:
    - '58'
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
image: /wp-content/uploads/2024/07/DockerWin11.jpg
categories:
    - 'Записи FastHowTo'
    - 'Записи по DevOps'
    - 'Записи по Windows'
tags:
    - docker
    - windows
format: false
---

Чтобы установить Docker Desktop на Windows 11 надо:  
1\. Перейти на [сайт с Docker Desktop](https://www.docker.com/products/docker-desktop/)  
2\. Нажать "Скачать для Windows" и подождать, пока скачается файл.  
3\. Запустить скаченный файл  
4\. Пройти установку. Если впервые устанавливаете, то лучше оставить галочки в рекомендуемых опциях.  
5\. Запустить Docker Desktop и подождать пока Docker Engine включиться. Должно быть зеленым в левом нижнем углу окна Docker Desktop.  
6\. Для проверки можно открыть командную строку и посмотреть версию через команду:  
\[code lang="plain"\]docker -v\[/code\]  
7\. Также можно проверить работу Docker, скачав и запустив какой-нибудь контейнер (hello-world или nginx с указанием 80 порта)

Видео на Youtube:

<iframe allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen="" frameborder="0" height="220" referrerpolicy="strict-origin-when-cross-origin" src="https://www.youtube.com/embed/TFhU2OnblHM" title="Как установить Docker Desktop на Windows 11? [FastHowTo]" width="330"></iframe>

Видео на Rutube:

<iframe allow="clipboard-write; autoplay" allowfullscreen="" frameborder="0" height="220" mozallowfullscreen="" src="https://rutube.ru/play/embed/42b4fc5bdf491c7778fbad6e7355466b" webkitallowfullscreen="" width="330"></iframe>