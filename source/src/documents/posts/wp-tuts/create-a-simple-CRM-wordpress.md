---
layout: 'content'
title: 'Create a simple CRM Wordpress'
---

http://code.tutsplus.com/tutorials/create-a-simple-crm-in-wordpress-advanced-custom-fields--cms-20049

1. Download plugin ACF
2. Tạo field
3. Export option ra PHP file, dán vào thư mục nào cũng được
4. Copy thư mục ACF vào trong theme/plugin
5. Active từ theme/plugin : include_once( 'advanced-custom-fields/acf.php' );
6. Set: add_action( 'plugins_loaded', array( $this, 'acf_fields' ) );
3. Ẩn menu ACF: define( 'ACF_LITE', true );