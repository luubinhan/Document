---
layout: 'content'
title: 'Windows'
description: ''
---

# Hiển thị Thumbnail trên windows

http://www.babelsoft.net/products.htm

# Tắt máy theo thời gian định sẵn trong windows: 


```
shutdown -i
```

# Vào thư mục sendto trong Vista: 

```
%appdata%\microsoft\windows\sendto
```

# Key bản quyền KIS: 

Tina Jones Your license code is: JD7F8-VHAN3-5FV7R-9TA3C

# Sửa lỗi wamp không chạy trên window 8

1. edit httpd.conf, using the link on the wampserver icon wampserver -> apache -> https.conf
find the line > Listen 80
and change to > listen 0.0.0.0:80

This will force apache to listen on IPV4 and make the pre-configured phpMyAdmin security configuration compatable.

# Change max file upload phpadmin

Đổi size trong apache/php.ini

memory_limit
post_max_size
upload_max_filesize


# Create mouse shortcut for "Go to defination" Sublime

Windows - create Default (Windows).sublime-mousemap in %appdata%\Sublime Text 3\Packages\User

Linux - create Default (Linux).sublime-mousemap in ~/.config/sublime-text-3/Packages/User

Mac - create Default (OSX).sublime-mousemap in ~/Library/Application Support/Sublime Text 3/Packages/User

Now open that file and put the following configuration inside

[
    {
        "button": "button1", 
        "count": 1, 
        "modifiers": ["ctrl"],
        "press_command": "drag_select",
        "command": "goto_definition"
    }
]


# Sublime Fetch Setup

{
    "files":
    {
        "JS Velocity": "https://github.com/julianshapiro/velocity/blob/master/velocity.min.js",
        "JS Velocity UI": "https://github.com/julianshapiro/velocity/blob/master/velocity.ui.min.js",
        "jquery": "http://code.jquery.com/jquery.min.js"
    },
    "packages":
    {
        "Grunt Template": "https://github.com/luubinhan/grunt-template/zipball/master",
        "HTML Template": "https://github.com/luubinhan/HTML-Template/zipball/master",
        "WP ACF": "https://downloads.wordpress.org/plugin/advanced-custom-fields.zip",
        "WP ACF Leaflet Field": "https://downloads.wordpress.org/plugin/advanced-custom-fields-leaflet-field.zip",
        "WP Admin menu editor": "https://downloads.wordpress.org/plugin/admin-menu-editor.1.4.1.zip",
        "WP Image widget": "https://downloads.wordpress.org/plugin/image-widget.4.1.zip",
        "WP Ninja form": "https://downloads.wordpress.org/plugin/ninja-forms.2.8.5.zip",
        "WP Page navi": "https://downloads.wordpress.org/plugin/wp-pagenavi.2.86.zip",
        "WP Recaptcha": "https://github.com/luubinhan/wp-recaptcha-integration/zipball/master",
        "WP SEO by Yoast": "https://downloads.wordpress.org/plugin/wordpress-seo.1.6.3.zip",
        "WP Template": "https://github.com/luubinhan/wordpress-boilerplate-theme/zipball/master",
        "WP Types": "https://downloads.wordpress.org/plugin/types.zip"
    }
}
