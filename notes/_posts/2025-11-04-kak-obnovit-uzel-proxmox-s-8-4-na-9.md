---
id: 3438
title: 'Как обновить узел Proxmox с 8.4 на 9?'
date: '2025-11-04T23:15:16+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3438'
permalink: /2025/11/04/kak-obnovit-uzel-proxmox-s-8-4-na-9/
views:
    - '96'
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
    - '88'
image: /wp-content/uploads/2025/11/Шаблон.jpg
categories:
    - Виртуализация
tags:
    - proxmox
format: false
---

Если используется Ceph, то читайте процесс обновления [здесь](https://pve.proxmox.com/wiki/Upgrade_from_8_to_9#Actions_step-by-step). Желательно выключить все машины перед обновлением, на всякий случай.

0\. Сделать бэкапы всего и работать через прямой доступ к серверу.

1.Выключаем pve-enterprise.list через комментирование

```
[code lang="plain"]# nano /etc/apt/sources.list.d/pve-enterprise.list
#deb https://enterprise.proxmox.com/debian/pve bookworm pve-enterprise[/code]
```

2\. Обновляем всё, что есть на текущей ветке

```
[code lang="plain"]apt update
apt dist-upgrade
pveversion[/code]
```

3\. Проверяем на ошибки при обновлении

```
[code lang="plain"]pve8to9 --full[/code]
```

Если есть, то исправляем всё.

4\. Обновляем репозитории

```
[code lang="plain"]sed -i 's/bookworm/trixie/g' /etc/apt/sources.list
sed -i 's/bookworm/trixie/g' /etc/apt/sources.list.d/pve-enterprise.list
apt update[/code]
```

5\. Если всё готово, то читаем какие вопросы могут возникнуть при обновлении вот [здесь ](https://pve.proxmox.com/wiki/Upgrade_from_8_to_9#Upgrade_the_system_to_Debian_Trixie_and_Proxmox_VE_9.0) и обновляемся

```
[code lang="plain"]apt dist-upgrade[/code]
```

Видео на Youtube:

<iframe allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen="" frameborder="0" height="220" referrerpolicy="strict-origin-when-cross-origin" src="https://www.youtube.com/embed/tRjznCVTjfw" title="Как обновить узел Proxmox с 8.4 на 9? [FastHowTo]" width="330"></iframe>

Видео на Rutube:

<iframe allow="clipboard-write; autoplay" allowfullscreen="" frameborder="0" height="220" mozallowfullscreen="" src="https://rutube.ru/play/embed/7d6c9bb346871d48c9f030c092bc0aeb" webkitallowfullscreen="" width="330"></iframe>