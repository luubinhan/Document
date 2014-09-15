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

## Orange Overstated by Chad Pierce

h1 { color: #7c795d; font-family: 'Trocchi', serif; font-size: 45px; font-weight: normal; line-height: 48px; margin: 0; }

h2 { color: #7c795d; font-family: 'Source Sans Pro', sans-serif; font-size: 28px; font-weight: 400; line-height: 32px; margin: 0 0 24px; }

.subheader { font-size: 26px; font-weight: 300; color: #ffcc66; margin: 0 0 24px; }

## Bold by Rafal Tomal

h1 { color: #111; font-family: 'Helvetica Neue', sans-serif; font-size: 275px; font-weight: bold; letter-spacing: -1px; line-height: 1; text-align: center; }

h2 { color: #111; font-family: 'Open Sans', sans-serif; font-size: 30px; font-weight: 300; line-height: 32px; margin: 0 0 72px; text-align: center; }

p { color: #685206; font-family: 'Helvetica Neue', sans-serif; font-size: 14px; line-height: 24px; margin: 0 0 24px; text-align: justify; text-justify: inter-word; }


## Don’t Taste Me Bro by Robert Neu

h1 { color: #ffffff; font-family: 'Raleway',sans-serif; font-size: 62px; font-weight: 800; line-height: 72px; margin: 0 0 24px; text-align: center; text-transform: uppercase; }

h2 { color: #ffffff; font-family: 'Raleway',sans-serif; font-size: 30px; font-weight: 800; line-height: 36px; margin: 0 0 24px; text-align: center; }

p { color: #f8f8f8; font-family: 'Raleway',sans-serif; font-size: 18px; font-weight: 500; line-height: 32px; margin: 0 0 24px; }

## Early Night by Rafal Tomal

h1 { color: #ffffff; font-family: 'Lato', sans-serif; font-size: 54px; font-weight: 300; line-height: 58px; margin: 0 0 58px; }

p { color: #adb7bd; font-family: 'Lucida Sans', Arial, sans-serif; font-size: 16px; line-height: 26px; text-indent: 30px; margin: 0; }

.date { background: #fe921f; color: #ffffff; display: inline-block; font-family: 'Lato', sans-serif; font-size: 12px; font-weight: bold; line-height: 12px; letter-spacing: 1px; margin: 0 0 30px; padding: 10px 15px 8px; text-transform: uppercase; }

## SureFire by Jon Perez

a { color: #ff6600; transition: .5s; -moz-transition: .5s; -webkit-transition: .5s; -o-transition: .5s; font-family: 'Muli', sans-serif; }

a:hover { text-decoration: underline }

h1 { padding-bottom: 15px }

h1 a { font-family: 'Open Sans Condensed', sans-serif; font-size: 48px; color: #333; }

h1 a:hover { color: #ff6600; text-decoration: none; }

p { color: #333; font-family: 'Muli', sans-serif; margin-bottom: 15px; }

a.more-link { color: white; font-weight: bold; font-size: 14px; font-family: Arial, Helvetica, sans-serif; padding: 3px 10px; background-color: #ff6600; border-radius: 5px; float: right; }

a.more-link:hover { text-decoration: none; background-color: #666; border-radius: 0px; }

## The Beauty of Words by Jim Rush

blockquote { background-image: url(http://typespiration.com/wp-content/themes/typespiration/images/quote.png); background-position: 10px 10%; background-repeat: no-repeat no-repeat; padding: 150px 0; }

p { color: #f2f2f2; background: #ff4a4a; font-size: 75px; line-height: 74px; font-weight: 700; margin: 0 5px 24px; float: left; padding: 10px; margin: 0 5px 24px; font-family: 'Libre Baskerville', serif; }

.punchline p { background: #f2f2f2; color: #ff4a4a; }

a { color: #adadad; font-size: 25px; text-decoration: none; float: right; font-family: 'Libre Baskerville', serif; line-height: 4; }

a:hover { color: #ff4a4a; text-decoration: none; }