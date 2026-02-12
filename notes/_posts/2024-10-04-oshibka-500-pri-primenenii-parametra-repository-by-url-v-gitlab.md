---
id: 3057
title: 'Ошибка 500 при применении параметра Repository by URL в GitLab'
date: '2024-10-04T16:29:32+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3057'
permalink: /2024/10/04/oshibka-500-pri-primenenii-parametra-repository-by-url-v-gitlab/
views:
    - '59'
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
    - '77'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Linux'
tags:
    - git
format: false
---

Столкнулся недавно с ситуацией, что при применении Repository by URL в GitLab в разделе

> Admin area -&gt; setting -&gt; Import and export settings -&gt; Repository by URL

Запрос подвисает и в логах пишет

```
[code lang="plain"]/var/log/gitlab/puma/puma_stderr.log:source=rack-timeout id=.... timeout=60000ms service=60000ms state=timed_out at=error
/var/log/gitlab/gitlab-rails/production_json.log:{"method":"PATCH","path":"/admin/application_settings/general","format":"html","controller":"Admin::ApplicationSettingsController","action":"general","status":500.....{"key":"authenticity_token","value":"[FILTERED]....[/code]
```

Оказалось, что при применении этого параметра идет запрос в DNS. Решилась проблема просто добавлением нужных правил:

```
[code lang="plain"]iptables -I INPUT -s IP_DNS/32 -p udp -m udp --sport 53 -j ACCEPT
iptables -I INPUT -s IP_DNS_2/32 -p udp -m udp --sport 53 -j ACCEPT[/code]
```