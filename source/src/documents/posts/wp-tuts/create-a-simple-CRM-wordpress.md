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
6.1 Set: add_action( 'plugins_loaded', array( $this, 'acf_fields' ) ); 
6.2 Cách khác so với 6.1 dùng để đưa vào theme mode
    6.2.1 Tạo file php với hàm function acf_fields() chứa nguyên file đã export
    6.2.2 require( trailingslashit( get_template_directory() ) . [đường dẫn tới file acf_fields] ); trong file functions.php
    6.2.3 Phía trên đầu file acf-fields, thêm add_action( 'after_setup_theme', 'acf_fields' );   

3. Ẩn menu ACF: define( 'ACF_LITE', true );