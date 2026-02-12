---
id: 190
title: 'Установка docker ubuntu 18.04'
date: '2018-07-12T13:52:39+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=190'
permalink: /2018/07/12/ustanovka-docker-ubuntu-18-04/
views:
    - '245'
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
tags:
    - docker
format: false
---

- Содержание

- [Установка из репозитория](#1 "Установка из репозитория")
- [Установка из репозитория Docker](#2 "Установка из репозитория Docker")
- [Проверка работы Docker](#3 "Проверка работы Docker")

#### *Установка Docker из репозитория Ubuntu*

Делаем update и устанавливаем docker.io: **`sudo apt updatesudo apt install docker.io`**Запускаем службу докер и включаем автозапуск при старте системы: **`sudo systemctl start dockersudo systemctl enable docker`**Проверка версии: **`docker --version`**#### *Установка из репозитория Docker*

- Докер доступен в 2 вариантах:

- Community Edition (CE)
- Enterprise Edition (EE)

Здесь рассматривается пример установка CE, но для начала подключим репозиторий. Делаем update и ставим дополнительное ПО: **`sudo apt updatesudo apt install apt-transport-https ca-certificates curl software-properties-common<c/ode>`**Добавляем GPG ключ репов докера в систему: **`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`**Добавляем репозиторий stable, если нет, то nightly **`### STABLE - Ubuntu 18.04 - НЕ РАБОТАЕТ ###echo "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable" | sudo tee /etc/apt/sources.list.d/docker.list`**\### EDGE - Ubuntu 18.04 - НЕ РАБОТАЕТ ### echo "deb \[arch=amd64\] https://download.docker.com/linux/ubuntu bionic edge" | sudo tee /etc/apt/sources.list.d/docker.list ### NIGHTLY - Ubuntu 18.04 ### echo "deb \[arch=amd64\] https://download.docker.com/linux/ubuntu bionic nightly" | sudo tee /etc/apt/sources.list.d/docker.list Делаем update: **`sudo apt update`**Проверка, что docker из репозитория: **`sudo apt-cache policy docker-ce`**Примерно должны получить **`docker-ce:Installed: (none)Candidate: 18.06.0~ce~dev~git20180504.170722.0.0e0adf0-0~ubuntuVersion table:18.06.0~ce~dev~git20180504.170722.0.0e0adf0-0~ubuntu 500500 https://download.docker.com/linux/ubuntu bionic/nightly amd64 Packages18.06.0~ce~dev~git20180503.170717.0.9bc9d40-0~ubuntu 500500 https://download.docker.com/linux/ubuntu bionic/nightly amd64 Packages`**Установка Docker CE **`sudo apt -y install docker-ce`**Запускаем службу докер и включаем автозапуск при старте системы: **`sudo systemctl start dockersudo systemctl enable docker`**Проверка версии: **`docker --version`**#### *Проверка работы Docker*

**sudo docker run hello-world**Пример вывода: **`Unable to find image 'hello-world:latest' locallylatest: Pulling from library/hello-world78445dd45222: Pull completeDigest: sha256:c5515758d4c5e1e838e9cd307f6c6a0d620b5e07e6f927b07d05f6d12a1ac8d7Status: Downloaded newer image for hello-world:latestHello from Docker!This message shows that your installation appears to be working correctly.`**-- Источник - [totaku.ru](https://totaku.ru/ustanovka-docker-i-docker-compose-v-ubuntu-18-04/)