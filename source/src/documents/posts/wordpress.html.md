---
layout: 'content'
title: 'Wordpress'
description: Wordpress Snip Code
---

#### Table of content

Wordpress Snip Code
----------------------

<!-- MarkdownTOC depth=2 -->

- Get post feature image
- Get option from admin
- Thêm VND vào WOO
- Get related post
- Tùy biến chữ readmore
- Get page slug
- Get post id
- jax
- Get product object woocommerce
- update cart ajax
- Make field not required
- Bỏ bớt menu WooCommerce
- Get template part woocommerce
- Get product price
- Convert to lower case
- Get Product Category
- Trang shop online
- Đăng ký sidebar
- ordPress add class to parent element if has submenu
- Change post name
- Recruitment Register
- Sử dụng biến trên khởi tạo ở trang cha trên trang con
- Get Various WooCommerce Page URLs
- Get slug trên trang archieve
- Khắc phục lỗi không thể gởi mail với host việt nam
- Get Thumbnail URL
- Tạo widget
- Đăng ký thêm vị trí menu
- Get term custom term link
- Get regular price woocommerce
- Giảm theo số lượng sản phẩm trong giỏ hàng
- Add support feature image for post and page
- woo_breadcrumbs
- Querying by Post Type
- Get Global post id
- Remove column
    - Wordpress SEO
- Optimize Contact Form 7
- Add google map
- Make Clickable
- Add shortcodes in sidebar Widgets
- Thêm cột trong admin // ADD COLUMN IN ADMIN
    - Để hiển thị hình ảnh
    - Để cột có thể sắp xếp
- Permalink structrue ending .html
- Tao shortcode
- Thêm class cho widget
- Remove Width and Height Attributes From Inserted Images
- WooCommerce : Remove Review tab
- Convert string to date
- Get the taxonomy (use as category)
- Get next/previous product
- Lấy ngẫu nhiên danh sách post liên quan với post hiện tại
- LOAD DASH ICON IN THEME
- Woocommerce - Thêm nút clear giỏ hàng
- get number of items in cart woocommerce
- Paging
- Get post date in loop
- Hiển thị Widget Cart trên tất cả các trang
- woocommerce custom ajax top cart
- Redirect login problem
- Woocommerce: get all categories
- Convert string to slug
- User không thể print invoice
- Thêm array động trong php
- check if admin
- Add discount/fee woocommerce
- Paging problem with custom taxonomi
- Make wordpress portable
- Include plugin từ theme
- Bắt buộc cài plugin sau khi cài theme
- Disable WordPress Heartbeat API
- Fix option tree textarea issue
- breadcrumbs
- ACF Repeater template
- Remove button from the TinyMCE
- Gallery Option tree
- Get all categories woocommerce
- Get the excert outside the loop
- Woocomerce change city to dropdown field
- FILTER NOT GET CURRENT POST
- REMOVE SUBMENU NINJA FORM
- REMOVE NINJA FORM METABOX
- FORMAT DATE FROM STRING
- Create Front-End login
- Posting in front-end
- GET FRONT PAGE ID
- CUSTOM SUB-MENU CLASS
- Display user name on menu
- Limit search
- Enqueue JQUERY
- Add to cart url
- GET BEST SELLER PRODUCT
- LOGOUT MENU
- Get products by categories
- Remove un use class body class

<!-- /MarkdownTOC -->


# Get post feature image

```php
    $url = wp_get_attachment_url( get_post_thumbnail_id($post->ID, 'thumbnail') );
    <img src="<?php echo $url ?>" title="<?php the_title(); ?>" alt="<?php the_title(); ?>" />


echo '<img alt="" src="' . get_thumbnail_src( get_the_ID() ) . '" />';

function get_thumbnail_src( $post = false ) {

    if (  false === $post ) {
        $post = get_the_ID();
    } else if ( is_object( $post ) && isset( $post->ID ) ) {
        $post = $post->ID;
    } else if ( is_array( $post ) && isset( $post['ID'] ) ) {
        $post = $post['ID'];
    }
    
    $thumb_id = get_post_thumbnail_id( $post );
    $src = wp_get_attachment_thumb_url( $thumb_id );
    
    return $src;
    
}
```

# Get option from admin
```php
<?php 
$settings = array(
            'thumb_w' => 787, 
            'thumb_h' => 300, 
            'thumb_align' => 'alignleft'
            );
            
$settings = woo_get_dynamic_values( $settings );
 ?>
```

Chỉ lấy một giá trị

```php
global $woo_options;

$woo_options['woo_brand_logo']
```

# Thêm VND vào WOO

```php

add_filter( 'woocommerce_currencies', 'add_my_currency' );

function add_my_currency( $currencies ) {
     $currencies['VNĐ'] = __( 'Vietnam dong (đ)', 'VNĐ' );
     return $currencies;
}

add_filter('woocommerce_currency_symbol', 'add_my_currency_symbol', 10, 2);

function add_my_currency_symbol( $currency_symbol, $currency ) {
     switch( $currency ) {
          case 'VNĐ': $currency_symbol = ' VNĐ'; break;
     }
     return $currency_symbol;
}

```


# Get related post

```php

    $related = get_posts( array( 'category__in' => wp_get_post_categories($post->ID), 'numberposts' => 5, 'post__not_in' => array($post->ID) ) );
    if( $related )
        echo "<hr /><h3>Đọc thêm </h3>";
        foreach( $related as $post ) {
            setup_postdata($post); ?>
            <ul> 
                <li>
                <a href="<?php the_permalink() ?>" rel="bookmark" title="<?php the_title(); ?>"><?php the_title(); ?></a>
                </li>
            </ul>   
            <?php 
        }
    wp_reset_postdata(); 
```

# Tùy biến chữ readmore

```php
function new_excerpt_more( $more ) {
    return '[.....]';
}
add_filter('excerpt_more', 'new_excerpt_more');
```

# Get page slug

``` php 
    global $post;
    $slug = get_post( $post )->post_name;
```

# Get post id

```php
    get_the_ID()
```

#Ajax

