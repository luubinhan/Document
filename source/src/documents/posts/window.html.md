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
