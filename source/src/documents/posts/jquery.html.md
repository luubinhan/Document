---
layout: 'content'
title: 'jQuery'
description: 'The Write Less, Do More, JavaScript Library'
---

#### Table of Content

<!-- MarkdownTOC depth=2 -->

- Get data attribute jquery
- get which radio is selected via jQuery?
- 5 JQUERY RESPONSIVE FULLSCREEN BACKGROUND IMAGE PLUGINS
- problem with when scroll iphone Backstretch plugin
- Plugin
- GA

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

```js
if (/iP/.test(navigator.platform) && /Safari/i.test(navigator.userAgent)) {
    g += 100;
    j += 100;
}
```

before

```js
this.$wrap.css({
    width: b,
    height: g
}).find("img:not(.deleteable)").css({
    width: e,
    height: j
}).css(a)
```


# Plugin

[JQUERY SCROLL FOLLOW](http://kitchen.net-perspective.com/open-source/scroll-follow/)

[jquery smartresize](https://github.com/luubinhan/jquery-smartresize)

[Transit](https://github.com/rstacruz/jquery.transit#readme)

[Form process](http://git.aaronlumsden.com/progression)

[CallagePlus](http://ed-lea.github.io/jquery-collagePlus/ )

[Magic Select](http://nicolasbize.com/magicsuggest/examples.html)

# GA

```js
gaq.push(['_trackPageview', '/url/to/page/view']);
 <script type=""text/javascript"">
    var _gaq = _gaq || [];
    _gaq.push(['_setAccount', 'UA-5016452-17']);
    _gaq.push(['_trackPageview']);   // ←
    (function() {
        var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
        ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
        var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
    })();

    gaq.push(['_trackEvent', 'Article', 'Reed', title, 1, true]);   
    gaq.push(['_trackEvent', category, action, label, value, opt_noninteraction]);
    //Ví dụ trang TOP
    gaq.push(['_trackEvent', '/recruit2015/top', 'top_student']);  

    //example for a student get 800.5 point
    gaq.push(['_trackEvent', '/recruit2015/top', 'top_student', 800.5]); 
</script>


```
- Notice
https://support.google.com/analytics/answer/1136920?hl=en