```js
$('span.preview').click(function(){
        var $productID = $(this).parent().parent().data('product-id');

        $.ajax({
            url: "wp-admin/admin-ajax.php",
            type: 'POST',
            data: 'action=preview_product&proID=' + $productID,
            success: function(data, textStatus, XMLHttpRequest){
                if( textStatus === 'success' ){
                    $data = data;
                    console.log($data);
                }
            }
        });
    });
```
```php 
    add_action( "wp_ajax_preview_product", "do_preview_product" );
    function do_preview_product(){
     
            $proID = $_POST['proID'];
            $data;

            if( $proID !== ''){
                $data =get_post( $proID ) ;
                echo $data->post_title;
            }
            die ();
        //die ($data);
    }
```

# Get product object woocommerce

```php 
    $product = get_product( $post->ID );
```

# update cart ajax

```php
//update cart ajax
function my_update_cart(){
  global $woocommerce;
  $my_cart = "";

  $my_cart .= $woocommerce->cart->cart_contents_count ." - " .$woocommerce->cart->get_cart_total(); 
  
  echo $my_cart;

}

add_action('wp_ajax_update_cart_action','my_update_cart');
add_action('wp_ajax_nopriv_update_cart_action', 'my_update_cart');
```

# Make field not required

```php
add_filter( 'woocommerce_billing_fields', 'wc_npr_filter_phone', 10, 1 );
 
function wc_npr_filter_phone( $address_fields ) {
$address_fields['billing_phone']['required'] = false;
return $address_fields;
}
```

# Bỏ bớt menu WooCommerce

```
Plugin Folder/admin/woocommerce-admin-init.php
```

# Get template part woocommerce

```php
woocommerce_get_template_part()
```

# Get product price 

```php
<?php woocommerce_get_template( 'loop/price.php' ); ?>
```

# Convert to lower case

```php
strtolower();
```

# Get Product Category

```php
<?php echo $product->get_categories(); ?>
```

# Trang shop online

Plugin > Woo Commerce > Template > Archieve product

# Đăng ký sidebar

Thêm vào file functions.php

```php
/* REGIS SHOP SIDEBAR
-------------------------------------------------------------- */
function regis_shop_sidebar(){
    register_sidebar(array(
        'name'          => __( 'Shop Sidebar' ),
        'id'            => 'shop-sidebar',
        'description'   => __( 'Widget hiển thị trên các trang sản phẩm' ),
        'before_title'  => '<h3>',
        'after_title'   => '</h3>',
        'before_widget' => '<div id="%1$s" class="widget %2$s">',
        'after_widget'  => '</div>',    
    ));    
}

add_action( 'widgets_init', 'regis_shop_sidebar' );
```

Tạo file sidebar-shop.php

```html
<div class="sidebar">
    <?php if ( woo_active_sidebar( 'shop-sidebar' ) ) { ?>
    <div class="primary">
        <?php woo_sidebar( 'shop-sidebar' );  ?>
    </div>        
    <?php } // End IF Statement ?>   
    
</div><!-- /#sidebar -->
```

#WordPress add class to parent element if has submenu 

```php
function menu_set_dropdown( $sorted_menu_items, $args ) {
    $last_top = 0;
    foreach ( $sorted_menu_items as $key => $obj ) {
        // it is a top lv item?
        if ( 0 == $obj->menu_item_parent ) {
            // set the key of the parent
            $last_top = $key;
        } else {
            $sorted_menu_items[$last_top]->classes['dropdown'] = 'dropdown';
        }
    }
    return $sorted_menu_items;
}
add_filter( 'wp_nav_menu_objects', 'menu_set_dropdown', 10, 2 );
```

# Change post name

```php
add_filter('gettext', 'change_post_to_article');
add_filter('ngettext', 'change_post_to_article');
function change_post_to_article($translated) {
    $translated = str_ireplace('Post', 'New', $translated);
    return $translated;
}
```

# Recruitment Register

```php
require_once ( get_template_directory() . '/inc/recruitment.php' );
```

# Sử dụng biến trên khởi tạo ở trang cha trên trang con

Ví dụ khai báo biến $i trên trang cha
```php
<?php $i = 0; ?>
```

Đừng sử dụng get_template_part(), sử dụng, locate_template()

```php
<?php include(locate_template('content-video.php')); ?>
```

Trên trang con có thể sử dụng biến $i trên trang cha

```php
<?php if( ($i % 5) == 0 ): ?>
    <div id="post-<?php the_ID(); ?>" <?php post_class('post-video alpha');?> >
<?php else: ?>
    <div id="post-<?php the_ID(); ?>" <?php post_class('post-video');?> >
<?php endif; ?>
```

# Get Various WooCommerce Page URLs

```php
<?php $shop_page_url = get_permalink( woocommerce_get_page_id( 'shop' ) ); ?>
```

- $myaccount_page_id = get_option( 'woocommerce_myaccount_page_id' );
- $payment_page = get_permalink( woocommerce_get_page_id( 'pay' ) );
- $myaccount_page_id = get_option( 'woocommerce_myaccount_page_id' );
- global $woocommerce;
$checkout_url = $woocommerce->cart->get_checkout_url();
global $woocommerce;
$cart_url = $woocommerce->cart->get_cart_url();

# Get slug trên trang archieve

```php
$term = get_term_by( 'slug', get_query_var( 'term' ), get_query_var( 'taxonomy' ) );
echo $term->slug;
```

# Khắc phục lỗi không thể gởi mail với host việt nam 

use plugin WP Email SMTP

# Get Thumbnail URL

```php
    $thumb = wp_get_attachment_image_src( get_post_thumbnail_id($post->ID), 'thumbnail' );
    $url = $thumb['0'];
    echo $url;
```

# Tạo widget

Chép vào function.php

```php

class MyStyle extends WP_Widget {
         public function __construct() {
            // widget actual processes
            parent::WP_Widget(false,'Tài khoản ngân hàng','description=Hiển thị danh sách tài khoản ngân hàng');
        }

        public function form( $instance ) {
               // outputs the options form on admin
        }

        public function update( $new_instance, $old_instance ) {
               // processes widget options to be saved
        }

        public function widget( $args, $instance ) {
               // outputs the content of the widget
            echo $before_widget;  

            global $woo_options;
            $settings = array(
                'chu_tk_vietcombank' => '',    
                'so_tk_vietcombank'  => '',    
                'chu_tk_donga'       => '',    
                'so_tk_donga'        => ''   
            );
            
            $settings = woo_get_dynamic_values( $settings );
           
            echo '<h3>Tài khoản Vietcombank</h3>';
            echo '<div class="menu-nav-help-container">';
                echo '<dl class="dl-horizontal">';
                    echo  '<dt>Chủ tài khoản:</dt>';
                        echo '<dd>'.$settings['chu_tk_vietcombank'].'</dd>';
                    echo   '<dt>Số tài khoản:</dt>';
                        echo  '<dd>'.$settings['so_tk_vietcombank'].'</dd>';
                        echo '</dl>';
                        echo '<h3>Tài khoản Đông á </h3>';
                        echo '<dl class="dl-horizontal">';
                        echo '<dt>Chủ tài khoản:</dt>';
                            echo '<dd>'.$settings['chu_tk_donga'].'</dd>';
                        echo  '<dt>Số tài khoản:</dt>';
                    echo '<dd>' .$settings['so_tk_donga'].'</dd>';
                echo '</dl>';
            echo '</div>';

            echo $after_widget;
        }

}
register_widget( 'MyStyle' );
```

