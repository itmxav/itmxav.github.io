---
id: 196
title: 'Команды для Docker в Linux (некоторые)'
date: '2018-07-13T16:27:26+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=196'
permalink: /2018/07/13/komandy-dlya-docker-nekotorye/
views:
    - '299'
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

``| curl -sSL https://get.docker.com/ \| sh | Установка |
|---|---|
| docker login docker login localhost:8080 | Вход в реестр |
| docker logout docker logout localhost:8080 | Выход из реестра |
| docker search nginx docker search nginx -- filter stars=3 --no-trunc busybox | Поиск образа |
| docker pull nginx docker pull eon01/nginx localhost:5000/myadmin/nginx | Pull (выгрузка из реестра) образа |
| docker push eon01/nginx docker push eon01/nginx localhost:5000/myadmin/nginx | Push (загрузка в реестр) образа |
| docker create -t -i eon01/infinite --name infinite | Создание контейнера |
| docker run -it --name infinite -d eon01/infinite | Первый запуск контейнера |
| docker rename infinite infinity | Переименование контейнера |
| docker rm infinite | Удаление контейнера |
| docker update --cpu-shares 512 -m 300M infinite | Обновление контейнера |
| docker start nginx | Запуск остановленного контейнера |
| docker stop nginx | Остановка |
| docker restart nginx | Перезагрузка |
| docker pause nginx | Пауза (приостановка всех процессов контейнера) |
| docker unpause nginx | Снятие паузы |
| docker wait nginx | Блокировка (до остановки контейнера) |
| docker kill nginx | Отправка SIGKILL (завершающего сигнала) |
| docker kill -s HUP nginx | Отправка другого сигнала |
| docker attach nginx | Подключение к существующему контейнеру |
| docker ps docker ps -a | Работающие контейнеры |
| docker logs infinite | Логи контейнера |
| docker inspect infinite docker inspect --format '{{ .NetworkSettings.IPAddress }}' $(docker ps -q) | Информация о контейнере |
| docker events infinite | События контейнера |
| docker port infinite | Публичные порты |
| docker top infinite | Выполняющиеся процессы |
| docker stats infinite | Использование ресурсов |
| docker diff infinite | Изменения в файлах или директориях файловой системы контейнера |
| docker images | Список образов |
| docker build . docker build github.com/creack/docker-firefox docker build - &lt; Dockerfile docker build - &lt; context.tar.gz docker build -t eon/infinite . docker build -f myOtherDockerfile . curl example.com/remote/Dockerfile \| docker build -f - . | Создание образов |
| docker rmi nginx | Удаление образа |
| docker load &lt; ubuntu.tar.gz docker load --input ubuntu.tar | Загрузка репозитория в tar (из файла или стандартного ввода) |
| docker save busybox &gt; ubuntu.tar | Сохранение образа в tar-архив |
| docker history | Просмотр истории образа |
| docker commit nginx | Создание образа из контейнера |
| docker tag nginx eon01/nginx | Тегирование образа |
| docker push eon01/nginx | Push (загрузка в реестр) образа |
| docker network create -d overlay MyOverlayNetwork docker network create -d bridge MyBridgeNetwork docker network create -d overlay \\ --subnet=192.168.0.0/16 \\ --subnet=192.170.0.0/16 \\ --gateway=192.168.0.100 \\ --gateway=192.170.0.100 \\ --ip-range=192.168.1.0/24 \\ --aux-address="my-router=192.168.1.5" --aux-address="my-switch=192.168.1.6" \\ --aux-address="my-printer=192.170.1.5" --aux-address="my-nas=192.170.1.6" \\ MyOverlayNetwork | Создание сети |
| docker network rm MyOverlayNetwork | Удаление сети |
| docker network ls | Список сетей |
| docker network inspect MyOverlayNetwork | Получение информации о сети |
| docker network connect MyOverlayNetwork nginx | Подключение работающего контейнера к сети |
| docker run -it -d --network=MyOverlayNetwork nginx | Подключение контейнера к сети при его запуске |
| docker network disconnect MyOverlayNetwork nginx | Отключение контейнера от сети |
| docker rm nginx | Удаление работающего контейнера |
| docker rm -v nginx | Удаление контейнера и его тома (volume) |
| docker rm $(docker ps -a -f status=exited -q) | Удаление всех контейнеров со статусом exited |
| docker container prune docker rm `docker ps -a -q` | Удаление всех остановленных контейнеров |
| docker container prune --filter "until=24h" | Удаление контейнеров, остановленных более суток назад |
| docker rmi nginx | Удаление образа |
| docker image prune docker rmi $(docker images -f dangling=true -q) | Удаление неиспользуемых (dangling) образов |
| docker image prune -a | Удаление неиспользуемых (dangling) образов даже с тегами |
| docker rmi $(docker images -a -q) | Удаление всех образов |
| docker rmi -f $(docker images \| grep "^&lt;none&gt;" \| awk "{print $3}") | Удаление всех образов без тегов |
| docker stop $(docker ps -a -q) &amp;&amp; docker rm $(docker ps -a -q) | Остановка и удаление всех контейнеров |
| docker volume prune docker volume rm $(docker volume ls -f dangling=true -q) | Удаление неиспользуемых (dangling) томов |
| docker volume prune --filter "label!=keep" | Удаление неиспользуемых (dangling) томов по фильтру |
| docker network prune | Удаление неиспользуемых сетей |
| docker system prune По умолчанию для Docker 17.06.1+ тома не удаляются.Чтобы удалились и они тоже: docker system prune --volumes | Удаление всех неиспользуемых объектов |
| curl -ssl https://get.docker.com \| bash | Установка Docker Swarm |
| docker swarm init --advertise-addr 192.168.10.1 | Инициализация Swarm |
| docker swarm join-token worker | Подключение рабочего узла (worker) к Swarm |
| docker swarm join-token manager | Подключение управляющего узла (manager) к Swarm |
| docker service ls | Список сервисов |
| docker node ls | Список узлов |
| docker service create --name vote -p 8080:80 instavote/vote | Создание сервиса |
| docker service ps | Список заданий Swarm |
| docker service scale vote=3 | Масштабирование сервиса |
| docker service update --image instavote/vote:movies vote docker service update --force --update-parallelism 1 --update-delay 30s nginx docker service update --update-parallelism 5--update-delay 2s --image instavote/vote:indent vote docker service update --limit-cpu 2 nginx docker service update --replicas=5 nginx | Обновление сервиса |

``````-- Источник - [habr.com](https://habr.com/company/flant/blog/336654/)