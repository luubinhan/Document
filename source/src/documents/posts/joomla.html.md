---
layout: 'content'
title: 'Joomla'
description: Note for Joomla
---

#### Table of content
-------------

<!-- MarkdownTOC depth=2 -->

- GRUNTJS SETUP ERROR
- Truncate string PHP
- Get first image as thumbnail
- Change joomla pagination
- ROUTE ARTICLE
- Escape string
- stripslashes
- Get date of week
- Create new component
- Change XAMPP IP
- Get Page Alias

<!-- /MarkdownTOC -->


# GRUNTJS SETUP ERROR

<code>path=%PATH%;%APPDATA%\npm</code>

# Truncate string PHP

```php
echo substr($product_s_desc, 0, strpos(wordwrap($product_s_desc, 150), "\n"));
```


# Get first image as thumbnail

```php
preg_match('/<img (.*?)>/', $this->item->text, $match); ?><a href="<?php echo $this->item->readmore_link; ?>"><?php echo $match[0]; ?></a>
```

# Change joomla pagination

http://www.slurpitup.com/joomla/tips-and-tricks/how-to-style-default-joomla-pagination-with-css

# ROUTE ARTICLE

```php
echo JRoute::_(ContentHelperRoute::getArticleRoute($this->item->id));
```

# Escape string

```php
 $this->escape($this->searchword)
```

# stripslashes

# Get date of week 

$dw = date( "w" );

# Create new component

http://www.joomladevuser.com/tutorials/components/component-dev-parti

# Change XAMPP IP

Stop the XAMPP server, if it is running already.
Open the file [XAMPP Installation Folder]/apache/conf/httpd.conf.
Search for the string *Listen 80 *(I'm assuming that your XAMPP was using the port 80.
Otherwise, just search for the string 'Listen'). This is the port number which XAMPP uses.
Change this 80 to 172.31.1.3:80.
Now save and re-start XAMPP server and you are done.

# Get Page Alias

```php
function getCurrentAlias()
{
   $path = JFactory::getURI()->getPath();
   $length = strlen($path);
   
   for ($i = $length; $i >= 0 ; $i--)
      if ($path[$i] == '/')
         return substr($path, $i + 1, $length - $i - 1);

   return $path;
}
```