1. Vào thư mục <code>includes/widgets</code> duplicate file widget-woo-search.php
2. <code>includes/theme-widgets.php</code> duplicate dòng
    <code>'includes/widgets/widget-woo-subscribe.php'</code>


# Đăng ký thêm vị trí menu

<code>theme directory / includes / theme-functions.php</code>

Search register_nav_menus

```php
if ( function_exists( 'wp_nav_menu') ) {
  add_theme_support( 'nav-menus' );
  register_nav_menus( array( 'primary-menu' => __( 'Primary Menu', 'devinition' ) ) );
  register_nav_menus( array( 'home-menu' => __( 'Home Menu', 'devinition' ) ) );
}
```

# Get term custom term link

```php
    $terms = get_terms('phanloai');
    echo '<ul>';
    foreach ($terms as $term) {
        //Always check if it's an error before continuing. get_term_link() can be finicky sometimes
        $term_link = get_term_link( $term, 'ao-thun' );
        if( is_wp_error( $term_link ) )
            continue;
        //We successfully got a link. Print it out.
        echo '<li><a href="' . $term_link . '">' . $term->name . '</a></li>';
    }
    echo '</ul>';
```

# Get regular price woocommerce

```php
    $regular_price = get_post_meta($_product->id,'_regular_price', true);
```

# Giảm theo số lượng sản phẩm trong giỏ hàng 

```php 
function mysite_box_discount( ) {
  
    global $woocommerce;
 
    /* Grab current total number of products */
    $number_products = $woocommerce->cart->cart_contents_count;
   
    $total_discount = 0;
    $my_increment = 5; // Apply another discount every 15 products
    $discount = 8.85;
    
    if ($number_products >= $my_increment) {
        
      /* Loop through the total number of products */
      foreach ( $woocommerce->cart->cart_contents as $cart_item_key => $values ) {
        $_product = $values['data'];

        $regular_price = get_post_meta($_product->id,'_regular_price', true);
        $retail_price = $_product->get_price();

        $total_discount += ( $retail_price - $regular_price ) * $values['quantity'];

      }
   
      // Alter the cart discount total
      $woocommerce->cart->discount_total = $total_discount;
    }   
}
add_action('woocommerce_calculate_totals', 'mysite_box_discount');
```

# Add support feature image for post and page

```php
/*  Add support for Featured Images
-------------------------------------------------------------- */

if (function_exists('add_theme_support')) {
    add_theme_support( 'post-thumbnails', array( 'post', 'page' ) );
    add_image_size('index-categories', 694, 150, true);
}
```

# woo_breadcrumbs

- separator – The character to display between the breadcrumbs.
- before – HTML to display before the breadcrumbs.
- after – HTML to display after the breadcrumbs.
- front_page – Include the front page at the beginning of the breadcrumbs.
- show_home – If $show_home is set and we’re not on the front page of the site, link to the home page.
- echo – Specify whether or not to echo the breadcrumbs. Alternative is “return”.
- show_posts_page – If a static front page is set and there is a posts page, toggle whether or not to display that page’s tree.

# Querying by Post Type 

```php
$args = array( 'post_type' => 'product', 'posts_per_page' => 10 );
$loop = new WP_Query( $args );
while ( $loop->have_posts() ) : $loop->the_post();
    the_title();
    echo '<div class="entry-content">';
    the_content();
    echo '</div>';
endwhile;
```

# Get Global post id

```php
$post_id = $GLOBALS['post']->ID;
```

# Remove column 

## Wordpress SEO

```php
add_filter( 'wpseo_use_page_analysis', '__return_false' );
```


# Optimize Contact Form 7

```php
// Deregister Contact Form 7 styles
add_action( 'wp_print_styles', 'aa_deregister_styles', 100 );
function aa_deregister_styles() {
    if ( ! is_page( 'contact-us' ) ) {
        wp_deregister_style( 'contact-form-7' );
    }
}

// Deregister Contact Form 7 JavaScript files on all pages without a form
add_action( 'wp_print_scripts', 'aa_deregister_javascript', 100 );
function aa_deregister_javascript() {
    if ( ! is_page( 'contact-us' ) ) {
        wp_deregister_script( 'contact-form-7' );
    }
}
```

# Add google map

File google-map.php

```js
<div id="googleMap"></div>

<script type="text/javascript" src="http://maps.google.com/maps/api/js?sensor=false"></script>
<script type="text/javascript">
//<![CDATA[
var geocoder = new google.maps.Geocoder();
var address = ""; //Add your address here, all on one line.
var latitude;
var longitude;
var color = ""; //Set your tint color. Needs to be a hex value.

function getGeocode() {
    geocoder.geocode( { 'address': address}, function(results, status) {
        if (status == google.maps.GeocoderStatus.OK) {
            latitude = results[0].geometry.location.lat();
            longitude = results[0].geometry.location.lng(); 
            initGoogleMap();   
        } 
    });
}

function initGoogleMap() {
    var styles = [
        {
          stylers: [
            { saturation: -100 }
          ]
        }
    ];
    
    var options = {
        mapTypeControlOptions: {
            mapTypeIds: ['Styled']
        },
        center: new google.maps.LatLng(latitude, longitude),
        zoom: 13,
        scrollwheel: false,
        navigationControl: false,
        mapTypeControl: false,
        zoomControl: true,
        disableDefaultUI: true, 
        mapTypeId: 'Styled'
    };
    var div = document.getElementById('googleMap');
    var map = new google.maps.Map(div, options);
    marker = new google.maps.Marker({
        map:map,
        draggable:false,
        animation: google.maps.Animation.DROP,
        position: new google.maps.LatLng(latitude,longitude)
    });
    var styledMapType = new google.maps.StyledMapType(styles, { name: 'Styled' });
    map.mapTypes.set('Styled', styledMapType);
    
    var infowindow = new google.maps.InfoWindow({
          content: "<div class='iwContent'>"+address+"</div>"
    });
    google.maps.event.addListener(marker, 'click', function() {
        infowindow.open(map,marker);
      });
    
    
    bounds = new google.maps.LatLngBounds(
      new google.maps.LatLng(-84.999999, -179.999999), 
      new google.maps.LatLng(84.999999, 179.999999));

    rect = new google.maps.Rectangle({
        bounds: bounds,
        fillColor: color,
        fillOpacity: 0.2,
        strokeWeight: 0,
        map: map
    });
}
google.maps.event.addDomListener(window, 'load', getGeocode);
//]]>
</script>

```

