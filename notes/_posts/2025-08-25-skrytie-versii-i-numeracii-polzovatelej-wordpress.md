---
id: 3363
title: 'Скрытие версии и нумерации пользователей WordPress'
date: '2025-08-25T17:04:21+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.mxav.ru/?p=3363'
permalink: /2025/08/25/skrytie-versii-i-numeracii-polzovatelej-wordpress/
views:
    - '10'
wp_statistics_words_count:
    - '103'
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
    - 'Записи по CMS'
format: false
---

После установки Wordpress забывают почистить лишнее в целях дополнительной безопасности:  
1\. Убрать/перенести файлы. Идем от корня сайта:

```
[code lang="plain"]

license.txt
readme.html
wp-config-sample.php
wp-admin/install.php

[/code]
```

2\. Отключить нумерацию пользователей в wp-includes/functions.php

```
[code lang="plain"]function my_r_username(){
    if (is_author()){
        wp_redirect( home_url() ); exit;
    }
}
add_action('template_redirect', 'my_r_username');
[/code]
```

3\. Удаляем имя пользователя из css. Для этого в wp-includes/functions.php

```
[code lang="plain"]function remove_c_author( $classes ) {
    foreach( $classes as $key =&amp;amp;amp;amp;amp;gt; $class ) {
        if(strstr($class, "comment-author-")) {
            unset( $classes[$key] );
        }
    }
    return $classes;
}
add_filter( 'comment_class' , 'remove_c_author' );
[/code]
```

4\. Удалить ?ver из скриптов и стилей. В wp-includes/functions.php прописываем

```
[code lang="plain"]function _remove_script_version($src){
    $parts = explode('?', $src);
    return $parts[0];
}
add_filter('script_loader_src','_remove_script_version',15,1);
add_filter('style_loader_src','_remove_script_version',15,1);
[/code]
```

5\. Удалить версию WordPress. Для этого в wp-includes/functions.php

```
[code lang="plain"]function remove_version_info() {
    return '';
}
add_filter('the_generator', 'remove_version_info');
[/code]
```

  
Источник и дополнительная информация - [artemsannikov.ru](https://artemsannikov.ru/cms/wordpress/security-wordpress/hide-version-scripts-and-styles-wordpress/)