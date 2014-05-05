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

