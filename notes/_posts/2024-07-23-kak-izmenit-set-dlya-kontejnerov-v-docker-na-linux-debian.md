---
id: 2949
title: 'Как изменить сеть для контейнеров в Docker на Linux (Debian)?'
date: '2024-07-23T01:02:01+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2949'
permalink: /2024/07/23/kak-izmenit-set-dlya-kontejnerov-v-docker-na-linux-debian/
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
    - '106'
image: /wp-content/uploads/2024/07/DockerNetworkLinux.jpg
categories:
    - 'Записи по DevOps'
    - 'Записи по Linux'
tags:
    - docker
    - linux
format: false
---

1\. Проверяем работает ли docker

\[code lang="plain"\]systemctl status docker\[/code\]

2\. Смотрим список сетей

\[code lang="plain"\]docker network list\[/code\]

В данном случае интересует bridge  
3\. Смотрим сеть для bridge

\[code lang="plain"\]docker network inspect bridge | grep Subnet\[/code\]

Вывод примерно такой по умолчанию бывает:

\[code lang="plain"\]"Subnet": "172.17.0.0/16",\[/code\]

4\. В качестве теста у меня запущен контейнер с nginx. Через браузер проверил, что всё работает.  
5\. Редактируем или создаем файл daemon.json

\[code lang="plain"\] nano /etc/docker/daemon.json\[/code\]

И прописываем, в качестве примера, сетевое адресное пространство 10.1.0.0/24 с IP-адресом bridge-интерфейса 10.1.0.1.

\[code lang="plain"\]{ "bip": "10.1.0.1/24", "default-address-pools": \[{ "base": "10.1.0.0/24", "size": 24 }\] }\[/code\]

6\. Смотрим запущенные контейнеры

\[code lang="plain"\]docker ps -a\[/code\]

7\. Удаляем все и проверяем

\[code lang="plain"\]docker rm -f `docker ps -q -a` docker ps -a\[/code\]

8\. Перезапускаем docker

\[code lang="plain"\] systemctl restart docker\[/code\]

9\. Проверяем сеть bridge

\[code lang="plain"\] docker network inspect bridge | grep Subnet\[/code\]

Вывод

\[code lang="plain"\]"Subnet": "10.1.0.0/24",\[/code\]

10\. В качестве теста запускаю контейнер с nginx, проверяю его адрес и работоспособность через браузер

\[code lang="plain"\]docker run -d -p 80:80 nginx\[/code\]

ID этого контейнера 3b2a1894c706

\[code lang="plain"\]docker inspect 3b2a1894c706 | grep "IPAddress"\[/code\]

Видео на Youtube:

<iframe allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen="" frameborder="0" height="220" referrerpolicy="strict-origin-when-cross-origin" src="https://www.youtube.com/embed/I12W2c-PgOI" title="Как изменить сеть для контейнеров в Docker на Linux (Debian)?" width="330"></iframe>

Видео на Rutube:

<iframe allow="clipboard-write; autoplay" allowfullscreen="" frameborder="0" height="220" mozallowfullscreen="" src="https://rutube.ru/play/embed/12c3ef6ad9aae50252c7002362640d1c" webkitallowfullscreen="" width="330"></iframe>