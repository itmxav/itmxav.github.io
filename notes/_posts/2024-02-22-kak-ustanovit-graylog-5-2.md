---
id: 2761
title: 'Как установить Graylog 5.2?'
date: '2024-02-22T18:03:38+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2761'
permalink: /2024/02/22/kak-ustanovit-graylog-5-2/
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
    - '185'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по DevOps'
tags:
    - graylog
format: false
---

*❗️Все действия идут под рутом.*

Для запуска нужны MongoDB, Opensearch и сам Graylog 5.2

1\. Устанавливаем MongoDB  
Сначала устанавливаем дополнительные пакеты

```
[code lang="plain"]apt update; apt install gnupg software-properties-common apt-transport-https ca-certificates build-essential libjpeg-dev libpng-dev libtiff-dev curl wget pwgen[/code]
```

  
Ставим ключ

```
[code lang="plain"]curl -fsSL https://pgp.mongodb.com/server-7.0.asc | gpg --dearmor -o /etc/apt/trusted.gpg.d/mongodb-server-7.0.gpg[/code]
```

  
Прописываем репозиторий

```
[code lang="plain"]echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-7.0.list[/code]
```

  
Ставим mongodb

```
[code lang="plain"]apt update; apt install mongodb-org[/code]
```

  
Закидываем в автозапуск и запускаем mongod

```
[code lang="plain"]systemctl enable mongod
systemctl start mongod; systemctl status mongod[/code]
```

  
Если это всё происходит на виртуальной машине Proxmox и не запускается MongoDB, то [здесь описывал проблемы и возможное решение](/2024/02/22/ne-zapuskaetsya-mongodb-na-virtualnoj-mashine-s-proxmox/).

2\. Устанавливаем Opensearch  
Opensearch форк Elastacsearch, потому что были изменения в лицензиях Elastacsearch и некоторым разрабочикам это не понравилось.  
Ставим ключ

```
[code lang="plain"]curl -fsSL https://artifacts.opensearch.org/publickeys/opensearch.pgp | gpg --dearmor -o /etc/apt/trusted.gpg.d/opensearch.gpg[/code]
```

  
Прописываем репозиторий

```
[code lang="plain"]echo "deb https://artifacts.opensearch.org/releases/bundle/opensearch/2.x/apt stable main" | tee /etc/apt/sources.list.d/opensearch-2.x.list[/code]
```

  
Обновляемся и прописываем пароль для установки (лучше сохранить его или в окружении добавить):

```
[code lang="plain"]apt update
export OPENSEARCH_INITIAL_ADMIN_PASSWORD=345Kjasdk3[/code]
```

  
Ставим Opensearch

```
[code lang="plain"]apt install opensearch[/code]
```

  
Далее надо поправить конфиг под Graylog

```
[code lang="plain"]nano /etc/opensearch/opensearch.yml
cluster.name: graylog52
node.name: ${HOSTNAME}
path.data: /var/lib/opensearch
path.logs: /var/log/opensearch
discovery.type: single-node
network.host: 0.0.0.0
#или 127.0.0.1
action.auto_create_index: false
plugins.security.disabled: true[/code]
```

И ещё конфиг

```
[code lang="plain"]nano /etc/opensearch/jvm.options
-Xms4g
-Xmx4g[/code]
```

  
Закидываем в автозапуск и запускаем opensearch

```
[code lang="plain"]sysctl -w vm.max_map_count=262144
echo 'vm.max_map_count=262144' &amp;gt;&amp;gt; /etc/sysctl.conf
Закидываем в автозапуск и запускаем  opensearch
systemctl daemon-reload
systemctl enable opensearch.service
systemctl start opensearch.service; systemctl status opensearch.service[/code]
```

  
Проверяем работу

```
[code lang="plain"]curl -X GET http://localhost:9200 -u ‘admin:admin’[/code]
```

  
Должна вернуться информация о версии, названии и т.п.  
3\. Устанавливаем Graylog  
Качаем

```
[code lang="plain"]wget https://packages.graylog2.org/repo/packages/graylog-5.2-repository_latest.deb[/code]
```

  
И устанавливаем

```
[code lang="plain"]dpkg -i graylog-5.2-repository_latest.deb
apt update; apt install graylog-server [/code]
```

  
Далее надо сделать password\_secret и root\_password\_sha2\[/code\]

Для password\_secret

```
[code lang="plain"]pwgen -N 1 -s 96[/code]
```

  
Для root\_password\_sha2

```
[code lang="plain"]echo -n "Enter Password: " &amp;amp;&amp;amp; head -1 &amp;lt;/dev/stdin | tr -d '\n' | sha256sum | cut -d" " -f1[/code]
```

  
И теперь настраиваем конфиг Graylog’a

```
[code lang="plain"]nano /etc/graylog/server/server.conf
is_leader = true
node_id_file = /etc/graylog/server/node-id
password_secret = PASSWORD_PWGEN
root_password_sha2 =  PASSWORD_ROOT_SHA2
bin_dir = /usr/share/graylog-server/bin
data_dir = /var/lib/graylog-server
plugin_dir = /usr/share/graylog-server/plugin
http_bind_address = IP_ADDRESS:9000
stream_aware_field_types=false
elasticsearch_hosts = http://127.0.0.1:9200
disabled_retention_strategies = none
allow_leading_wildcard_searches = false
allow_highlighting = false
output_batch_size = 500
output_flush_interval = 1
output_fault_count_threshold = 5
output_fault_penalty_seconds = 30
processbuffer_processors = 5
outputbuffer_processors = 3
processor_wait_strategy = blocking
ring_size = 65536
inputbuffer_ring_size = 65536
inputbuffer_processors = 2
inputbuffer_wait_strategy = blocking
message_journal_enabled = true
message_journal_dir = /var/lib/graylog-server/journal
lb_recognition_period_seconds = 3
mongodb_uri = mongodb://localhost/graylog
mongodb_max_connections = 1000[/code]
```

Закидываем в автозапуск и запускаем graylog

```
[code lang="plain"]systemctl daemon-reload
systemctl enable graylog-server.service
systemctl start graylog-server.service; systemctl status graylog-server.service[/code]
```