---
layout: 'content'
title: 'jQuery'
description: 'The Write Less, Do More, JavaScript Library'
---

#### Table of Content
-------------
<!-- MarkdownTOC depth=2 -->

- Get data attribute jquery
- get which radio is selected via jQuery?
- 5 JQUERY RESPONSIVE FULLSCREEN BACKGROUND IMAGE PLUGINS
- problem with when scroll iphone Backstretch plugin

<!-- /MarkdownTOC -->


# Get data attribute jquery

```js
$(this).data("id")
```

# get which radio is selected via jQuery? 

```js
$('input[name=radioName]:checked', '#myForm').val()
```

# 5 JQUERY RESPONSIVE FULLSCREEN BACKGROUND IMAGE PLUGINS

http://www.jquery4u.com/plugins/responsive-fullscreen-background-image-plugins/


# problem with when scroll iphone Backstretch plugin
add
if (/iP/.test(navigator.platform) && /Safari/i.test(navigator.userAgent)) {
    g += 100;
    j += 100;
}
before
this.$wrap.css({
    width: b,
    height: g
}).find("img:not(.deleteable)").css({
    width: e,
    height: j
}).css(a)













