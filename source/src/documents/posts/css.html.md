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
- CSS Checkbox generator
- Meta data template
  - Product Social Media Tag Template
  - Full Social Media Tag Template: Article
- Typography Collection
  - http://www.coudalpartners.com/
  - Human Sexuality and the Nuptial Mystery
  - I love Typography
  - The Big Noob
  - Orange Overstated by Chad Pierce
  - Bold by Rafal Tomal
  - Don’t Taste Me Bro by Robert Neu
  - Early Night by Rafal Tomal
  - SureFire by Jon Perez
  - The Beauty of Words by Jim Rush
- Character-code
- FAVICON
- Custom Select
- File upload
- Checkbox Radio
- Must have meta tag
- Bootstrap slider
- Font convert

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

# Meta data template

http://moz.com/blog/meta-data-templates-123

## Product Social Media Tag Template

```html
<!-- Update your html tag to include the itemscope and itemtype attributes. -->
<html itemscope itemtype="http://schema.org/Product">

<!-- Place this data between the <head> tags of your website -->
<title>Page Title. Maximum length 60-70 characters</title>
<meta name="description" content="Page description. No longer than 155 characters." />

<!-- Schema.org markup for Google+ -->
<meta itemprop="name" content="The Name or Title Here">
<meta itemprop="description" content="This is the page description">
<meta itemprop="image" content="http://www.example.com/image.jpg">

<!-- Twitter Card data -->
<meta name="twitter:card" content="product">
<meta name="twitter:site" content="@publisher_handle">
<meta name="twitter:title" content="Page Title">
<meta name="twitter:description" content="Page description less than 200 characters">
<meta name="twitter:creator" content="@author_handle">
<meta name="twitter:image" content="http://www.example.com/image.html">
<meta name="twitter:data1" content="$3">
<meta name="twitter:label1" content="Price">
<meta name="twitter:data2" content="Black">
<meta name="twitter:label2" content="Color">

<!-- Open Graph data -->
<meta property="og:title" content="Title Here" />
<meta property="og:type" content="article" />
<meta property="og:url" content="http://www.example.com/" />
<meta property="og:image" content="http://example.com/image.jpg" />
<meta property="og:description" content="Description Here" />
<meta property="og:site_name" content="Site Name, i.e. Moz" />
<meta property="og:price:amount" content="15.00" />
<meta property="og:price:currency" content="USD" />
```

## Full Social Media Tag Template: Article

```html
<!-- Update your html tag to include the itemscope and itemtype attributes. -->
<html itemscope itemtype="http://schema.org/Article">

<!-- Place this data between the <head> tags of your website -->
<title>Page Title. Maximum length 60-70 characters</title>
<meta name="description" content="Page description. No longer than 155 characters." />

<!-- Schema.org markup for Google+ -->
<meta itemprop="name" content="The Name or Title Here">
<meta itemprop="description" content="This is the page description">
<meta itemprop="image" content="http://www.example.com/image.jpg">

<!-- Twitter Card data -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@publisher_handle">
<meta name="twitter:title" content="Page Title">
<meta name="twitter:description" content="Page description less than 200 characters">
<meta name="twitter:creator" content="@author_handle">
<!-- Twitter summary card with large image must be at least 280x150px -->
<meta name="twitter:image:src" content="http://www.example.com/image.html">

<!-- Open Graph data -->
<meta property="og:title" content="Title Here" />
<meta property="og:type" content="article" />
<meta property="og:url" content="http://www.example.com/" />
<meta property="og:image" content="http://example.com/image.jpg" />
<meta property="og:description" content="Description Here" />
<meta property="og:site_name" content="Site Name, i.e. Moz" />
<meta property="article:published_time" content="2013-09-17T05:59:00+01:00" />
<meta property="article:modified_time" content="2013-09-16T19:08:47+01:00" />
<meta property="article:section" content="Article Section" />
<meta property="article:tag" content="Article Tag" />
<meta property="fb:admins" content="Facebook numberic ID" />
```

Pat

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


    font-family: times, Times New Roman, times-roman, georgia, serif;
    color: #444;
    margin: 0;
    padding: 0px 0px 6px 0px;
    font-size: 51px;
    line-height: 44px;
    letter-spacing: -2px;
    font-weight: bold;


## Human Sexuality and the Nuptial Mystery


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


## I love Typography

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


## The Big Noob


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


# Character-code

