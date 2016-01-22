# Register shortcode

```php
/***
*** @listen to search
***/ 
add_shortcode('user_search','custom_user_search');
function custom_user_search($atts = null){

    $out = user_search_form();

    if ( isset($_GET['user_search']) && $_GET['user_search'] == "search_users" && $_GET['s_value'] != "" ){

        global $wpdb;     
        $args = array(              
            'meta_key'     => 'nickname',
            'meta_compare' => 'LIKE'
        );

        if ( isset($_GET['s_value']) ){
            $metavalue = $_GET['s_value'];
            $args['meta_value'] = $metavalue;
        }


        $search_users = get_users($args);

        $out .= '<div class="user_search_results">';
        if ( count($search_users) > 0){

            // here we loop over the users found and return whatever you want eg:
            $out .= '<ul class="alx-posts group">';
            foreach ($search_users as $user) {
                um_fetch_user($user->ID);
                $url = um_user_profile_url();
                um_reset_user();

                $out .= sprintf("<li><div class='post-item-inner group'><p class='post-item-title'><a href='%s'>%s (%s)</a></p></div></li>", $url, $user->user_nicename, $user->user_email);
            }
            $out .= '</ul>';
        }else{
            $out .= '<div class="alert alert-warning">No users found, try searching for something else.</div>';
        }
        $out .= '</div>';
    }
    return $out;
}
```

# Render search form

```php
/***
*** @render search form
***/ 
function user_search_form(){
    $metavalue = $metakey = '';
   
    if (isset($_GET['s_value'])){
        $metavalue = $_GET['s_value'];
    }
    $re = '<div class="user_search">
            <form action="" name="user_s" method="get">          
                <input id="s_value" name="s_value" type="text" value="'.$metavalue.'" placeholder="Input your keywords here" />
                <input name="user_search" id="user_search" type="hidden" value="search_users"/>
                <input id="submit" type="submit" value="Search" />
            </form>
            </div>';
    return $re;
}
```

# Stylesheet

```css
/* user_search
-------------------------------------------------------------- */

.user_search {
    margin-right: 75px;
    position: relative;
}
.user_search form {
    margin-bottom: 20px;
}
.user_search #s_value {
    width: 100%;
}
.user_search #submit {
    position: absolute;
    right: -75px;
    top: 0;
}

/* user_search -------------------------------------------------------------- */
```

# Using in template

```
<div class="well-form">
    <?php echo do_shortcode("[user_search]"); ?>
</div>
<?php if ( isset($_GET['user_search']) && $_GET['user_search'] == "search_users" && $_GET['s_value'] != "" ): ?>

<?php else: ?>
    
<?php endif; ?>
```