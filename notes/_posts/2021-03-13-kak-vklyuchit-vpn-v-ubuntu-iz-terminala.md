---
id: 822
title: 'Как включить VPN в Ubuntu из терминала?'
date: '2021-03-13T21:38:23+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=822'
permalink: /2021/03/13/kak-vklyuchit-vpn-v-ubuntu-iz-terminala/
views:
    - '153'
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
    - 'Debian, Ubuntu etc.'
tags:
    - linux
    - vpn
format: false
---

Чтобы включить VPN в Ubuntu из terminal'a надо запустить nmcli с указанием нужных параметров:

> `nmcli connection up id VPNname`

Выключить: > `nmcli connection down id VPNname`