---
id: 2708
title: 'Как установить WordPress на Debian?'
date: '2024-02-11T19:32:23+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=2708'
permalink: /2024/02/11/kak-ustanovit-wordpress-na-debian/
views:
    - '250'
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
image: /wp-content/uploads/2024/02/Надпись-1.jpg
categories:
    - 'Записи по DevOps'
tags:
    - linux
    - mysql
    - wordpress
format: false
---

Чтобы установить WordPress (в качестве примера используется домен wp-site.test) на Linux Debian с самоподписанным сертификатом необходимо:

1. Обновить систему
\[code lang="plain"\]apt update; apt upgrade\[/code\]

3. Устанавливаем необходимые пакеты
\[code lang="plain"\]apt install nginx apache2 htop curl wget mariadb-server php php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap php-intl php-zip unzip php-mysql\[/code\]

5. Временно выключим и добавим в автозапуск сервисы
\[code lang="plain"\]systemctl enable nginx apache2 mariadb; systemctl stop nginx apache2\[/code\]

7. Поправим порт в ports.conf на 8080, т.к. делаем связку nginx+apache2+php+mariadb и создадим виртуальный хост на apache2
\[code lang="plain"\]nano /etc/apache2/ports.conf; nano /etc/apache2/sites-available/wp-site.test.conf\[/code\]

\[code lang="plain"\]&lt;VirtualHost 127.0.0.1:8080&gt; ServerName wp-site.test ServerAlias www.wp-site.test DocumentRoot "/var/www/wp-site.test" &lt;Directory "/var/www/wp-site.test/"&gt; AllowOverride All allow from all Options -Indexes #Options FollowSymLinks &lt;/Directory&gt; &lt;FilesMatch "\\.ph(p\[3-8\]?|tml)$"&gt; SetHandler application/x-httpd-php &lt;/FilesMatch&gt; ErrorLog /var/www/log/apache2/wp-site.test-error.log CustomLog /var/www/log/apache2/wp-site.test-access.log combined &lt;ifModule mod\_headers.c&gt; Header set X-XSS-Protection "1; mode=block" &lt;/IfModule&gt; &lt;IfModule php8\_module&gt; php\_flag session.cookie\_httponly 1 php\_flag session.cookie\_secure 1 &lt;/IfModule&gt; &lt;/VirtualHost&gt;\[/code\]

10. Создаем папки для логов
\[code lang="plain"\]mkdir /var/www/log/; mkdir /var/www/log/apache2/; mkdir /var/www/log/nginx/\[/code\]

12. Создаем папку для сайта и тестовый php-файл
\[code lang="plain"\]mkdir /var/www/wp-site.test/; echo '&lt;?php phpinfo(); ?&gt;' &gt; /var/www/wp-site.test/index.php\[/code\]

14. Включаем редиректы на apache2 и проверяем конфигурацию
\[code lang="plain"\]a2enmod rewrite; apache2ctl configtest\[/code\]

16. Включаем сайт
\[code lang="plain"\]a2ensite wp-site.test.conf\[/code\]

18. Создаем сертификат и ключ для https-соединения
\[code lang="plain"\]openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/wp-site.test-selfsigned.key -out /etc/ssl/certs/wp-site.test-selfsigned.crt\[/code\]

20. Создаем виртуальный хост для nginx и прописываем конфиг
\[code lang="plain"\]nano /etc/nginx/sites-available/wp-site.test\[/code\]

