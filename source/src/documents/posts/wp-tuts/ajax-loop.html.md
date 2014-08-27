---
layout: 'content'
title: 'Getting Loopy - Ajax Powered Loops with jQuery and WordPress'
---

1. Tạo file loopHandler.php ( cùng thư mục file functions.php )

```php
// Our include
define('WP_USE_THEMES', false);
require_once('../../../wp-load.php');

// Storing GET Data as Variables in Our Handler.
$numPosts = (isset($_GET['numPosts'])) ? $_GET['numPosts'] : 0;
$page = (isset($_GET['pageNumber'])) ? $_GET['pageNumber'] : 0;

query_posts(array(
       'posts_per_page' => $numPosts,
       'paged'          => $page
));

 
// our loop
if (have_posts()) {
       while (have_posts()){
              the_post();
              get_template_part( 'content', get_post_format() );
       }
}
```

2. File ajaxLoop.js

```js
jQuery(function($){
    var page = 1;
    var loading = true;
    var $window = $(window);
    var $content = $("body.blog #content");
    var load_posts = function(){
            $.ajax({
                type       : "GET",
                data       : {numPosts : 1, pageNumber: page},
                dataType   : "html",
                url        : "http://WWW.YOURSITE.COM/wp-content/themes/YOUR_THEME_NAME/loopHandler.php",
                beforeSend : function(){
                    if(page != 1){
                        $content.append('<div id="temp_load" style="text-align:center">\
                            <img src="../images/ajax-loader.gif" />\
                            </div>');
                    }
                },
                success    : function(data){
                    $data = $(data);
                    if($data.length){
                        $data.hide();
                        $content.append($data);
                        $data.fadeIn(500, function(){
                            $("#temp_load").remove();
                            loading = false;
                        });
                    } else {
                        $("#temp_load").remove();
                    }
                },
                error     : function(jqXHR, textStatus, errorThrown) {
                    $("#temp_load").remove();
                    alert(jqXHR + " :: " + textStatus + " :: " + errorThrown);
                }
        });
    }
    $window.scroll(function() {
        var content_offset = $content.offset();
        console.log(content_offset.top);
        if(!loading && ($window.scrollTop() +
            $window.height()) > ($content.scrollTop() +
            $content.height() + content_offset.top)) {
                loading = true;
                page++;
                load_posts();
        }
    });
    load_posts();
});
```