Add to your template

```php
<?php get_template_part( 'google-map'); ?>
```

css

```css
#googleMap iframe {
   width: 100%;
}
#googleMap {
   height: 350px;
}
#googleMap img { max-width: none; }
```

# Make Clickable

make_clickable()


# Add shortcodes in sidebar Widgets

add_filter('widget_text', 'do_shortcode');

# Thêm cột trong admin // ADD COLUMN IN ADMIN

```php

function add_table_columns( $columns ) { 
    $columns['email_address'] = __( 'Email Address', 'tuts-crm' );
    $columns['phone_number'] = __( 'Phone Number', 'tuts-crm' );
    $columns['photo'] = __( 'Photo', 'tuts-crm' );
     
    return $columns;
     
}
add_filter( 'manage_edit-{Post Type}_columns', 'add_table_columns',10, 1 );
function output_table_columns_data( $columnName, $post_id ) {
    echo get_field( $columnName, $post_id );   
}
add_action( 'manage_{Post Type}_posts_custom_column', 'output_table_columns_data', 10, 2 );
```

Các giá trị phone_number tương ứng với id của ACF

## Để hiển thị hình ảnh

```php
function output_table_columns_data( $columnName, $post_id ) {
 
    // Field
    $field = get_field( $columnName, $post_id );
     
    if ( 'photo' == $columnName ) {
        echo '<img src="' . $field['sizes']['thumbnail'].'" width="'.$field['sizes']['thumbnail-width'] . '" height="' . $field['sizes']['thumbnail-height'] . '" />';
    } else {
        // Output field
        echo $field;
    }
     
}
```

## Để cột có thể sắp xếp

```php
function define_sortable_table_columns( $columns ) {
 
    $columns['email_address'] = 'email_address';
    $columns['phone_number'] = 'phone_number';
     
    return $columns;
     
}
 if ( is_admin() ) {
        add_filter( 'request', array( $this, 'orderby_sortable_table_columns' ) );
    }
/**
* Inspect the request to see if we are on the Contacts WP_List_Table and attempting to
* sort by email address or phone number.  If so, amend the Posts query to sort by
* that custom meta key
*
* @param array $vars Request Variables
* @return array New Request Variables
*/
function orderby_sortable_table_columns( $vars ) {
 
    // Don't do anything if we are not on the Contact Custom Post Type
    if ( 'contact' != $vars['post_type'] ) return $vars;
     
    // Don't do anything if no orderby parameter is set
    if ( ! isset( $vars['orderby'] ) ) return $vars;
     
    // Check if the orderby parameter matches one of our sortable columns
    if ( $vars['orderby'] == 'email_address' OR
        $vars['orderby'] == 'phone_number' ) {
        // Add orderby meta_value and meta_key parameters to the query
        $vars = array_merge( $vars, array(
            'meta_key' => $vars['orderby'],
            'orderby' => 'meta_value',
        ));
    }
     
    return $vars;
     
}
add_filter( 'manage_edit-contact_sortable_columns', array( $this, 'define_sortable_table_columns') );
```

# Permalink structrue ending .html 

```php
add_action( 'rewrite_rules_array', 'rewrite_rules' );
function rewrite_rules( $rules ) {
    $new_rules = array();
    foreach ( get_post_types() as $t )
        $new_rules[ $t . '/([^/]+)\.html$' ] = 'index.php?post_type=' . $t . '&name=$matches[1]';
    return $new_rules + $rules;
}

add_filter( 'post_type_link', 'custom_post_permalink' ); // for cpt post_type_link (rather than post_link)

function custom_post_permalink ( $post_link ) {
    global $post;
    $type = get_post_type( $post->ID );
    return home_url( $type . '/' . $post->post_name . '.html' );
}

add_filter( 'redirect_canonical', '__return_false' );

```

# Tao shortcode

```php
function recent_posts_function() {
   query_posts(array('orderby' => 'date', 'order' => 'DESC' , 'showposts' => 1));
   if (have_posts()) :
      while (have_posts()) : the_post();
         $return_string = '<a href="'.get_permalink().'">'.get_the_title().'</a>';
      endwhile;
   endif;
   wp_reset_query();
   return $return_string;
}

function register_shortcodes(){
   add_shortcode('recent-posts', 'recent_posts_function');
}

add_action( 'init', 'register_shortcodes');

[recent-posts]
```

# Thêm class cho widget

```php
register_sidebar(array(
    'id' => 'sidebar1',
    'name' => 'Sidebar (Main)',
    'description' => 'Primary sidebar',
    'before_widget' => '<div id="%1$s" class="widget %2$s">',
    'after_widget' => '</div>',
    'before_title' => '<h3 class="widgettitle">',
    'after_title' => '</h3>',
    'class' => 'clearfix'
));
```

# Remove Width and Height Attributes From Inserted Images

```php
add_filter( 'post_thumbnail_html', 'remove_width_attribute', 10 );
add_filter( 'image_send_to_editor', 'remove_width_attribute', 10 );

function remove_width_attribute( $html ) {
   $html = preg_replace( '/(width|height)="\d*"\s/', "", $html );
   return $html;
}
```

# WooCommerce : Remove Review tab

```php
add_filter( 'woocommerce_product_tabs', 'sb_woo_remove_reviews_tab', 98);
function sb_woo_remove_reviews_tab($tabs) {

    unset($tabs['reviews']);
    unset($tabs['description']);                
    unset($tabs['additional_information']);    

    return $tabs;
}
```

# Convert string to date

