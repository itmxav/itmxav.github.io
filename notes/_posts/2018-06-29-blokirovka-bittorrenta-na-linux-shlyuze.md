---
id: 179
title: 'Блокировка BitTorrent&#8217;a на Linux-шлюзе'
date: '2018-06-29T16:03:29+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=179'
permalink: /2018/06/29/blokirovka-bittorrenta-na-linux-shlyuze/
views:
    - '432'
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
image: /wp-content/uploads/2017/03/torrent.png
categories:
    - 'Записи по Linux'
tags:
    - firewall
    - iptables
    - linux
    - torrent
format: false
---

Блокировка скачивания файлов .torrent и сайтов со словами, которые находятся в string:

> `# iptables -I FORWARD 1 -m string --string "BitTorrent" --algo bm --to 65535 -j DROP# iptables -I FORWARD 1 -m string --string "BitTorrent protocol" --algo bm --to 65535 -j DROP# iptables -I FORWARD 1 -m string --string "peer_id=" --algo bm --to 65535 -j DROP# iptables -I FORWARD 1 -m string --string ".torrent" --algo bm --to 65535 -j DROP# iptables -I FORWARD 1 -m string --string "announce.php?passkey=" --algo bm --to 65535 -j DROP# iptables -I FORWARD 1 -m string --string "torrent" --algo bm --to 65535 -j DROP# iptables -I FORWARD 1 -m string --string "announce" --algo bm --to 65535 -j DROP# iptables -I FORWARD 1 -m string --string "info_hash" --algo bm --to 65535 -j DROP`

Также можно поставить модуль ipp2p, но он устарел и толку мало от него: > `# apt-get update# apt-get install xtables-addons-common# iptables -I FORWARD -p tcp -m ipp2p --bit -j DROP# iptables -I FORWARD -p udp -m ipp2p --bit -j DROP`