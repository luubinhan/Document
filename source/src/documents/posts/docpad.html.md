---
layout: 'content'
title: 'DocPad'
description: 'Streamlined Web Development'
---

#### Table of Content
-------------
<!-- MarkdownTOC depth=2 -->

- Install
- Get all file in posts/wordpress

<!-- /MarkdownTOC -->


# Install

```
mkdir my-new-web
cd my-new-web
docpad run
```

# Get all file in posts/wordpress

```html
<% for document in  @getFilesAtPath( @getPath("wordpress", "posts")).toJSON(): %>
    <li>
    <a href="<%= document.url %>"><%= document.title %></a></li>
<% end %>
```