```php
echo $display_date = date('d F, Y', strtotime(get_field('product_start_date')));
```

# Get the taxonomy (use as category)

```php
$terms = get_the_terms( $post->ID, 'product_cat' );
$term = array_pop($terms);
echo '<a href="'.get_term_link($term->slug, 'product_cat').'">'.$term->name.'</a>';
```

# Get next/previous product

<?php
// get next and prev products
// Author: Georgy Bunin (bunin.co.il@gmail.com)
// forked from https://gist.github.com/2176823

function ShowLinkToProduct($post_id, $categories_as_array, $label) {
    // get post according post id
    $query_args = array( 'post__in' => array($post_id), 'posts_per_page' => 1, 'post_status' => 'publish', 'post_type' => 'product', 'tax_query' => array(
        array(
            'taxonomy' => 'product_cat',
            'field' => 'id',
            'terms' => $categories_as_array
        )));
    $r_single = new WP_Query($query_args);
    if ($r_single->have_posts()) {
        $r_single->the_post();
        global $product;
    ?>
    <ul class="product_list_widget">
        <li><a href="<?php the_permalink() ?>" title="<?php echo esc_attr(get_the_title() ? get_the_title() : get_the_ID()); ?>">
            <?php if (has_post_thumbnail()) the_post_thumbnail('shop_thumbnail'); else echo '<img src="'. woocommerce_placeholder_img_src() .'" alt="Placeholder" width="'.$woocommerce->get_image_size('shop_thumbnail_image_width').'" height="'.$woocommerce->get_image_size('shop_thumbnail_image_height').'" />'; ?>
            <?php echo $label; ?>
            <?php if ( get_the_title() ) the_title(); else the_ID(); ?>
        </a> <?php echo $product->get_price_html(); ?></li>
    </ul>
    <?php
        wp_reset_query();
    }
}

if ( is_singular('product') ) {
    global $post;

    // get categories
    $terms = wp_get_post_terms( $post->ID, 'product_cat' );
    foreach ( $terms as $term ) $cats_array[] = $term->term_id;

    // get all posts in current categories
    $query_args = array('posts_per_page' => -1, 'post_status' => 'publish', 'post_type' => 'product', 'tax_query' => array(
        array(
            'taxonomy' => 'product_cat',
            'field' => 'id',
            'terms' => $cats_array
        )));
    $r = new WP_Query($query_args);

    // show next and prev only if we have 3 or more
    if ($r->post_count > 2) {

        $prev_product_id = -1;
        $next_product_id = -1;

        $found_product = false;
        $i = 0;

        $current_product_index = $i;
        $current_product_id = get_the_ID();

        if ($r->have_posts()) {
            while ($r->have_posts()) {
                $r->the_post();
                $current_id = get_the_ID();

                if ($current_id == $current_product_id) {
                    $found_product = true;
                    $current_product_index = $i;
                }

                $is_first = ($current_product_index == $first_product_index);

                if ($is_first) {
                    $prev_product_id = get_the_ID(); // if product is first then 'prev' = last product
                } else {
                    if (!$found_product && $current_id != $current_product_id) {
                        $prev_product_id = get_the_ID();
                    }
                }

                if ($i == 0) { // if product is last then 'next' = first product
                    $next_product_id = get_the_ID();
                }

                if ($found_product && $i == $current_product_index + 1) {
                    $next_product_id = get_the_ID();
                }

                $i++;
            }

            if ($prev_product_id != -1) { ShowLinkToProduct($prev_product_id, $cats_array, "next: "); }
            if ($next_product_id != -1) { ShowLinkToProduct($next_product_id, $cats_array, "prev: "); }
        }

        wp_reset_query();
    }
}
?>
<?php previous_post_link('&laquo; %link'); ?>    
<?php next_post_link('%link &raquo;'); ?> 

# Lấy ngẫu nhiên danh sách post liên quan với post hiện tại

```php
$terms = get_the_terms( $post->ID, 'product_cat' );
$term = array_pop($terms);  

$args = array(
    'post_type'            => 'product',
    'ignore_sticky_posts'  => 1,
    'no_found_rows'        => 1,
    'posts_per_page'       => 3,
    'orderby'              => 'rand',
    'tax_query' => array(
        array(
            'taxonomy'  => 'product_cat',
            'field'     => 'slug',
            'terms'     => $term,
            'operator'  => 'IN'
        )
    ),
    'post__not_in'         => array( $product->id )
);

$products = new WP_Query( $args );
```

# LOAD DASH ICON IN THEME

```php
add_action( 'wp_enqueue_scripts', 'themename_scripts' );
function themename_scripts() {
    wp_enqueue_style( 'themename-style', get_stylesheet_uri(), array( 'dashicons' ), '1.0' );
}
```

Xem code icon ở đây: http://melchoyce.github.io/dashicons/
https://developer.wordpress.org/resource/dashicons

# Woocommerce - Thêm nút clear giỏ hàng

```
// Add the Empty Cart button right before the "Continue to Checkout" button
add_action( 'woocommerce_proceed_to_checkout', 'iwc_clear_cart_contents_button' );
function iwc_clear_cart_contents_button() {
    // HTML for our new button
    echo '<input type="submit" class="button" name="empty_cart" value="Empty Cart" />';
}

add_action( 'woocommerce_before_cart', 'iwc_clear_cart_contents' );
function iwc_clear_cart_contents() {
    // check whether or not this button was the one pressed
    if( isset( $_POST['empty_cart'] ) ) {
        global $woocommerce;
        // Go ahead and empty the cart
        $woocommerce->cart->empty_cart();
        // Finally redirect to your Shop Page since the Cart is now empty
        wp_safe_redirect( get_permalink( woocommerce_get_page_id( 'shop' ) ) );
    }
}

```

# get number of items in cart woocommerce

<?php global $woocommerce; ?>

<a class="cart-contents" href="<?php echo $woocommerce->cart->get_cart_url(); ?>" title="<?php _e('View your shopping cart', 'woothemes'); ?>"><?php echo sprintf(_n('%d item', '%d items', $woocommerce->cart->cart_contents_count, 'woothemes'), $woocommerce->cart->cart_contents_count);?> - <?php echo $woocommerce->cart->get_cart_total(); ?></a>

# Paging

```php
                                                                         
$args = array( 
    'post_type' => 'client-logo', 
    'posts_per_page' => 20,
    'paged' => get_query_var('paged')
 
);
$loop = new WP_Query( $args );
wp_pagenavi( array( 'query' => $loop ) );
wp_reset_query();
```

