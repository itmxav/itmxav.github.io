---
id: 3105
title: 'Как настроить chroot для sftp (OpenSSH)?'
date: '2024-11-27T12:47:41+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3105'
permalink: /2024/11/27/kak-sdelat-chroot-dlya-sftp-openssh/
views:
    - '205'
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
    - '302'
image: /wp-content/uploads/2024/02/bash2.png
categories:
    - 'Записи по Linux'
tags:
    - linux
    - ssh
format: false
---

Часто может требоваться настроить доступ так, чтобы пользователь не мог ходить по всей системе при подключении по sftp. Также возможность подключения по ssh для этого пользователя может не требоваться.

Для того чтобы настроить chroot надо сделать следующее :  
1\. Открываем /etc/ssh/sshd\_conf

```
[code lang="plain"]nano /etc/ssh/sshd_conf[/code]
```

2\. Найти строчку относительно sftp. Закомментировать её и добавить ниже новую, чтобы использовался встроенный sftp-сервер

```
[code lang="plain"]#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp -f AUTH -l VERBOSE[/code]
```

3\. Переходим в конец файла и добавляем

```
[code lang="plain"]Match user usertest
  ChrootDirectory /home
  ForceCommand internal-sftp -d /usertest
  PermitTunnel no
  AllowAgentForwarding no
  AllowTcpForwarding no
  X11Forwarding no[/code]
```

В случаем подключения пользователя usertest попадаем в домашнюю папку /home/usertest.  
На всякий случай можно отключить переадресацию агентов (AllowAgentForwarding), портов SSH (AllowTcpForwarding), возможность графических интерфейсов X11 программ (X11Forwarding) и возможности туннелирования (PermitTunnel), если глобально что-то включено. ForceCommand internal-sftp говорит о том, что можно использовать только встроенный sftp.  
В ChrootDirectory можно указывать не только конкретный каталог, но переменную %h (home directory).  
Если же необходимо на группу пользователей сделать, то

```
[code lang="plain"]Match group ugroupsftp
  ChrootDirectory /home
  ForceCommand internal-sftp -d %u
  AllowTcpForwarding no
  PermitTunnel no
  AllowAgentForwarding no
  AllowTcpForwarding no
  X11Forwarding no[/code]
```

Вместо пользователя указываем нужную группу и папку для ChrootDirectory, в данном случае home. %u - параметр для папки пользователя, если она совпадает с именем.  
Т. е. сначала идет подключение в ChrootDirectory, а потом автоматический переход в папку пользователя /home/usertest

4\. **Важный момент!** Чтобы всё работало необходимо установить правильные права на папки:

/home и ветка выше, если не home, должна принадлежать пользователю root и группе root.  
/home/usertest должна принадлежать пользователю usertest и группе usertest, а также установлены права

```
[code lang="plain"]drwxr-x---[/code]
```

или более низкие. Это для того, чтобы другие пользователи не заходили в домашнюю папку, если их нет в группе конкретного пользователя.

5\. Далее проверяем конфигурацию

```
[code lang="plain"]sshd -t [/code]
```

Если всё хорошо, то вывода не будет. Если что-то не так, то будет написано где ошибка в конфигурации. Если ошибок нет и не удается подключиться, то надо смотреть логи.

6\. Перечитываем конфигурацию sshd

```
[code lang="plain"]systemctl reload sshd[/code]
```