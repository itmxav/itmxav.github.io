---
id: 3035
title: 'Ошибка при удалении репозитория в GitLab'
date: '2024-10-03T13:34:07+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3035'
permalink: /2024/10/03/oshibka-pri-udalenii-repozitoriya-v-gitlab/
views:
    - '50'
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
    - git
    - linux
format: false
---

Недавно в GitLab столкнулся с ошибкой при удалении репозитория:

> This project was scheduled for deletion, but failed with the following message: Failed to open TCP connection to 127.0.0.1:5000 (execution expired)  
> The project visibility may have been made more restrictive if the parent group's visibility changed while the deletion was scheduled.

Поиски по инету привели к следующему [решению](https://gitlab.com/gitlab-org/gitlab/-/issues/24110#note_215456120). В файле /etc/gitlab/gitlab.rb надо изменить конфиг  
\[code lang="plain"\]gitlab\_rails\['registry\_api\_url'\] = "http://127.0.0.1:5000" gitlab\_rails\['registry\_key\_path'\] = "/var/opt/gitlab/gitlab-rails/certificate.key" gitlab\_rails\['registry\_issuer'\] = "omnibus-gitlab-issuer" ### Settings used by Registry application registry\['enable'\] = true registry\['username'\] = "registry" registry\['group'\] = "registry" registry\['uid'\] = nil registry\['gid'\] = nil registry\['dir'\] = "/var/opt/gitlab/registry" registry\['registry\_http\_addr'\] = "localhost:5000" registry\['debug\_addr'\] = "localhost:5001" registry\['log\_directory'\] = "/var/log/gitlab/registry" registry\['env\_directory'\] = "/opt/gitlab/etc/registry/env" registry\['env'\] = { 'SSL\_CERT\_DIR' =&gt; "/opt/gitlab/embedded/ssl/certs/" } registry\['log\_level'\] = "info" registry\['log\_formatter'\] = "text" #registry\['rootcertbundle'\] = "/var/opt/gitlab/registry/certificate.crt" registry\['rootcertbundle'\] = "/var/opt/gitlab/registry/gitlab-registry.crt" registry\['health\_storagedriver\_enabled'\] = true registry\['storage\_delete\_enabled'\] = true registry\_external\_url 'https://registry.gitlab.example.com' registry\_nginx\['enable'\] = true registry\_nginx\['listen\_port'\] = 4567\[/code\]

После внесения изменений переконфигурируем gitlab и перезапускаем  
\[code lang="plain"\]gitlab-ctl reconfigure gitlab-ctl restart\[/code\]

Также надо добавить правило в IPTables (если его нет и весь лишний трафик блокируется) или туда, где задаются правила  
\[code lang="plain"\]iptables -I INPUT -s 127.0.0.1/32 -j ACCEPT\[/code\]   
Или разрешить конкретный порт можно по такому принципу, если нужно более строгое правило. Главное чтобы localhost мог работать запросами внутри сервера.