# Get post date in loop

```php
    get_the_date( $d ); 
```

$d
- l, F j, Y :Friday, September 24, 2004
-  l, F jS, Y - Saturday, November 6th, 2010 
-  F j, Y g:i a - November 6, 2010 12:50 am 

http://codex.wordpress.org/Formatting_Date_and_Time

# Hiển thị Widget Cart trên tất cả các trang

file <code>class-wc-widget-cart.php</code>

```php
if ( is_cart() || is_checkout() ) return;  
```

Edit: Additional information how to override widget and make changes update secure
Source: http://www.skyverge.com/blog/overriddin-woocommerce-widgets/ (Option 5)

    Duplicate class-wc-widget-cart.php;
    Copy the duplicate into a folder inside your theme, for example: cust_woo_widgets
    Make above changes to the file;

    Additionally make the following change to the widget duplicate:

    class Custom_WooCommerce_Widget_Cart extends WooCommerce_Widget_Cart {
      function widget( $args, $instance ) {
    // copy the widget function from woocommerce/classes/widgets/class-wc-widget-cart.php
      }
    }

    Put following code into your functions.php:

    add_action( 'widgets_init', 'override_woocommerce_widgets', 15 );
    function override_woocommerce_widgets() { 
      if ( class_exists( 'WooCommerce_Widget_Cart' ) ) {
        unregister_widget( 'WooCommerce_Widget_Cart' ); 
        include_once( 'cust_woo_widgets/widget-cart.php' );
        register_widget( 'Custom_WooCommerce_Widget_Cart' );
      } 
    }

Note: See source for more information; untested.

# woocommerce custom ajax top cart

http://stackoverflow.com/questions/14675292/woocommerce-custom-ajax-top-cart

# Redirect login problem

add_query_arg( array('key1' => 'value1', ...), $old_query_or_uri );

# Woocommerce: get all categories 

```php
woocommerce_product_categories();

//or
$args = array(
    'number'     => $number,
    'orderby'    => $orderby,
    'order'      => $order,
    'hide_empty' => $hide_empty,
    'include'    => $ids
);

$product_categories = get_terms( 'product_cat', $args );
```

# Convert string to slug

sanitize_title();

# User không thể print invoice

```php
//xóa dòng sau trong plugin

if( !is_admin() ) {
    wp_die( __( 'You do not have sufficient permissions to access this page.' ) );
}

if( !current_user_can( 'manage_woocommerce_orders' ) && !current_user_can( 'edit_shop_orders' ) ) {
    wp_die( __( 'You do not have sufficient permissions to access this page.' ) );
}
```

# Thêm array động trong php

```php
$array = array();
Add to an array:

$array[] = "item";
$array[$key] = "item";
array_push($array, "item", "another item");
Remove from an array:

$item = array_pop($array);
$item = array_shift($array);
unset($array[$key]);
```

# check if admin

current_user_can( 'manage_options' )

# Add discount/fee woocommerce

```php
add_action( 'woocommerce_cart_calculate_fees','RuleShouldDiscountAdministrationFee' );
function RuleShouldDiscountAdministrationFee() {
    global $woocommerce;

    if ( is_admin() && ! defined( 'DOING_AJAX' ) )
        return;

    $percentage = 0.01;
    $surcharge = ( $woocommerce->cart->cart_contents_total + $woocommerce->cart->shipping_total ) * $percentage;    
    $woocommerce->cart->add_fee( 'Surcharge', $surcharge, true, 'standard' );

}
// discount
$discount = floatval(10);
$discount *= -1; // convert positive to negative fees
```

# Paging problem with custom taxonomi

```php
function jetstream_rewrite_flush() {
    flush_rewrite_rules();
}
add_action('init', 'jetstream_rewrite_flush');
```

# Make wordpress portable

wp-config

```php
$base_path = substr(ABSPATH, strlen($_SERVER['DOCUMENT_ROOT']));
define('WP_SITEURL', "http://${_SERVER['HTTP_HOST']}${base_path}");
define('WP_HOME',    "http://${_SERVER['HTTP_HOST']}${base_path}");
```

# Include plugin từ theme

http://alexking.org/blog/2012/07/09/include-plugin-in-wordpress-theme

```php
 
// Run this code on 'after_theme_setup', when plugins have already been loaded.
add_action('after_setup_theme', 'my_load_plugin');
 
// This function loads the plugin.
function my_load_plugin() {
 
// Check to see if your plugin has already been loaded. This can be done in several
// ways - here are a few examples:
//
// Check for a class:
// if (!class_exists('MyPluginClass')) {
//
// Check for a function:
// if (!function_exists('my_plugin_function_name')) {
//
// Check for a constant:
// if (!defined('MY_PLUGIN_CONSTANT')) {
 
if (!class_exists('Social')) {
 
// load Social if not already loaded
include_once(TEMPLATEPATH.'plugins/my-plugin/my-plugin.php');
 
}
}
```

# Bắt buộc cài plugin sau khi cài theme

http://tgmpluginactivation.com/

# Disable WordPress Heartbeat API

http://www.inmotionhosting.com/support/website/wordpress/heartbeat-ajax-php-usage
add_action( 'init', 'stop_heartbeat', 1 );

function stop_heartbeat() {
        wp_deregister_script('heartbeat');
}

# Fix option tree textarea issue

add_filter( 'ot_override_forced_textarea_simple', '__return_true' );

# breadcrumbs