http://character-code.com/


# FAVICON

<link rel="icon" href="<?php echo $GLOBALS["TEMPLATE_RELATIVE_URL"]; ?>images/favicon.ico" type="image/x-icon" size="57x57">
<link rel="apple-touch-icon" href="<?php echo $GLOBALS["TEMPLATE_RELATIVE_URL"]; ?>images/apple-touch-iphone.png" />
<link rel="apple-touch-icon" sizes="72x72" href="<?php echo $GLOBALS["TEMPLATE_RELATIVE_URL"]; ?>images/apple-touch-ipad.png" />
<link rel="apple-touch-icon" sizes="114x114" href="<?php echo $GLOBALS["TEMPLATE_RELATIVE_URL"]; ?>images/apple-touch-iphone4.png" />
<link rel="apple-touch-icon" sizes="144x144" href="<?php echo $GLOBALS["TEMPLATE_RELATIVE_URL"]; ?>images/apple-touch-iphone4.png" /> 

# Custom Select

HTML

```html
<select id="mounth">
    <option value="hide">-- Month --</option>
    <option value="january" rel="icon-temperature">January</option>
    <option value="february">February</option>
    <option value="march">March</option>
    <option value="april">April</option>
    <option value="may">May</option>
    <option value="june">June</option>
    <option value="july">July</option>
    <option value="august">August</option>
    <option value="september">September</option>
    <option value="october">October</option>
    <option value="november">November</option>
    <option value="december">December</option>
</select> 
```

CSS

```css
.select-hidden {
  display: none;
  visibility: hidden;
  padding-right: 10px;
}

.select {
  cursor: pointer;
  display: inline-block;
  position: relative;
  font-size: 16px;
  color: #fff;
  width: 220px;
  height: 40px;
}

.select-styled {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background-color: #c0392b;
  padding: 8px 15px;
  -moz-transition: all 0.2s ease-in;
  -o-transition: all 0.2s ease-in;
  -webkit-transition: all 0.2s ease-in;
  transition: all 0.2s ease-in;
}
.select-styled:after {
  content: "";
  width: 0;
  height: 0;
  border: 7px solid transparent;
  border-color: #fff transparent transparent transparent;
  position: absolute;
  top: 16px;
  right: 10px;
}
.select-styled:hover {
  background-color: #b83729;
}
.select-styled:active, .select-styled.active {
  background-color: #ab3326;
}
.select-styled:active:after, .select-styled.active:after {
  top: 9px;
  border-color: transparent transparent #fff transparent;
}

.select-options {
  display: none;
  position: absolute;
  top: 100%;
  right: 0;
  left: 0;
  z-index: 999;
  margin: 0;
  padding: 0;
  list-style: none;
  background-color: #ab3326;
}
.select-options li {
  margin: 0;
  padding: 12px 0;
  text-indent: 15px;
  border-top: 1px solid #962d22;
  -moz-transition: all 0.15s ease-in;
  -o-transition: all 0.15s ease-in;
  -webkit-transition: all 0.15s ease-in;
  transition: all 0.15s ease-in;
}
.select-options li:hover {
  color: #c0392b;
  background: #fff;
}
.select-options li[rel="hide"] {
  display: none;
}
```

js

```js 
/*
Reference: http://jsfiddle.net/BB3JK/47/
*/

$('select').each(function(){
    var $this = $(this), numberOfOptions = $(this).children('option').length;
  
    $this.addClass('select-hidden'); 
    $this.wrap('<div class="select"></div>');
    $this.after('<div class="select-styled"></div>');

    var $styledSelect = $this.next('div.select-styled');
    $styledSelect.text($this.children('option').eq(0).text());
  
    var $list = $('<ul />', {
        'class': 'select-options'
    }).insertAfter($styledSelect);
  
    for (var i = 0; i < numberOfOptions; i++) {
        $('<li />', {
            text: $this.children('option').eq(i).text(),
            rel: $this.children('option').eq(i).val()
        }).appendTo($list);
    }
  
    var $listItems = $list.children('li');
  
    $styledSelect.click(function(e) {

        e.stopPropagation();
          
          if ($(this).hasClass('active')) {
            $(this).removeClass('active');
              $(this).next('ul.select-options').hide();
          } else {
            $(this).addClass('active');
            $(this).next('ul.select-options').show();
          }
      });  
  
    $listItems.click(function(e) {
        e.stopPropagation();
        // Change Text
        $styledSelect.text($(this).text()).removeClass('active');
        $rel = $(this).attr('rel');
        $this.val($rel);
        $list.hide();

        //Change Select Option      
        $(this).parents('.select').find('select').val($rel).change();
    });
  
    $(document).click(function() {
        $styledSelect.removeClass('active');
        $list.hide();
    });

});
```

