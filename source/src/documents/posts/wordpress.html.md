---
layout: 'content'
title: 'Wordpress'
description: Wordpress Snip Code
---

#### Table of content
-------------

Wordpress Snip Code
----------------------

<!-- MarkdownTOC depth=2 -->

- Get post feature image
- Get option from admin
- Thêm VND vào WOO
- animate css
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

<!-- /MarkdownTOC -->


# Get post feature image

```php
    $url = wp_get_attachment_url( get_post_thumbnail_id($post->ID, 'thumbnail') );
    <img src="<?php echo $url ?>" title="<?php the_title(); ?>" alt="<?php the_title(); ?>" />
```

# Get option from admin

<?php 
$settings = array(
            'thumb_w' => 787, 
            'thumb_h' => 300, 
            'thumb_align' => 'alignleft'
            );
            
$settings = woo_get_dynamic_values( $settings );
 ?>

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
# animate css

http://www.w3.org/TR/css3-transitions/#properties-from-css-

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

Plugin Folder/admin/woocommerce-admin-init.php

# Get template part woocommerce

woocommerce_get_template_part()

# Get product price 

<?php woocommerce_get_template( 'loop/price.php' ); ?>

# Convert to lower case

strtolower();

# Get Product Category

<?php echo $product->get_categories(); ?>

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
<?php $i = 0; ?>

Đừng sử dụng get_template_part(), sử dụng, locate_template()

<?php include(locate_template('content-video.php')); ?>

Trên trang con có thể sử dụng biến $i trên trang cha

<?php if( ($i % 5) == 0 ): ?>
    <div id="post-<?php the_ID(); ?>" <?php post_class('post-video alpha');?> >
<?php else: ?>
    <div id="post-<?php the_ID(); ?>" <?php post_class('post-video');?> >
<?php endif; ?>

# Get Various WooCommerce Page URLs

<?php $shop_page_url = get_permalink( woocommerce_get_page_id( 'shop' ) ); ?>

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

// Add support for Featured Images
if (function_exists('add_theme_support')) {
    add_theme_support('post-thumbnails');
    add_image_size('index-categories', 694, 150, true);
}

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

$post_id = $GLOBALS['post']->ID;

# Remove column 

## Wordpress SEO
add_filter( 'wpseo_use_page_analysis', '__return_false' );