```php
function the_breadcrumb() {
    global $post;
    echo '<ul id="breadcrumbs">';
    if (!is_home()) {
        echo '<li><a href="';
        echo get_option('home');
        echo '">';
        echo 'Home';
        echo '</a></li><li class="separator"> / </li>';
        if (is_category() || is_single()) {
            echo '<li>';
            the_category(' </li><li class="separator"> / </li><li> ');
            if (is_single()) {
                echo '</li><li class="separator"> / </li><li>';
                the_title();
                echo '</li>';
            }
        } elseif (is_page()) {
            if($post->post_parent){
                $anc = get_post_ancestors( $post->ID );
                $title = get_the_title();
                foreach ( $anc as $ancestor ) {
                    $output = '<li><a href="'.get_permalink($ancestor).'" title="'.get_the_title($ancestor).'">'.get_the_title($ancestor).'</a></li> <li class="separator">/</li>';
                }
                echo $output;
                echo '<strong title="'.$title.'"> '.$title.'</strong>';
            } else {
                echo '<li><strong> '.get_the_title().'</strong></li>';
            }
        }
    }
    elseif (is_tag()) {single_tag_title();}
    elseif (is_day()) {echo"<li>Archive for "; the_time('F jS, Y'); echo'</li>';}
    elseif (is_month()) {echo"<li>Archive for "; the_time('F, Y'); echo'</li>';}
    elseif (is_year()) {echo"<li>Archive for "; the_time('Y'); echo'</li>';}
    elseif (is_author()) {echo"<li>Author Archive"; echo'</li>';}
    elseif (isset($_GET['paged']) && !empty($_GET['paged'])) {echo "<li>Blog Archives"; echo'</li>';}
    elseif (is_search()) {echo"<li>Search Results"; echo'</li>';}
    echo '</ul>';
}
```

# ACF Repeater template

```php
<?php 
  // check for rows (parent repeater)
  if( have_rows('timeline') ): 
    echo "<ul class='timeline'>";
    $i = 1;
    // loop through rows (parent repeater)
    while( have_rows('timeline') ): the_row(); ?>     
      <li>
        <div class="<?php if ($i%2 == 0) { echo 'direction-r'; } else{ echo 'direction-l';} ?>">
          <div class="flag-wrapper">
            <span class="flag"><?php the_sub_field('history_title'); ?></span>           
          </div>
          <div class="desc"><?php the_sub_field('history_content'); ?></div>
        </div>
      </li>                       
  <?php 
    $i++;
    endwhile; // while( has_sub_field('to-do_lists') ):
    echo "</ul>";
  endif; // if( get_field('to-do_lists') ): 
  ?> 
```

# Remove button from the TinyMCE

```php
add_filter( 'mce_buttons_2', 'acme_remove_from_kitchen_sink');
/**
 * Removes the all but the formatting button from the post editor.
 *
 * @since 1.0.0
 *
 * @param array $buttons The current array buttons including the kitchen sink.
 * @return array The updated array of buttons that exludes the kitchen sink.
 */
function acme_remove_from_kitchen_sink( $buttons ) {
 
$invalid_buttons = array(
'underline',
'justifyfull',
'forecolor',
'|',
'pastetext',
'pasteword',
'removeformat',
'charmap',
'outdent',
'indent',
'undo',
'redo',
'wp_help'
);
 
 
 
foreach ( $buttons as $button_key => $button_value ) {
 
if ( in_array( $button_value, $invalid_buttons ) ) {
unset( $buttons[ $button_key ] );
}
 
}
 
return $buttons;
 
}
```

# Gallery Option tree

```php
if ( function_exists( 'ot_get_option' ) ) {
    // Convert to array 
    $gallery =  explode(',', ot_get_option('partners_gallery'));

    if ( ! empty( $gallery ) ) {
        foreach( $gallery as $id ) {
          if ( ! empty( $id ) ) {
            echo wp_get_attachment_image( $id, 'full' );                
          }
        } /*foreach*/
    } /*! empty( $gallery )*/
} /*function_exists*/
```

# Get all categories woocommerce

```php
woocommerce_product_categories();
or
$args = array(
    'number'     => $number,
    'orderby'    => $orderby,
    'order'      => $order,
    'include'    => $ids
);

$product_categories = get_terms( 'product_cat', $args );
```
<?php wp_list_categories( 'taxonomy=product_cat&pad_counts=1&show_count=1&exclude=25&title_li=' ); ?>

# Get the excert outside the loop

```
function get_excerpt_by_id($post_id){
    $the_post = get_post($post_id); //Gets post ID
    $the_excerpt = $the_post->post_content; //Gets post_content to be used as a basis for the excerpt
    $excerpt_length = 35; //Sets excerpt length by word count
    $the_excerpt = strip_tags(strip_shortcodes($the_excerpt)); //Strips tags and images
    $words = explode(' ', $the_excerpt, $excerpt_length + 1);

    if(count($words) > $excerpt_length) :
        array_pop($words);
        array_push($words, '…');
        $the_excerpt = implode(' ', $words);
    endif;

    $the_excerpt = '<p>' . $the_excerpt . '</p>';

    return $the_excerpt;
}
```

# Woocomerce change city to dropdown field

```php
// Hook in
add_filter( 'woocommerce_checkout_fields' , 'custom_override_checkout_fields' );
function custom_override_checkout_fields( $fields ) {
  $fields['billing']['billing_city'] =  array(
      'label'       => __('Thành phố', 'woocommerce'),      
      'required'    => true,
      'clear'       => true,
      'type'        => 'select',
      'class'       => array('form-row form-row-first billing_anrede_dropdown'),
      'options'     => array(
          '1' => __('Nội thành Hồ Chí Minh', 'woocommerce' ),
          '2' => __('Khu vực khác', 'woocommerce' )
          )
  );

  $fields['shipping']['shipping_city'] =  array(
      'label'       => __('Thành phố', 'woocommerce'),      
      'required'    => true,
      'clear'       => true,
      'type'        => 'select',
      'class'       => array('address-field','update_totals_on_change'),
      'options'     => array(
          '1' => __('Nội thành Hồ Chí Minh', 'woocommerce' ),
          '2' => __('Khu vực khác', 'woocommerce' )
          )
  );
 /* $fields['billing']['billing_address_1']['options'] = array(
    '1' => 'Nội thành Hồ Chí Minh',
    '2' => 'Tỉnh/TP khác'
  ); */  
  return $fields;
}
```

# FILTER NOT GET CURRENT POST

```php
function no_post_id( $query ) {
  global $post;    
  $query['post__not_in'] = array($post->ID);  
  return $query;
   
}
add_filter( 'rpwe_default_query_arguments', 'no_post_id' );
```

# REMOVE SUBMENU NINJA FORM

```php
add_action( 'admin_menu', 'adjust_the_wp_menu', 999 );
function adjust_the_wp_menu() {
  remove_submenu_page( 'index.php', 'nf-about' );
  remove_submenu_page( 'index.php', 'nf-changelog' );
  remove_submenu_page( 'index.php', 'nf-getting-started' );
  remove_submenu_page( 'index.php', 'nf-credits' );
}
```

# REMOVE NINJA FORM METABOX