# File upload

HTML

```html
<div class="custom-file-upload">
    <!--<label for="file">File: </label>--> 
    <input type="file" id="file" name="myfiles[]" multiple />
</div>
```

CSS

```css

.custom-file-upload-hidden {
  display: none;
  visibility: hidden;
  position: absolute;
  left: -9999px;
}

.custom-file-upload {
  display: block;
  width: auto;
  font-size: 16px;
  margin-top: 30px;
}
.custom-file-upload label {
  display: block;
  margin-bottom: 5px;
}

.file-upload-wrapper {
  position: relative;
  margin-bottom: 5px;
}

.file-upload-input {
  width: 300px;
  color: #fff;
  font-size: 16px;
  padding: 11px 17px;
  border: none;
  background-color: #c0392b;
  -moz-transition: all 0.2s ease-in;
  -o-transition: all 0.2s ease-in;
  -webkit-transition: all 0.2s ease-in;
  transition: all 0.2s ease-in;
  float: left;
  /* IE 9 Fix */
}
.file-upload-input:hover, .file-upload-input:focus {
  background-color: #ab3326;
  outline: none;
}

.file-upload-button {
  cursor: pointer;
  display: inline-block;
  color: #fff;
  font-size: 16px;
  text-transform: uppercase;
  padding: 11px 20px;
  border: none;
  margin-left: -1px;
  background-color: #962d22;
  float: left;
  /* IE 9 Fix */
  -moz-transition: all 0.2s ease-in;
  -o-transition: all 0.2s ease-in;
  -webkit-transition: all 0.2s ease-in;
  transition: all 0.2s ease-in;
}
.file-upload-button:hover {
  background-color: #6d2018;
}

```

JS

```js
//Reference: 
//http://www.onextrapixel.com/2012/12/10/how-to-create-a-custom-file-input-with-jquery-css3-and-php/
;(function($) {

          // Browser supports HTML5 multiple file?
          var multipleSupport = typeof $('<input/>')[0].multiple !== 'undefined',
              isIE = /msie/i.test( navigator.userAgent );

          $.fn.customFile = function() {

            return this.each(function() {

              var $file = $(this).addClass('custom-file-upload-hidden'), // the original file input
                  $wrap = $('<div class="file-upload-wrapper">'),
                  $input = $('<input type="text" class="file-upload-input" />'),
                  // Button that will be used in non-IE browsers
                  $button = $('<button type="button" class="file-upload-button">Select a File</button>'),
                  // Hack for IE
                  $label = $('<label class="file-upload-button" for="'+ $file[0].id +'">Select a File</label>');

              // Hide by shifting to the left so we
              // can still trigger events
              $file.css({
                position: 'absolute',
                left: '-9999px'
              });

              $wrap.insertAfter( $file )
                .append( $file, $input, ( isIE ? $label : $button ) );

              // Prevent focus
              $file.attr('tabIndex', -1);
              $button.attr('tabIndex', -1);

              $button.click(function () {
                $file.focus().click(); // Open dialog
              });

              $file.change(function() {

                var files = [], fileArr, filename;

                // If multiple is supported then extract
                // all filenames from the file array
                if ( multipleSupport ) {
                  fileArr = $file[0].files;
                  for ( var i = 0, len = fileArr.length; i < len; i++ ) {
                    files.push( fileArr[i].name );
                  }
                  filename = files.join(', ');

                // If not supported then just take the value
                // and remove the path to just show the filename
                } else {
                  filename = $file.val().split('\\').pop();
                }

                $input.val( filename ) // Set the value
                  .attr('title', filename) // Show filename in title tootlip
                  .focus(); // Regain focus

              });

              $input.on({
                blur: function() { $file.trigger('blur'); },
                keydown: function( e ) {
                  if ( e.which === 13 ) { // Enter
                    if ( !isIE ) { $file.trigger('click'); }
                  } else if ( e.which === 8 || e.which === 46 ) { // Backspace & Del
                    // On some browsers the value is read-only
                    // with this trick we remove the old input and add
                    // a clean clone with all the original events attached
                    $file.replaceWith( $file = $file.clone( true ) );
                    $file.trigger('change');
                    $input.val('');
                  } else if ( e.which === 9 ){ // TAB
                    return;
                  } else { // All other keys
                    return false;
                  }
                }
              });

            });

          };

          // Old browser fallback
          if ( !multipleSupport ) {
            $( document ).on('change', 'input.customfile', function() {

              var $this = $(this),
                  // Create a unique ID so we
                  // can attach the label to the input
                  uniqId = 'customfile_'+ (new Date()).getTime(),
                  $wrap = $this.parent(),

                  // Filter empty input
                  $inputs = $wrap.siblings().find('.file-upload-input')
                    .filter(function(){ return !this.value }),

                  $file = $('<input type="file" id="'+ uniqId +'" name="'+ $this.attr('name') +'"/>');

              // 1ms timeout so it runs after all other events
              // that modify the value have triggered
              setTimeout(function() {
                // Add a new input
                if ( $this.val() ) {
                  // Check for empty fields to prevent
                  // creating new inputs when changing files
                  if ( !$inputs.length ) {
                    $wrap.after( $file );
                    $file.customFile();
                  }
                // Remove and reorganize inputs
                } else {
                  $inputs.parent().remove();
                  // Move the input so it's always last on the list
                  $wrap.appendTo( $wrap.parent() );
                  $wrap.find('input').focus();
                }
              }, 1);

            });
          }

}(jQuery));

$('input[type=file]').customFile();
```

