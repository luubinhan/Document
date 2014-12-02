---
layout: 'content'
title: 'Settings and Controls for a Color Scheme in the Theme Customizer'
---

Source: http://code.tutsplus.com/tutorials/settings-and-controls-for-a-color-scheme-in-the-theme-customizer--cms-21350

Include <code>customizer.php</code> trong file <code>functions.php</code>

```php
include_once( 'inc/customizer.php' );
```

File <code>customizer.php</code>

```php
function wptutsplus_customize_register( $wp_customize ) {
 
}
add_action( 'customize_register', 'wptutsplus_customize_register' );

function wptutsplus_customize_colors() {
    /**********************
    text colors
    **********************/
    // main color
    $color_scheme_1 = get_option( 'color_scheme_1' );
     
    // secondary color
    $color_scheme_2 = get_option( 'color_scheme_2' );
     
    // link color
    $link_color = get_option( 'link_color' );
     
    // hover or active link color
    $hover_link_color = get_option( 'hover_link_color' );
    ?>
    <style> 
 
    /* color scheme */
     
    /* main color */
    #site-title a, h1, h2, h2.page-title, h2.post-title, h2 a:link, h2 a:visited, .menu.main a:link, .menu.main a:visited, footer h3 {
        color:  <?php echo $color_scheme_1; ?>;
    }
     
    /* secondary color */
    #site-description, .sidebar h3, h3, h5, .menu.main a:active, .menu.main a:hover {
        color:  <?php echo $color_scheme_2; ?>;
    }
    .menu.main,
    .fatfooter {
        border-top: 1px solid <?php echo $color_scheme_2; ?>;
    }
    .menu.main {
        border-bottom: 1px solid <?php echo $color_scheme_2; ?>; 
    }
    .fatfooter {
        border-bottom: 1px solid <?php echo $color_scheme_2; ?>;
    }
     
    /* links color */
    a:link, a:visited {
        color:  <?php echo $link_color; ?>;
    }
     
    /* hover links color */
    a:hover, a:active {
        color:  <?php echo $hover_link_color; ?>;
    }
     
    </style>
    <?php
}
add_action( 'wp_head', 'wptutsplus_customize_colors' );
```

Tạo Settings và Controls trong hàm <code>wptutsplus_customize_register</code>

```php
/*******************************************
Color scheme
********************************************/
 
// add the section to contain the settings
$wp_customize->add_section( 'textcolors' , array(
    'title' =>  'Color Scheme',
) );

// main color ( site title, h1, h2, h4. h6, widget headings, nav links, footer headings )
$txtcolors[] = array(
    'slug'=>'color_scheme_1',
    'default' => '#000',
    'label' => 'Main Color'
);
 
// secondary color ( site description, sidebar headings, h3, h5, nav links on hover )
$txtcolors[] = array(
    'slug'=>'color_scheme_2',
    'default' => '#666',
    'label' => 'Secondary Color'
);
 
// link color
$txtcolors[] = array(
    'slug'=>'link_color',
    'default' => '#008AB7',
    'label' => 'Link Color'
);
 
// link color ( hover, active )
$txtcolors[] = array(
    'slug'=>'hover_link_color',
    'default' => '#9e4059',
    'label' => 'Link Color (on hover)'
);


// add the settings and controls for each color
foreach( $txtcolors as $txtcolor ) {
 
    // SETTINGS
    $wp_customize->add_setting(
        $txtcolor['slug'], array(
            'default' => $txtcolor['default'],
            'type' => 'option',
            'capability' =>
            'edit_theme_options'
        )
    );
    // CONTROLS
    $wp_customize->add_control(
        new WP_Customize_Color_Control(
            $wp_customize,
            $txtcolor['slug'],
            array('label' => $txtcolor['label'],
            'section' => 'textcolors',
            'settings' => $txtcolor['slug'])
        )
    );
}
```