```php
remove_action('add_meta_boxes','ninja_forms_add_custom_box');
remove_action('save_post','ninja_forms_save_postdata');
```

# FORMAT DATE FROM STRING

```php
$date = $file->file_date; $d = DateTime::createFromFormat("Y-m-d H:i:s", $date); echo $d->format("F j, Y");
```

# Create Front-End login


https://wordpress.org/plugins/sidebar-login/screenshots/
<?php
/**
 * Template Name: Login
 *
 */
?>
 
<?php get_header(); ?>
<!-- section -->
<section class="aa_loginForm">
 
<?php global $user_login;
if(isset($_GET['login']) && $_GET['login'] == 'failed')
{
?>
<div class="aa_error">
<p>FAILED: Try again!</p>
</div>
<?php
}
if (is_user_logged_in()) {
echo '<div class="aa_logout"> Hello, <div class="aa_logout_user">', $user_login, '. You are already logged in.</div><a id="wp-submit" href="', wp_logout_url(), '" title="Logout">Logout</a></div>';
} else {
wp_login_form($args);
$args = array(
'echo' => true,
'redirect' => home_url('/wp-admin/'),
'form_id' => 'loginform',
'label_username' => __( 'Username' ),
'label_password' => __( 'Password' ),
'label_remember' => __( 'Remember Me' ),
'label_log_in' => __( 'Log In' ),
'id_username' => 'user_login',
'id_password' => 'user_pass',
'id_remember' => 'rememberme',
'id_submit' => 'wp-submit',
'remember' => true,
'value_username' => NULL,
'value_remember' => true
);
}
?>
 
</section>
<!-- /section -->
 
<?php get_footer(); ?> 

# Posting in front-end

http://code.tutsplus.com/tutorials/posting-via-the-front-end-inserting--wp-27034

# GET FRONT PAGE ID

```php
$frontpage_ID = get_option('page_on_front');
```

# CUSTOM SUB-MENU CLASS

```php
class UL_Class_Walker extends Walker_Nav_Menu {

  function start_lvl(&$output, $depth = 0, $args = array()) {
    $indent = str_repeat("\t", $depth);
    $output .= "\n$indent<ul class=\"submenu dropdown-menu level-".$depth."\">\n";
  }
}

 $args = array(
    'theme_location' => 'primary-menu',
    'container'      => false,
    'menu'           => 'primary-menu',                
    'menu_class'     => 'ul-primary-nav',
    'depth'          => 5,
    'walker' => new UL_Class_Walker()
  );
  wp_nav_menu( $args );
```

# Display user name on menu

```php
add_filter('wp_nav_menu', 'do_menu_shortcodes'); 
function do_menu_shortcodes( $menu ){ 
        return do_shortcode( $menu ); 
} 

add_shortcode( 'current-username' , 'username_on_menu' );
function username_on_menu(){
    $user = wp_get_current_user();
    return $user->display_name;
}
```

# Limit search

```php
function searchfilter($query) {
    if ($query->is_search ) {
        $query->set('post_type',array('page'));
    }
    return $query;
}

add_filter('pre_get_posts','searchfilter');
```

# Enqueue JQUERY

```php
wp_deregister_script('jquery');
      wp_register_script('jquery', "http" . ($_SERVER['SERVER_PORT'] == 443 ? "s" : "") . "://code.jquery.com/jquery-1.11.2.min.js", false, null);
      wp_enqueue_script('jquery');
```

# Add to cart url

```php
<?php echo $checkout_url ?>?add-to-cart=<?php echo $best_seller->ID?>
```


# GET BEST SELLER PRODUCT

```php
$args = array(   
    'post_type'              => 'product',
    'post_status'            => 'publish',
    'order'                  => 'DESC',
    'orderby'                => 'meta_value_num',
    'meta_key'               => 'total_sales',
    'posts_per_page'         => $number_of_products_per_page,
    'posts_per_archive_page' => $number_of_products_per_page,
    'paged'                  => get_query_var('paged'),                    
    'tax_query' => array(
        'relation'  => 'AND',
        array(
          'taxonomy'         => 'product_type',
          'field'            => 'slug',
          'terms'            => array( 'simple' ),
          'include_children' => true,
          'operator'         => 'IN'
        ),          
    )
  
);

$query = new WP_Query( $args );
```

# LOGOUT MENU

```php
add_filter( 'wp_nav_menu_items', 'wti_loginout_menu_link', 10, 2 );

function wti_loginout_menu_link( $items, $args ) {
   if ($args->theme_location == 'primary') {
      if (is_user_logged_in()) {
         $items .= '<li class="right"><a href="'. wp_logout_url() .'">Log Out</a></li>';
      } else {
         $items .= '<li class="right"><a href="'. wp_login_url(get_permalink()) .'">Log In</a></li>';
      }
   }
   return $items;
}
```

# Get products by categories

```php
$args = array(
    'number'     => $number,
    'orderby'    => 'title',
    'order'      => 'ASC',
    'hide_empty' => $hide_empty,
    'include'    => $ids
);
$product_categories = get_terms( 'product_cat', $args );
$count = count($product_categories);
if ( $count > 0 ){
    foreach ( $product_categories as $product_category ) {
        echo '<h4><a href="' . get_term_link( $product_category ) . '">' . $product_category->name . '</a></h4>';
        $args = array(
            'posts_per_page' => -1,
            'tax_query' => array(
                'relation' => 'AND',
                array(
                    'taxonomy' => 'product_cat',
                    'field' => 'slug',
                    // 'terms' => 'white-wines'
                    'terms' => $product_category->slug
                )
            ),
            'post_type' => 'product',
            'orderby' => 'title,'
        );
        $products = new WP_Query( $args );
        echo "<ul>";
        while ( $products->have_posts() ) {
            $products->the_post();
            ?>
                <li>
                    <a href="<?php the_permalink(); ?>">
                        <?php the_title(); ?>
                    </a>
                </li>
            <?php
        }
        echo "</ul>";
    }
}
```

# Remove un use class body class

```php
add_filter( 'body_class', 'my_class_names', 10, 2  );
function my_class_names( $classes ) {
    foreach($classes as $key => $value) {
        if ($value == 'woocommerce') unset($classes[$key]);
        if ($value == 'woocommerce-page') unset($classes[$key]);
        if ($value == 'page') unset($classes[$key]);
        if ($value == 'single-author') unset($classes[$key]);
    }
    return $classes;
}
```