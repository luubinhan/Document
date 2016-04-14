>> https://www.smashingmagazine.com/2016/04/three-approaches-to-adding-configurable-fields-to-your-plugin/

# 1 Using The Built-In WordPress Functionality

``` php
public function plugin_settings_page_content() { ?>
    <div class="wrap">
        <h2>My Awesome Settings Page</h2>
        <form method="post" action="options.php">
            <?php
                settings_fields( 'smashing_fields' );
                do_settings_sections( 'smashing_fields' );
                submit_button();
            ?>
        </form>
    </div> <?php
}
```

Sections And Fields

```php
add_action( 'admin_init', array( $this, 'setup_sections' ) );

public function setup_sections() {
    add_settings_section( 'our_first_section', 'My First Section Title', array( $this, 'section_callback' ), 'smashing_fields' );
    add_settings_section( 'our_second_section', 'My Second Section Title', array( $this, 'section_callback' ), 'smashing_fields' );
    add_settings_section( 'our_third_section', 'My Third Section Title', array( $this, 'section_callback' ), 'smashing_fields' );
}

public function section_callback( $arguments ) {
    switch( $arguments['id'] ){
        case 'our_first_section':
            echo 'This is the first description here!';
            break;
        case 'our_second_section':
            echo 'This one is number two';
            break;
        case 'our_third_section':
            echo 'Third time is the charm!';
            break;
    }
}

add_action( 'admin_init', array( $this, 'setup_fields' ) );
public function setup_fields() {
    $fields = array(
        array(
            'uid' => 'our_first_field',
            'label' => 'Awesome Date',
            'section' => 'our_first_section',
            'type' => 'text',
            'options' => false,
            'placeholder' => 'DD/MM/YYYY',
            'helper' => 'Does this help?',
            'supplemental' => 'I am underneath!',
            'default' => '01/01/2015'
        )
    );
    foreach( $fields as $field ){
        add_settings_field( $field['uid'], $field['label'], array( $this, 'field_callback' ), 'smashing_fields', $field['section'], $field );
        register_setting( 'smashing_fields', $field['uid'] );
    }
}
public function field_callback( $arguments ) {
    $value = get_option( $arguments['uid'] ); // Get the current value, if there is one
    if( ! $value ) { // If no value exists
        $value = $arguments['default']; // Set to our default
    }

    // Check which type of field we want
    switch( $arguments['type'] ){
        case 'text': // If it is a text field
            printf( '<input name="%1$s" id="%1$s" type="%2$s" placeholder="%3$s" value="%4$s" />', $arguments['uid'], $arguments['type'], $arguments['placeholder'], $value );
            break;
        case 'textarea': // If it is a textarea
            printf( '<textarea name="%1$s" id="%1$s" placeholder="%2$s" rows="5" cols="50">%3$s</textarea>', $arguments['uid'], $arguments['placeholder'], $value );
            break;
        case 'select': // If it is a select dropdown
            if( ! empty ( $arguments['options'] ) && is_array( $arguments['options'] ) ){
                $options_markup = '';
                foreach( $arguments['options'] as $key => $label ){
                    $options_markup .= sprintf( '<option value="%s" %s>%s</option>', $key, selected( $value, $key, false ), $label );
                }
                printf( '<select name="%1$s" id="%1$s">%2$s</select>', $arguments['uid'], $options_markup );
            }
            break;
    }

    // If there is help text
    if( $helper = $arguments['helper'] ){
        printf( '<span class="helper"> %s</span>', $helper ); // Show it
    }

    // If there is supplemental text
    if( $supplimental = $arguments['supplemental'] ){
        printf( '<p class="description">%s</p>', $supplimental ); // Show it
    }
}
```

# 2 Integrating ACF (Advanced Custom Fields) Into Your Plugin

In your plugin directory create a vendor directory and add ACF to it

## Include ACF In Your Plugin

First we have to include the main ACF file with PHP. Add the following code to the bottom of our constructor function:

```php
include_once( plugin_dir_path( __FILE__ ) . 'vendor/advanced-custom-fields/acf.php' );
```

We need to tell ACF to look for its front-end assets and file includes in our plugin directory instead of its normal place. Add these two hooks to your constructor:

```php
add_filter( 'acf/settings/path', array( $this, 'update_acf_settings_path' ) );
add_filter( 'acf/settings/dir', array( $this, 'update_acf_settings_dir' ) );
public function update_acf_settings_path( $path ) {
    $path = plugin_dir_path( __FILE__ ) . 'vendor/advanced-custom-fields/';
    return $path;
}

public function update_acf_settings_dir( $dir ) {
    $dir = plugin_dir_url( __FILE__ ) . 'vendor/advanced-custom-fields/';
    return $dir;
}
```

To add the options, we need to add a method call to our constructor. Add this line to the end of your constructor after our ACF include:

```php
$this->setup_options();

public function setup_options() {
    if( function_exists( 'register_field_group' ) ) {
        register_field_group(array (
            'id' => 'acf_awesome-options',
            'title' => 'Awesome Options',
            'fields' => array (
                array (
                    'key' => 'field_562dc35316a0f',
                    'label' => 'Awesome Name',
                    'name' => 'awesome_name',
                    'type' => 'text',
                    'default_value' => '',
                    'placeholder' => '',
                    'prepend' => '',
                    'append' => '',
                    'formatting' => 'html',
                    'maxlength' => '',
                ),
                array (
                    'key' => 'field_562dc9affedd6',
                    'label' => 'Awesome Date',
                    'name' => 'awesome_date',
                    'type' => 'date_picker',
                    'date_format' => 'yymmdd',
                    'display_format' => 'dd/mm/yy',
                    'first_day' => 1,
                ),
                array (
                    'key' => 'field_562dc9bffedd7',
                    'label' => 'Awesome WYSIWYG',
                    'name' => 'awesome_wysiwyg',
                    'type' => 'wysiwyg',
                    'default_value' => '',
                    'toolbar' => 'full',
                    'media_upload' => 'yes',
                ),
            ),
            'location' => array (
                array (
                    array (
                        'param' => 'options_page',
                        'operator' => '==',
                        'value' => 'smashing_fields',
                    ),
                ),
            ),
            'menu_order' => 0,
            'position' => 'normal',
            'style' => 'default',
            'label_placement' => 'top',
            'instruction_placement' => 'label',
            'hide_on_screen' => '',
            'active' => 1,
            'description' => '',
        ));
    }
}
```


To add the fields we just created to the page we will need to update our plugin_settings_page_content method.


```php
public function plugin_settings_page_content() {
    do_action('acf/input/admin_head'); // Add ACF admin head hooks
    do_action('acf/input/admin_enqueue_scripts'); // Add ACF scripts

    $options = array(
        'id' => 'acf-form',
        'post_id' => 'options',
        'new_post' => false,
        'field_groups' => array( 'acf_awesome-options' ),
        'return' => admin_url('admin.php?page=smashing_fields'),
        'submit_value' => 'Update',
    );
    acf_form( $options );
}
```

we need to add another hook to our constructor:

```
add_action( 'admin_init', array( $this, 'add_acf_variables' ) );

// you need to hide the Custom Fields menu item
add_filter( 'acf/settings/show_admin', '__return_false' );

public function add_acf_variables() {
    acf_form_head();
}
```

get_field( 'awesome_date', 'option' )