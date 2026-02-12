---
id: 2748
title: 'Обновление Oxidized c 0.26.3 до 0.29.1 на CentOS 7'
date: '2024-02-20T11:41:02+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2748'
permalink: /2024/02/20/obnovlenie-oxidized-c-0-26-3-do-0-29-1-na-centos-7/
views:
    - '183'
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
    - 'Записи по сетям'
tags:
    - oxidized
    - сети
format: false
---

1\. Обновляем cmake.

1.1 Создаем папки

\[code lang="plain"\] # mkdir tmpdir; cd tmpdir/; mkdir tmpcmake; cd tmpcmake\[/code\]

1.2 Качаем cmake-3.6.2

\[code lang="plain"\] # wget https://cmake.org/files/v3.6/cmake-3.6.2.tar.gz\[/code\]

1.3 Удаляем установленный cmake

\[code lang="plain"\] # yum remove cmake -y\[/code\]

1.4 Распаковываем с переходим в папку cmake

\[code lang="plain"\] # clear;tar -zxvf cmake-3.6.2.tar.gz; cd cmake-3.6.2\[/code\]

1.5 Устанавливаем и проверяем версию

\[code lang="plain"\] # ./bootstrap --prefix=/usr/local # make # make install; cmake --version\[/code\]

2\. Теперь обновляем ruby

2.1 Создаем папки

\[code lang="plain"\]# cd ~/tmpdir; mkdir tmpruby; cd tmpruby; \[/code\]

2.2 Устанавлиаем доп.пакеты и качаем ruby 3.0.4 (для версии выше могут потребоваться дополнительные зависимости)

\[code lang="plain"\]#yum groupinstall "Development Tools"; yum install openssl-devel; wget http://cache.ruby-lang.org/pub/ruby/3.0/ruby-3.0.4.tar.gz\[/code\]

2.3 Распаковываем с переходим в папку ruby

\[code lang="plain"\]# tar -xzvf ruby-\*; cd ruby-3.0.4\[/code\]

2.4 Устанавливаем и проверяем версию

\[code lang="plain"\]# ./configure # make # make install; ruby -v\[/code\]

3\. Теперь обновляем сам gem и oxidized

\[code lang="plain"\]# gem update --system # gem install oxidized-web oxidized\[/code\]