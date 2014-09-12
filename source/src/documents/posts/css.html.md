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
- ont face
- Extend Bootstrap

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

#Font face

Download this [Microsoft app](http://www.microsoft.com/typography/property/fpedit.htm)
Strip out the info in the font file - replace font name with your own
On the last page, remove the Vendor Name
Then convert to OTF because it'll probably say corrupted. [Use this](http://www.freefontconverter.com/)
Now upload to Font Squirrel and it'll let you use it without restrictions

# Extend Bootstrap

http://exacttarget.github.io/fuelux/

# CSS Checkbox generator

http://www.csscheckbox.com/css-checkbox-generator.php


# Typography Collection

## http://www.coudalpartners.com/

Small headline

```
    font-family: Gill Sans, Verdana;
    font-size: 11px;
    line-height: 14px;
    text-transform: uppercase;
    letter-spacing: 2px;
    font-weight: bold;
```

Large Headline

```css

    font-family: times, Times New Roman, times-roman, georgia, serif;
    color: #444;
    margin: 0;
    padding: 0px 0px 6px 0px;
    font-size: 51px;
    line-height: 44px;
    letter-spacing: -2px;
    font-weight: bold;
```

## Human Sexuality and the Nuptial Mystery

```css
HEADLINE
        font-family:Georgia,serif;
    color:#4E443C;
    font-variant: small-caps; text-transform: none; font-weight: 100; margin-bottom: 0;

PARAGRAPH
        font-family: "Helvetica Neue", "Lucida Grande", Helvetica, Arial, Verdana, sans-serif;
        font-size: 14px;
        margin-top: .5em; color: #666;

PARAGRAPH START
        font-family:Georgia,serif;
    font-size: .8em;
        font-weight: bold;
    text-transform:uppercase;
    letter-spacing:2px; 
```

## I love Typography

```css
HEADLINE
        font-family: Georgia, "Times New Roman", Times, serif;
        font-size:24px;
    margin-top: 5px; margin-bottom: 0px;
    text-align: center;
        font-weight: normal;
        color: #222;

SUBHEADLINE
        font-family: "Lucida Grande", Tahoma;
    font-size: 10px;
    font-weight: lighter;
    font-variant: normal;
    text-transform: uppercase;
    color: #666666;
        margin-top: 10px;
    text-align: center!important;
    letter-spacing: 0.3em;
```

## The Big Noob

```css
DATE
      font-size: 85%;
      text-transform: uppercase;
      letter-spacing: 1px;
      color: #bbb;
      font-size: 10px;
      font-family: "Lucida Grande", Verdana, Helvetica, Arial, sans-serif;
      font-weight: 100; 

HEADLINE
        font: bold 34px "Century Schoolbook", Georgia, Times, serif;
    color: #333;
    line-height: 90%;
    margin: .2em 0 .4em 0;
    letter-spacing: -2px;

TAG
        color: #76879b;
        font-size: 10px;
        margin: 5px;
        font-family: "Lucida Grande", Verdana, Helvetica, Arial, sans-serif;
        font-size: 11px;

```