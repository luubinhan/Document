---
layout: 'content'
title: 'Getting Loopy - Ajax Powered Loops with jQuery and WordPress'
---

File functions.php

```php
function wp_infinitepaginate(){
    $loopFile        = $_POST['loop_file'];
    $paged           = $_POST['page_no'];
    $posts_per_page  = get_option('posts_per_page');
 
    # Load the posts
    query_posts(array('paged' => $paged ));
    get_template_part( $loopFile );
 
    exit;
}

add_action('wp_ajax_infinite_scroll', 'wp_infinitepaginate');           // for logged in user
add_action('wp_ajax_nopriv_infinite_scroll', 'wp_infinitepaginate'); 
```

Header.php

```php

<!-- start infinite scroll function  -->

<?php if (!is_single() || !is_page()): ?>

<script type="text/javascript">
    jQuery(document).ready(function($) {
        var count = 2;
        var total = <?php echo $wp_query->max_num_pages; ?>;
        $(window).scroll(function(){
                if  ($(window).scrollTop() == $(document).height() - $(window).height()){
                   if (count > total){
                        return false;
                   }else{
                        loadArticle(count);
                   }
                   count++;
                }
        }); 

        function loadArticle(pageNumber){    
                $('a#inifiniteLoader').show('fast');
                $.ajax({
                    url: "<?php bloginfo('wpurl') ?>/wp-admin/admin-ajax.php",
                    type:'POST',
                    data: "action=infinite_scroll&page_no="+ pageNumber + '&loop_file=loop', 
                    success: function(html){
                        $('a#inifiniteLoader').hide('1000');
                        $("#content").append(html);    // This will be the div where our content will be loaded
                    }
                });
            return false;
        }

    });

</script>

<!-- end infinite scroll pagination -->
<?php endif; ?> 
```

https://github.com/paulirish/infinite-scroll