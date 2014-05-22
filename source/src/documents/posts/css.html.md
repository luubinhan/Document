---
layout: 'content'
title: 'CSS'
description: Best practice and trick
---

#### Table of content


<!-- MarkdownTOC depth=2 -->

- IPHONE FONT SIZE
- iOS forces rounded corners and glare on inputs
- How to disable phone number linking in Mobile Safari
- Twitter width 100%
- Facebook responsive
- Cần nhớ khi thiết kế email
- Free fontface
- Popular font

<!-- /MarkdownTOC -->


# IPHONE FONT SIZE

```css
-webkit-text-size-adjust: 100%;
```

# iOS forces rounded corners and glare on inputs 

```css
-webkit-appearance: none;
```

# How to disable phone number linking in Mobile Safari

```html
<meta name="format-detection" content="telephone=no">
```

# Twitter width 100%

```css
iframe[id^='twitter-widget-']{ width:100% !important;}
```

# Facebook responsive

```css
#fb-root {
    display: none;
}

/* To fill the container and nothing else */
.fb_iframe_widget, .fb_iframe_widget span, .fb_iframe_widget span iframe[style]{
    width: 100% !important;
}
```

# Cần nhớ khi thiết kế email

kích thước nhỏ hơn 500-700
Cho phép unsubscribe
trường hợp hình ko load được
làm rõ ai là người gởi mail

# Free fontface

http://fontsforweb.com/

# Popular font

http://www.google.com/fonts/specimen/Droid+Sans
http://www.google.com/fonts/specimen/Noto+Sans
123rf.com