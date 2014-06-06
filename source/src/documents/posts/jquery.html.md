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
- Khai báo mảng trong javascript
- Converts a JavaScript value to a JavaScript Object Notation (JSON) string.
- Make an array of object
- One Page Plugin

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

# Khai báo mảng trong javascript

best practices

```js
var a = [];
```

nếu khai báo

```js
var a = new Array(1);
```

Array là object có thể overwritten

```js
Array = function(key){
    this.id = key;
}
```

# Converts a JavaScript value to a JavaScript Object Notation (JSON) string.

```js
JSON.stringify(value [, replacer] [, space])
```

value
Required. A JavaScript value, usually an object or array, to be converted.

replacer
Optional. A function or array that transforms the results.

If replacer is a function, JSON.stringify calls the function, passing in the key and value of each member. The return value is used instead of the original value. If the function returns undefined, the member is excluded. The key for the root object is an empty string: "".
If replacer is an array, only members with key values in the array will be converted. The order in which the members are converted is the same as the order of the keys in the array. The replacer array is ignored when the value argument is also an array.

space
Optional. Adds indentation, white space, and line break characters to the return-value JSON text to make it easier to read.
If space is omitted, the return-value text is generated without any extra white space.
If space is a number, the return-value text is indented with the specified number of white spaces at each level. If space is greater than 10, text is indented 10 spaces.
If space is a non-empty string, such as '\t', the return-value text is indented with the characters in the string at each level.
If space is a string that is longer than 10 characters, the first 10 characters are used.

# Make an array of object

```js
 var usersData = [{
        firstName: "tommy",
        lastName: "MalCom",
        email: "test@test.com",
        id: 102
    }, {
        firstName: "Peter",
        lastName: "breCht",
        email: "test2@test2.com",
        id: 103
    }, {
        firstName: "RoHan",
        lastName: "sahu",
        email: "test3@test3.com",
        id: 104
    }];
```

```js
var n = 100;
var sample = new Array();
for (var i = 0; i < n; i++)
    sample.push(new Object());
```


http://nfriedly.com/techblog/2009/06/advanced-javascript-objects-arrays-and-array-like-objects/


# One Page Plugin

https://github.com/alvarotrigo/fullPage.js
https://github.com/peachananr/onepage-scroll