\[code lang="plain"\]server { listen 80; server\_name wp-site.test www.wp-site.test; add\_header Content-Security-Policy upgrade-insecure-requests; return 302 https://wp-site.test$request\_uri; } server { listen 443 ssl; server\_name wp-site.test www.wp-site.test; access\_log /var/www/log/nginx/wp-site.test-access.log; error\_log /var/www/log/nginx/wp-site.test-error.log; ssl\_certificate /etc/ssl/certs/wp-site.test-selfsigned.crt; ssl\_certificate\_key /etc/ssl/private/wp-site.test-selfsigned.key; ssl\_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3; add\_header Strict-Transport-Security 'max-age=15552000; includeSubDomains'; add\_header Content-Security-Policy upgrade-insecure-requests; ssl\_ciphers EECDH+ECDSA+AESGCM:EECDH+aRSA+AESGCM:EECDH+ECDSA+SHA384:"убрать перенос" EECDH+ECDSA+SHA256:EECDH+aRSA+SHA384: "убрать перенос" EECDH+aRSA+SHA256:EECDH:EDH+aRSA:HIGH:!aNULL:!eNULL:!LOW:!RC4:!3DES:"убрать перенос" !MD5:!EXP:!PSK:!SRP:!SEED:!DSS:!CAMELLIA; ssl\_prefer\_server\_ciphers on; client\_max\_body\_size 200M; keepalive\_requests 100; keepalive\_timeout 30; reset\_timedout\_connection on; client\_body\_timeout 10; send\_timeout 2; fastcgi\_ignore\_client\_abort on; location / { fastcgi\_ignore\_client\_abort on; proxy\_ignore\_client\_abort on; proxy\_pass http://127.0.0.1:8080/; proxy\_set\_header Host $host; proxy\_set\_header X-Real-IP $remote\_addr; proxy\_set\_header X-Forwarded-For $proxy\_add\_x\_forwarded\_for; #proxy\_set\_header Connection ""; proxy\_connect\_timeout 120; proxy\_send\_timeout 120; proxy\_read\_timeout 180; } location ~\* \\.(woff2|svg|png|jpg|jpeg|gif|css|js|pdf|doc|zip|rar|docx|avi|tiff|"убрать перенос" rtf|gz|gzip|mpg|mpeg|"убрать перенос" mp3|mp4|tgz|wav|wmv|wma|xls|xlsx|xml|bmp|ico||psd)$ { root /var/www/wp-site.test/; } }\[/code\]

23. Включаем хост на nginx
\[code lang="plain"\]ln -s "/etc/nginx/sites-available/wp-site.test" /etc/nginx/sites-enabled/wp-site.test\[/code\]

25. Проверяем конфиг
nginx -t\[/code\] 27. Задаем пароль root для mariadb
\[code lang="plain"\]mysqladmin -u root password newpasstest\[/code\]

29. Заходим в СУБД
\[code lang="plain"\]mysql -uroot -p\[/code\]

31. Создаем пользователя с паролем и базу данных для WordPress
\[code lang="plain"\]CREATE DATABASE `wptestdb`; CREATE USER 'wpuzer'@'localhost' IDENTIFIED BY 'password'; GRANT ALL PRIVILEGES ON `wptestdb`.\* TO 'wpuzer'@'localhost'; FLUSH PRIVILEGES; quit;\[/code\]

33. Перезапускаем сервисы и проверяем работу сайта (надо в браузере зайти на URL)
\[code lang="plain"\]systemctl restart apache2 nginx mariadb\[/code\]

35. Переходим в папку сайта и удаляем ненужное.
\[code lang="plain"\]cd /var/www/wp-site.test/; rm index.php\[/code\]

37. Качаем сам WordPress
\[code lang="plain"\]wget https://ru.wordpress.org/latest-ru\_RU.zip; \[/code\]

39. Распаковываем скаченное и перемещаем в корень сайта
\[code lang="plain"\]unzip latest-ru\_RU.zip;mv wordpress/\* ./\[/code\]

41. Удаляем ненужное
\[code lang="plain"\]rm -r wordpress/; rm latest-ru\_RU.zip\[/code\]

43. Ставим права на папку с файлами сайта
\[code lang="plain"\]cd ..; chown www-data:www-data -R wp-site.test/; chmod g+s wp-site.test/\[/code\]

45. Переходим в браузере по URL домена и настраиваем WordPress
\[code lang="plain"\]Имя - Тестовый сайт Логин с паролем wp-user:4dveRElmfKjNrltN Почта для восстановения test@example.loc\[/code\]


Видео на Youtube:

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="220" src="https://www.youtube.com/embed/1JOiGeq0Xz8 " title="Как установить WordPress на Debian?" width="330"></iframe>

Видео на Rutube:

<iframe allow="clipboard-write; autoplay" allowfullscreen="" frameborder="0" height="220" mozallowfullscreen="" src="https://rutube.ru/play/embed/0d5d4ca26a9d7dc0d12cef413fe16776/" webkitallowfullscreen="" width="330"></iframe>