# Checkbox Radio

```html
<div class="wrapper">
    <ul>
        <li>
            <p>Gender:</p>
        </li>
        <li>
            <input type="radio" name="radio-btn" />Male</li>
        <li>
            <input type="radio" name="radio-btn" />Female</li>
    </ul>
    <ul>
        <li>
            <p>Favorite music:</p>
        </li>
        <li>
            <input type="checkbox" name="check-box" /> <span>Pop music</span>

        </li>
        <li>
            <input type="checkbox" name="check-box" /> <span>Rock music</span>

        </li>
        <li>
            <input type="checkbox" name="check-box" /> <span>Rap music</span>

        </li>
        <li>
            <input type="checkbox" name="check-box" /> <span>Hiphop music</span>

        </li>
    </ul>
</div>
```
```css

.radio-btn input[type="radio"], .check-box input[type="checkbox"] {
    visibility: hidden;
}
/*Custom checkbox*/
 .check-box {
    width: 22px;
    height: 22px;
    cursor: pointer;
    display: inline-block;
    margin: 2px 7px 0 0;
    position: relative;
    overflow: hidden;
    box-shadow: 0 0 1px #ccc;
    -webkit-border-radius: 3px;
    -moz-border-radius: 3px;
    border-radius: 3px;
    background: rgb(255, 255, 255);
    background: -moz-linear-gradient(top, rgba(255, 255, 255, 1) 0%, rgba(246, 246, 246, 1) 47%, rgba(237, 237, 237, 1) 100%);
    background: -webkit-gradient(linear, left top, left bottom, color-stop(0%, rgba(255, 255, 255, 1)), color-stop(47%, rgba(246, 246, 246, 1)), color-stop(100%, rgba(237, 237, 237, 1)));
    background: -webkit-linear-gradient(top, rgba(255, 255, 255, 1) 0%, rgba(246, 246, 246, 1) 47%, rgba(237, 237, 237, 1) 100%);
    background: -o-linear-gradient(top, rgba(255, 255, 255, 1) 0%, rgba(246, 246, 246, 1) 47%, rgba(237, 237, 237, 1) 100%);
    background: -ms-linear-gradient(top, rgba(255, 255, 255, 1) 0%, rgba(246, 246, 246, 1) 47%, rgba(237, 237, 237, 1) 100%);
    background: linear-gradient(to bottom, rgba(255, 255, 255, 1) 0%, rgba(246, 246, 246, 1) 47%, rgba(237, 237, 237, 1) 100%);
    filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#ffffff', endColorstr='#ededed', GradientType=0);
    border: 1px solid #ccc;
}
.check-box i {
    background: url('http://cdn1.iconfinder.com/data/icons/mimiGlyphs/16/check_mark.png') no-repeat center center;
    position: absolute;
    left: 3px;
    bottom: -15px;
    width: 16px;
    height: 16px;
    opacity: .5;
    -webkit-transition: all 400ms ease-in-out;
    -moz-transition: all 400ms ease-in-out;
    -o-transition: all 400ms ease-in-out;
    transition: all 400ms ease-in-out;
    -webkit-transform:rotateZ(-180deg);
    -moz-transform:rotateZ(-180deg);
    -o-transform:rotateZ(-180deg);
    transform:rotateZ(-180deg);
}
.checkedBox {
    -moz-box-shadow: inset 0 0 5px 1px #ccc;
    -webkit-box-shadow: inset 0 0 5px 1px #ccc;
    box-shadow: inset 0 0 5px 1px #ccc;
    border-bottom-color: #fff;
}
.checkedBox i {
    bottom: 2px;
    -webkit-transform:rotateZ(0deg);
    -moz-transform:rotateZ(0deg);
    -o-transform:rotateZ(0deg);
    transform:rotateZ(0deg);
}
/*Custom radio button*/
 .radio-btn {
    width: 20px;
    height: 20px;
    display: inline-block;
    float: left;
    margin: 3px 7px 0 0;
    cursor: pointer;
    position: relative;
    -webkit-border-radius: 100%;
    -moz-border-radius: 100%;
    border-radius: 100%;
    border: 1px solid #ccc;
    box-shadow: 0 0 1px #ccc;
    background: rgb(255, 255, 255);
    background: -moz-linear-gradient(top, rgba(255, 255, 255, 1) 0%, rgba(246, 246, 246, 1) 47%, rgba(237, 237, 237, 1) 100%);
    background: -webkit-gradient(linear, left top, left bottom, color-stop(0%, rgba(255, 255, 255, 1)), color-stop(47%, rgba(246, 246, 246, 1)), color-stop(100%, rgba(237, 237, 237, 1)));
    background: -webkit-linear-gradient(top, rgba(255, 255, 255, 1) 0%, rgba(246, 246, 246, 1) 47%, rgba(237, 237, 237, 1) 100%);
    background: -o-linear-gradient(top, rgba(255, 255, 255, 1) 0%, rgba(246, 246, 246, 1) 47%, rgba(237, 237, 237, 1) 100%);
    background: -ms-linear-gradient(top, rgba(255, 255, 255, 1) 0%, rgba(246, 246, 246, 1) 47%, rgba(237, 237, 237, 1) 100%);
    background: linear-gradient(to bottom, rgba(255, 255, 255, 1) 0%, rgba(246, 246, 246, 1) 47%, rgba(237, 237, 237, 1) 100%);
    filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#ffffff', endColorstr='#ededed', GradientType=0);
}
.checkedRadio {
    -moz-box-shadow: inset 0 0 5px 1px #ccc;
    -webkit-box-shadow: inset 0 0 5px 1px #ccc;
    box-shadow: inset 0 0 5px 1px #ccc;
}
.radio-btn i {
    border: 1px solid #E1E2E4;
    width: 10px;
    height: 10px;
    position: absolute;
    left: 4px;
    top: 4px;
    -webkit-border-radius: 100%;
    -moz-border-radius: 100%;
    border-radius: 100%;
}
.checkedRadio i {
    background-color: #898A8C;
}
```
```js
/*
    Custom checkbox and radio button - Jun 18, 2013
    (c) 2013 @ElmahdiMahmoud 
    license: http://www.opensource.org/licenses/mit-license.php
*/   
$('input[name="radio-btn"]').wrap('<div class="radio-btn"><i></i></div>');
$(".radio-btn").on('click', function () {
    var _this = $(this),
        block = _this.parent().parent();
    block.find('input:radio').attr('checked', false);
    block.find(".radio-btn").removeClass('checkedRadio');
    _this.addClass('checkedRadio');
    _this.find('input:radio').attr('checked', true);
});
$('input[name="check-box"]').wrap('<div class="check-box"><i></i></div>');
$.fn.toggleCheckbox = function () {
    this.attr('checked', !this.attr('checked'));
}
$('.check-box').on('click', function () {
    $(this).find(':checkbox').toggleCheckbox();
    $(this).toggleClass('checkedBox');
});
```

# Must have meta tag 

http://moz.com/blog/meta-data-templates-123

# Bootstrap slider

https://github.com/seiyria/bootstrap-slider

# Font convert

https://fontie.flowyapps.com/home